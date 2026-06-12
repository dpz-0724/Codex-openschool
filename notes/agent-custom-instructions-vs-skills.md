# Agent 个性化分层：Custom Instructions、Skills 和一次性 Prompt 怎么分工

## 审计信息

- 整理时间：2026-06-12。
- 来源：Replit 官方 X 动态、Replit 官方博客《Customize Replit Agent with Skills & Custom Instructions》、Replit Agent Skills 与 Agent Customization 文档，以及本仓库已有 skill 触发边界和新工具审计笔记。
- 作者：本地整理；公开版由 Codex 脱敏改写。
- 适合读者：已经开始反复给 Agent 解释偏好、项目结构、代码风格、品牌规范或安全规则，但不知道该放在哪里的新手。
- 目标：把“重复提示词”拆成四层可维护资产：一次性 Prompt、项目约定、Custom Instructions、Skills。
- 隐私处理：不包含账号、浏览器登录态、聊天记录、客户材料、密钥、本地路径、后台截图或内部运营目标。

## 先说结论

Replit 这次动态最值得学的不是“它有了一个技能市场”，而是一个更通用的 Agent 方法：

> 反复说给 Agent 听的内容，不应该永远留在聊天框里。它应该被分层沉淀成规则、技能、项目约定或任务提示。

新手最容易犯两个相反的错误：

1. 每次都重新复制一大段提示词，经验留不下来。
2. 把所有规则都写进全局指令，导致任何任务都背着一堆无关上下文。

更稳的做法是先分层。

| 层级 | 适合放什么 | 不适合放什么 |
|---|---|---|
| 一次性 Prompt | 当前任务目标、输入、交付物、验收方式 | 长期团队规范、通用安全规则 |
| 项目约定 | 当前项目的目录结构、运行命令、技术栈、测试入口 | 跨项目都成立的规则 |
| Custom Instructions | 永远成立的短规则，例如隐私、密钥、语言、代码风格 | 具体任务流程、长篇教程、复杂参考材料 |
| Skills | 某类任务才需要的工作流、检查表、设计系统、API 模式 | 所有任务都要遵守的底线规则 |

## 这条 Replit 动态到底在说什么

Replit 的公开动态大意是：Agent 很强，但默认不记得你的偏好，所以用户会反复说明项目结构、品牌规范等要求。Replit 推出的 Agent Customization 把这件事拆成两部分：

- **Custom Instructions**：写一次，自动注入到每个项目、每个会话。
- **Skills**：只有相关任务出现时才加载的可复用说明。

Replit 官方博客进一步解释：Custom Instructions 适合“不要把密钥提交到版本控制”“默认使用某种代码风格”“遵守数据处理政策”这类总是成立的规则；Skills 更像交给新工程师的一页任务指南，只在 UI、鉴权、安全审查、设计系统、分析埋点等具体任务触发。

这和任何 Agent 工具都相关，不只适用于 Replit。Codex、Claude Code、GitHub Copilot CLI 或本地 Agent 工作流都要面对同一个问题：长期知识到底放哪里。

## 四层决策表

当你有一条想告诉 Agent 的规则，先用这张表判断。

| 问题 | 如果答案是 | 放哪里 |
|---|---|---|
| 只对这一次任务有效吗？ | 是 | 一次性 Prompt |
| 只对当前仓库或当前项目有效吗？ | 是 | 项目约定 / repo guidance |
| 任何任务都必须遵守吗？ | 是 | Custom Instructions |
| 只有某类任务才需要吗？ | 是 | Skill |
| 会不会涉及工具权限、账号、发布、删除、付款？ | 是 | Prompt 或 Skill 里加人工确认点 |
| 写不出不适用场景吗？ | 是 | 暂时不要做成 Skill |

一句话判断：

```text
总是成立，写短规则。
反复出现，写成 skill。
只在当前项目成立，写进项目约定。
只做这一次，留在 prompt。
```

## 什么时候放 Custom Instructions

Custom Instructions 适合少量、稳定、跨项目都成立的规则。

好例子：

```text
不要把密钥、cookie、访问凭证或未脱敏隐私写入公开文件。
默认用中文解释方案，但代码和文件名遵循项目现有语言。
修改文件前先确认范围，完成后给出验证结果。
涉及发布、付款、删除、提交远端、读取私有账号时必须先停下来确认。
```

坏例子：

```text
以后所有网页整理任务都按 15 步流程做，附上这个长模板和 8 个示例。
以后所有 UI 都使用某个特定产品的品牌色。
以后所有项目都按 React + Tailwind + Supabase 搭建。
```

问题在于：Custom Instructions 会反复进入上下文。它应该像底线规则，不应该像一本手册。

## 什么时候放 Skill

Skill 适合某一类会反复出现、输入输出稳定、能写清验收方式的任务。

好例子：

| Skill | 触发场景 | 输出 |
|---|---|---|
| `web-note` | 用户给公开 URL，要整理成学习笔记 | Markdown、来源、自检 |
| `security-review` | 改鉴权、支付、权限、敏感数据 | 风险清单、diff 审查、阻断项 |
| `design-system-ui` | 做页面或组件，必须遵守设计系统 | 页面结构、组件规则、视觉检查 |
| `ppt-master-workflow` | 把长文档转课程或汇报 PPT | 页级大纲、视觉路线、验收点 |
| `agent-trace-review` | 复盘一次 Agent 任务是否可信 | 来源、工具、产物、失败、验证证据 |

不适合做 Skill 的内容：

- 只用一次的任务要求。
- 没有固定输入输出的泛泛偏好。
- 需要真实账号、客户材料或私有路径才能说明清楚的流程。
- 和已有 skill 高度重复的能力。
- 只有宣传口号，没有验收标准的“效率提升方法”。

## 什么时候放项目约定

项目约定适合当前仓库里的稳定事实。

例如：

```text
项目使用 pnpm。
测试命令是 pnpm test。
文档都放在 docs/。
不要修改 generated/。
PR 前必须跑 markdown 链接检查。
```

这些东西不一定适合全局 Custom Instructions，因为换个项目可能完全不同；也不一定适合 Skill，因为它不是某类任务的方法，而是这个项目的事实。

如果你的工具支持类似 `AGENTS.md`、repo guidance、project rules、workspace settings，就把这类内容放到项目层。

## 什么时候只写一次性 Prompt

一次性 Prompt 适合当前任务的临时输入和验收条件。

例如：

```text
请把这篇公开文章整理成 Markdown 笔记。
目标读者是刚接触 Agent 的新手。
不要复制长篇原文。
输出包括：一句话结论、要点表、可复制提示词、风险提醒、来源链接。
```

不要把这种具体任务塞进全局指令，否则以后所有任务都会被它干扰。

## 一个可复制的分层模板

当你发现自己第三次重复同一段提示词时，用这个模板重写。

```markdown
# Agent 个性化分层记录

## 重复内容

我反复告诉 Agent 的话：

## 判断

| 问题 | 答案 |
|---|---|
| 是否永远成立 | 是 / 否 |
| 是否只对当前项目成立 | 是 / 否 |
| 是否只对某类任务成立 | 是 / 否 |
| 是否只对这一次任务成立 | 是 / 否 |
| 是否有稳定输入 | 是 / 否 |
| 是否有稳定输出 | 是 / 否 |
| 是否能写出不适用场景 | 是 / 否 |
| 是否涉及敏感权限 | 是 / 否 |

## 归类

- 放入 Custom Instructions：
- 放入项目约定：
- 做成 Skill：
- 只留在 Prompt：

## 验收

- Agent 是否少问重复问题：
- 是否减少误触发：
- 是否保留来源、产物和验证证据：
- 是否没有泄露隐私或扩大权限：
```

## 例子 1：安全规则

原始重复提示词：

```text
不要把密钥、cookie、账号信息写到代码或 README 里，遇到真实账号相关操作要先问我。
```

归类：

| 内容 | 放哪里 | 原因 |
|---|---|---|
| 不写入密钥和账号信息 | Custom Instructions | 任何任务都成立 |
| 真实账号操作前确认 | Custom Instructions | 是安全底线 |
| 当前项目哪些文件不能读 | 项目约定 | 只对当前仓库成立 |
| 做安全审查的 12 项流程 | Skill | 只有安全审查任务才需要 |

## 例子 2：设计系统

原始重复提示词：

```text
我们的页面使用 8px radius、按钮用图标、不要用大面积紫色渐变，Dashboard 要信息密度高。
```

归类：

| 内容 | 放哪里 | 原因 |
|---|---|---|
| 当前产品的品牌色、组件规范 | Skill 或项目约定 | 只在 UI 任务或当前产品成立 |
| “不要让文本溢出” | Custom Instructions 可选 | 如果你所有 UI 任务都需要 |
| Dashboard 信息架构检查表 | Skill | 只有 dashboard 设计任务触发 |
| 当前页面的具体标题和布局 | 一次性 Prompt | 只对这次任务成立 |

## 例子 3：内容知识库

原始重复提示词：

```text
整理公开资料时要保留来源，不要搬运全文，输出 Markdown，最后检查隐私。
```

归类：

| 内容 | 放哪里 | 原因 |
|---|---|---|
| 不搬运全文、不放隐私 | Custom Instructions | 是公开内容底线 |
| Markdown 笔记结构 | Skill | 公开网页整理任务反复出现 |
| 本仓库目录结构 | 项目约定 | 只对当前知识库成立 |
| 本次文章 URL 和读者定位 | 一次性 Prompt | 只对当前任务成立 |

## 写 Skill 前先回答 8 个问题

Replit 官方资料反复强调：Skill 的 description 很关键，因为 Agent 会先读 name 和 description，相关时才加载完整内容。写 skill 前先答：

1. 这个任务是否会重复出现？
2. 输入是否稳定？
3. 输出是否稳定？
4. 是否能写出不适用场景？
5. 是否有验收方式？
6. 是否和已有 skill 重复？
7. 是否涉及敏感权限？
8. 是否会过期，谁来维护？

如果第 4、5、8 条答不出来，先别发布成 skill。

## 安装现成 Skills 时也要审计

Replit 提供预制 skills，也支持从外部来源安装。预制不等于不用审计，外部来源更要仔细看。

安装前至少做这 5 件事：

| 检查 | 为什么 |
|---|---|
| 读 `SKILL.md` | Skill 是 Agent 会遵循的指令 |
| 看来源 | 确认作者、仓库、维护状态 |
| 查敏感动作 | 是否要求读取密钥、账号、私有数据 |
| 看外链和脚本 | 是否下载、上传或调用未知服务 |
| 低风险试用 | 先用公开样例，不直接上真实项目 |

这和本仓库的 [新工具 / Skill 安装前审计清单](agent-tool-skill-audit-checklist.md) 是同一个原则：先审计，再安装。

## 维护规则：少而精

个性化内容会腐烂。Skill、项目约定和全局规则都要定期清理。

建议每月问一次：

```text
这条规则最近是否真的减少了重复沟通？
它是否和别的规则冲突？
它是否过时？
它是否太宽，导致误触发？
它是否应该从全局规则降级为 skill？
它是否应该从 skill 升级为项目约定或脚本？
```

尤其要警惕两种情况：

- Custom Instructions 越写越长，任何任务都被旧规则拖累。
- Skills 越装越多，description 重叠，Agent 不知道该用哪个。

## 可复制 Prompt：让 Agent 帮你分层

```text
请帮我把下面这段反复使用的 Agent 提示词做分层整理。

原始提示词：
[粘贴内容]

请输出：
1. 哪些内容应该放 Custom Instructions，原因是什么。
2. 哪些内容应该放项目约定，原因是什么。
3. 哪些内容应该做成 Skill，原因是什么。
4. 哪些内容只应该留在一次性 Prompt。
5. 如果要做成 Skill，请写 name、description、适用场景、不适用场景、输入、输出和验收方式。
6. 哪些内容涉及隐私、账号、密钥、发布、删除、付款或提交远端，需要人工确认。

要求：
- 不要把所有内容都塞进全局规则。
- 不要把一次性任务包装成 skill。
- 如果某条规则太泛，请指出并缩小。
```

## 和本仓库其他内容的关系

- Skill description 怎么写：读 [Skill 描述怎么写才不误触发](skill-description-trigger-boundaries.md)。
- 安装外部 skill 前怎么审计：读 [Agent 新工具 / Skill 安装前审计清单](agent-tool-skill-audit-checklist.md)。
- 工具、skill、MCP 怎么分：读 [Agent 工具调用选型](agent-tooling-mcp-vs-cli.md)。
- 长期协作知识怎么沉淀：读 [Agent 共享上下文与知识编译](agent-shared-context-knowledge-compile.md)。
- 终端里的重复任务怎么沉淀：读 [终端 Agent 可重复工作流](agent-terminal-workflow-card.md)。

## 参考来源

- [Replit X: AI agents are powerful, but they don't remember your preferences](https://x.com/Replit/status/2065146579326271883)
- [Replit Blog: Customize Replit Agent with Skills & Custom Instructions](https://replit.com/blog/custom-skills)
- [Replit Docs: Agent Skills](https://docs.replit.com/references/agent/skills)
- [Replit Docs: Improve Agent with skills](https://docs.replit.com/learn/agent-skills)
- [Replit Docs: Use Agent Skills](https://docs.replit.com/build/use-agent-skills)
- [Replit Docs: Build an Agent](https://docs.replit.com/build/build-an-agent)
