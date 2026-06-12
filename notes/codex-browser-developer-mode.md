# Codex 浏览器开发者模式：把网页调试变成可验证的 Agent 任务

## 审计信息

- 整理时间：2026-06-12。
- 来源：AIHot 近期 Agent 条目发现，事实部分以 OpenAI Codex 官方文档为准。
- 作者：本地整理；公开版由 Codex 脱敏改写。
- 适合读者：已经开始让 Codex 调试网页、预览前端、检查页面问题，但还分不清 Browser、Chrome 扩展和 Developer mode 的新手。
- 目标：把“让 Agent 操作浏览器”拆成安全、可验收、可复查的网页调试流程。
- 隐私处理：不包含账号、浏览器历史、本地路径、客户页面、后台截图、cookie、密钥或未脱敏调试日志。

## 先说结论

Codex 的浏览器能力不是一个单独的 skill，也不是“让 Agent 随便操作网页”的许可。它更像三层工具：

1. **In-app browser**：适合本地开发服务器、文件预览和不需要登录的公开页面。
2. **Codex Chrome extension**：适合确实需要你当前 Chrome 登录态的网站，例如内部工具或已经登录的业务系统。
3. **Developer mode / CDP**：适合调试问题本身，例如性能、console、network、DOM、样式和页面状态。

新手最稳的顺序是：

```text
本地或公开页面 -> 先用 in-app browser
需要真实登录态 -> 再考虑 Chrome extension
需要看 console/network/performance/DOM/styles -> 再开 Developer mode
涉及发布、付款、删除、提交、账号设置 -> 必须人工确认
```

这篇笔记的核心不是教你“怎么让 Agent 点网页”，而是教你什么时候该让 Agent 看页面、看哪些证据、怎么避免把敏感浏览器状态带进任务。

## 三个能力不要混在一起

| 能力 | 解决什么问题 | 适合场景 | 不适合场景 | 风险点 |
|---|---|---|---|---|
| In-app browser | 在 Codex 线程里共同查看渲染后的网页 | `localhost`、文件预览、公开页面、视觉标注、低风险点击验证 | 登录态页面、需要浏览器插件或真实 Chrome profile 的页面 | 页面内容仍然是不可信上下文，不要粘贴秘密 |
| Chrome extension | 让 Codex 使用你真实 Chrome 的登录状态 | 已登录的内部系统、Gmail、Salesforce、LinkedIn 等需要当前浏览器状态的页面 | 本地开发预览、公开网页、普通视觉调试 | Chrome profile、历史记录、网页内容可能很敏感 |
| Developer mode / CDP | 让 Codex 通过 Chrome DevTools Protocol 做深度调试 | console、network、performance trace、DOM、computed styles、页面状态诊断 | 普通资料阅读、无需调试证据的页面浏览、绕过限制 | CDP 能看到更深的浏览器内部状态，授权前必须确认站点和任务 |

一句话：**Browser 是看页面，Chrome extension 是带登录态看页面，Developer mode 是带调试仪表盘看页面。**

## 什么时候值得用 Developer mode

只有当问题需要“浏览器内部证据”时，Developer mode 才值得打开。

| 现象 | 为什么 Developer mode 有价值 | 你应该让 Agent 看什么 |
|---|---|---|
| 页面白屏 | 截图只能证明白屏，不能说明原因 | console error、failed network request、bundle 加载情况 |
| 点击后没反应 | 需要判断是事件没绑定、请求失败，还是状态没更新 | DOM state、event 后的 network、按钮 disabled 状态 |
| 页面很慢 | 需要定位是 JS、接口、图片、字体还是渲染阻塞 | performance trace、network waterfall、long task |
| 样式错位 | 需要看真实应用到元素上的样式 | DOM、computed styles、布局尺寸 |
| 本地修复后要验收 | 需要证明改动真的影响了页面 | 修复前后截图、console 是否干净、关键请求是否成功 |

不值得用的情况：

1. 只是读一篇公开网页。
2. 只是把网页内容整理成笔记。
3. 只是填写一个可人工完成的表单。
4. 任务目标不清楚，只是说“帮我看看这个站”。
5. 需要绕过验证码、付费墙、反爬、风控或访问控制。

## 新手推荐工作流

### 1. 先定义页面和状态

不要只说“帮我调一下页面”。应该给出：

```text
页面：
期望状态：
当前问题：
可改范围：
不能做什么：
验收方式：
```

例子：

```text
页面：http://localhost:3000/settings
期望状态：移动端宽度下，保存按钮不溢出，错误提示显示在输入框下方。
当前问题：375px 宽度时按钮文字被截断。
可改范围：settings 页面和共用表单样式。
不能做：不要改接口、路由、登录逻辑。
验收方式：桌面和移动端截图各 1 张；console 没有新错误。
```

### 2. 本地页面先用 in-app browser

如果页面是本地开发服务器或公开页面，先让 Codex 在 in-app browser 里打开。这样不会使用你的 Chrome profile，也不会读取真实登录状态。

适合的任务：

1. 预览本地页面。
2. 点击按钮复现布局问题。
3. 留视觉标注。
4. 做修复前后截图。
5. 用只读页面检查 JS 查看渲染状态。

### 3. 需要登录态时再用 Chrome extension

只有当任务必须依赖你当前 Chrome 的登录状态时，再考虑 Chrome extension。

使用前先写清：

| 检查项 | 需要确认 |
|---|---|
| 站点 | 只允许本次任务需要的网站 |
| 动作 | 只读、草稿、可撤销，还是不可撤销 |
| 数据 | 是否会出现客户、订单、邮箱、聊天、联系人、财务、密钥 |
| 输出 | 是否会把截图、日志、页面内容写进公开仓库 |
| 人工确认 | 哪些动作必须停下来等你确认 |

公开分享内容时，不要上传 Chrome 登录态页面截图、后台数据、浏览器历史、客户字段或完整调试日志。

### 4. 需要证据时再开 Developer mode

Developer mode 适合“页面为什么坏了”的问题。授权前先让 Agent 说清它准备看什么：

```text
请使用 Browser Developer mode 调试这个本地页面。

目标：
找出页面白屏原因。

允许查看：
- console errors
- network failed requests
- DOM 中根节点渲染状态
- 必要的 performance 信息

不允许：
- 读取登录态站点
- 读取浏览器历史
- 导出完整页面数据
- 访问无关网站

请输出：
1. 观察到的证据。
2. 最可能原因。
3. 建议修改文件。
4. 修改后如何复验。
```

这比“开 CDP 看看”安全得多，因为任务、站点、证据范围和输出边界都写清楚了。

### 5. 修复后必须复验

Agent 改完代码后，不要只看它的总结。至少要留下：

1. 修复前问题描述。
2. 改了哪些文件。
3. 重新打开的页面 URL。
4. console / network / screenshot / DOM 中至少一种证据。
5. 还没验证的地方。

如果是 UI 问题，截图很重要。如果是接口问题，network 和状态断言更重要。如果是性能问题，trace 或关键耗时对比更重要。

## 可复制提示词

### 本地前端调试

```text
请用 Browser 打开这个本地页面并调试问题。

页面：
{URL}

问题：
{描述可见问题}

要求：
1. 先复现问题，不要直接改代码。
2. 记录你观察到的证据：截图、console、network 或 DOM 状态。
3. 只修改和问题直接相关的文件。
4. 修改后重新打开页面复验。
5. 输出已验证项和未验证项。

边界：
- 不访问登录态页面。
- 不读取密钥、cookie、浏览器历史或私有数据。
- 不做发布、付款、删除、提交等不可逆动作。
```

### Chrome 登录态页面只读审查

```text
请使用 Chrome extension 只读查看下面这个已登录页面。

网站：
{网站}

任务：
{只读目标}

允许：
- 阅读当前页面可见内容。
- 总结页面结构和我需要手动检查的位置。

不允许：
- 点击提交、发送、删除、付款、邀请、授权、保存。
- 读取浏览器历史、cookie、密钥或无关标签页。
- 把客户、联系人、邮箱、订单、聊天记录写入公开文件。

遇到任何写入、发布或不可逆动作，请停止并询问我。
```

### Developer mode 性能诊断

```text
请用 Developer mode 诊断这个页面为什么变慢。

页面：
{URL}

关注点：
- 首屏是否有慢请求。
- 是否有明显 JS long task。
- 图片、字体或接口是否阻塞渲染。
- 是否有 console error。

输出：
1. 关键证据。
2. 最可能瓶颈。
3. 建议修改方向。
4. 需要我确认的风险。
5. 复验方法。

不要读取无关站点、浏览器历史、cookie、密钥或登录态隐私。
```

## 和自动化浏览技术路线的关系

[Agent 自动化浏览与软件操作技术路线](agent-automation-browser.md) 讲的是更通用的技术分层：API、DOM、CDP、Playwright、UIA、RPA、视觉坐标和 Computer Use。

这篇补充的是 Codex 新手最常遇到的产品层判断：

1. 本地网页调试优先 in-app browser。
2. 真实登录态才考虑 Chrome extension。
3. 需要浏览器内部证据才考虑 Developer mode。
4. CDP 不是越早开越好，它是高权限调试工具。
5. 任何账号、发布、付款、删除、提交动作都要人工确认。

## 发布到公开仓库前的脱敏清单

如果你把浏览器调试过程整理成笔记，发布前检查：

- 没有登录态页面截图。
- 没有客户、订单、联系人、邮件、聊天记录。
- 没有 cookie、token、Authorization header、`.env`、密钥。
- 没有本机绝对路径、内部域名、私有仓库地址。
- 没有完整 network payload，只保留脱敏后的错误类型和排查方法。
- 没有把页面里的不可信提示当成系统指令。
- 有来源链接、复现条件和已验证项。

## 来源

- [OpenAI Codex: In-app browser](https://developers.openai.com/codex/app/browser)
- [OpenAI Codex: Chrome extension](https://developers.openai.com/codex/app/chrome-extension)
- [Chrome DevTools Protocol](https://chromedevtools.github.io/devtools-protocol/)
- [AIHot](https://aihot.virxact.com)
