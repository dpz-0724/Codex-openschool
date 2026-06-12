# 第一个 Agent 实战任务：整理一篇公开网页并写成 Markdown 笔记

## 审计信息

- 来源：本地 Codex / skills / 自动化浏览 / 知识库维护经验；结合 OpenAI、Anthropic 的公开一手资料整理。
- 作者：本地整理；公开版由 Codex 脱敏改写。
- 适合读者：已经读过 Agent 概念，但还没有让 Agent 做过完整任务的新手。
- 目标：用 30 分钟完成一个低风险闭环：选公开资料 -> 让 Agent 阅读 -> 生成结构化笔记 -> 自检 -> 存入知识库。
- 隐私处理：不包含本地路径、账号、聊天记录、后台数据、私有 skill 源码、密钥或未发布项目。

## 为什么第一个任务选“整理公开网页”

第一个 Agent 任务不要从“全自动操作账号”“批量抓取数据”“修改真实项目”开始。那些任务风险高，失败原因也复杂，新手很难判断问题出在哪里。

整理公开网页更适合入门：

- 资料来源可验证。
- 不需要账号和隐私数据。
- 输出是 Markdown，容易检查。
- 能练到 Agent 的关键能力：读资料、抓重点、标不确定、给来源、写成可复用笔记。
- 失败也容易修正，不会影响外部系统。

OpenAI 的 Agent 学习资料强调 agent 需要 instructions、guardrails 和 tools，并能代表用户采取行动。Anthropic 也建议先使用简单、可组合的模式，不要一开始就追复杂框架。这个练习就是把这些原则压缩成一个小闭环。

## 任务目标

让 Agent 阅读一篇公开网页，并输出一篇可以放进个人知识库的 Markdown 笔记。

最终产物应该包含：

1. 资料标题和链接。
2. 这篇资料解决的问题。
3. 3-5 条核心观点。
4. 适合新手的解释。
5. 可以立即实践的一步。
6. 不确定或需要继续查证的地方。
7. 来源链接。
8. 一段自检结论。

## 推荐练习资料

任选一个公开网页即可。第一轮建议选官方资料，减少二手转述误差：

| 资料 | 适合练什么 |
|---|---|
| [OpenAI Building agents](https://developers.openai.com/tracks/building-agents) | 理解 agent、tools、guardrails、orchestration |
| [Anthropic Building effective agents](https://www.anthropic.com/engineering/building-effective-agents) | 理解 workflow 和 agent 的区别 |
| [Anthropic Effective context engineering](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) | 理解为什么上下文不是越多越好 |
| [Model Context Protocol 官方介绍](https://modelcontextprotocol.io/docs/getting-started/intro) | 理解 MCP 的定位和使用边界 |

新手第一篇建议选 Anthropic 的 `Building effective agents`，因为它非常适合练“workflow 和 agent 的区别”。

## 安全边界

这个任务只允许处理公开资料。

不要让 Agent：

- 登录你的账号。
- 抓取付费墙内容。
- 绕过验证码或反爬。
- 复制长篇原文。
- 处理聊天记录、客户资料、后台截图或私有文档。
- 自动发布内容到外部平台。
- 把没有来源的判断写成事实。

如果页面需要登录、付费、验证或授权，换一个公开页面。

## 第一步：给 Agent 任务说明

把下面这段复制给 Agent，替换里面的 `资料链接`。

```text
你是一个 AI Agent 入门学习助手。

任务：阅读下面这篇公开资料，把它整理成一篇适合新手保存到 Markdown 知识库的学习笔记。

资料链接：
[粘贴资料链接]

要求：
1. 只基于资料正文和可访问页面内容整理，不要编造。
2. 不要复制长篇原文，只做中文转述和结构化摘要。
3. 每个关键判断都尽量关联到来源链接。
4. 标出你不确定、需要继续查证、或资料没有覆盖的地方。
5. 输出 Markdown。
6. 最后做一次自检：是否有来源、是否过度概括、是否适合新手、是否有隐私或版权风险。

输出结构：
- 标题
- 适合谁
- 这篇资料解决什么问题
- 3-5 条核心观点
- 新手解释
- 可以立刻实践的一步
- 不确定 / 待查证
- 来源
- 自检结论
```

## 第二步：让 Agent 先确认边界

在它开始写之前，最好让它先回答：

```text
在正式整理前，请先判断：

1. 这个页面是否公开可访问？
2. 是否需要登录、付费或绕过限制？
3. 是否适合做学习摘要？
4. 你会避免哪些版权或隐私风险？

确认后再继续整理。
```

这一步能防止 Agent 一上来就抓错页面、搬运原文或忽略授权边界。

## 第三步：拿到初稿后做审计

初稿出来后，不要直接保存。继续让 Agent 自检：

```text
请审计你刚才的笔记：

1. 哪些内容来自资料，哪些是你的解释？
2. 有没有没有来源支撑的判断？
3. 有没有过度复制原文？
4. 有没有对新手不友好的术语？
5. 这篇笔记是否能指导我做一个具体动作？

请给出修订版。
```

## 第四步：保存为知识库笔记

合格笔记可以保存成这样的文件结构：

```markdown
# [资料主题] 学习笔记

## 来源

- 标题：
- 链接：
- 阅读日期：
- 整理者：

## 适合谁

## 这篇资料解决什么问题

## 核心观点

## 新手解释

## 可以立刻实践的一步

## 不确定 / 待查证

## 我的行动

## 标签
```

## 示例：整理 Anthropic 的 Agent 文章

假设你选择的是 `Building effective agents`，合格输出不应该是“这篇文章讲了 AI Agent 很重要”这种空话。

更好的输出应该能回答：

- workflow 和 agent 的区别是什么？
- 为什么不是所有任务都需要 agent？
- 什么时候应该保持简单？
- 为什么工具、检索、记忆这些能力要有清晰接口？
- 新手下一步应该做什么小实验？

一个合格的“可以立刻实践的一步”可能是：

> 选一个固定任务，例如“先提纲、再检查、再写正文”，把它拆成 workflow；只有当输入变化很大、需要模型动态选择下一步时，再考虑做成 agent。

## 验收清单

发布或保存前，用这张表检查：

| 检查项 | 通过标准 |
|---|---|
| 来源 | 有原始链接，不只写“网上看到” |
| 版权 | 没有长篇复制原文 |
| 隐私 | 没有账号、聊天、后台、客户或本地路径 |
| 结构 | 有问题、观点、解释、行动、待查证 |
| 新手友好 | 术语有解释，不默认读者懂框架 |
| 可执行 | 读完知道下一步能做什么 |
| 可复用 | 可以保存到知识库，以后还能查 |
| 自检 | Agent 说明了不确定和边界 |

## 常见失败样子

如果输出出现下面情况，说明任务还没做好：

- 只有摘要，没有行动建议。
- 只有观点堆叠，没有说明适合谁。
- 把原文大段翻译过来。
- 没有来源链接。
- 把官方文章没有说的内容写成事实。
- 不区分“资料观点”和“自己的解释”。
- 没有任何不确定项，像是全知全能。

## 进阶：把它变成可复用 workflow

当你已经做过 3 次网页整理，可以把流程固化：

1. 输入 URL。
2. 检查页面是否公开可访问。
3. 提取标题、正文、发布时间、作者。
4. 生成 Markdown 初稿。
5. 自检来源、版权、隐私、术语。
6. 写入知识库。
7. 更新索引。

这时它就从一次 Agent 任务，变成了一个可复用 workflow。后续如果你经常处理网页资料，可以再考虑写成 skill。

## 一句话收尾

第一个 Agent 任务不要追求“全自动”。先完成一个可验证的小闭环：公开资料、明确目标、结构化输出、来源审计、保存复用。这个闭环跑通，比装一堆框架更重要。

## 参考来源

- [OpenAI Building agents](https://developers.openai.com/tracks/building-agents)
- [Anthropic Building effective agents](https://www.anthropic.com/engineering/building-effective-agents)
- [Anthropic Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)
- [Model Context Protocol 官方介绍](https://modelcontextprotocol.io/docs/getting-started/intro)
