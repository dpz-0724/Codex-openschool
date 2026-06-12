# AI Agent 新手概念 FAQ：Agent、Workflow、Skill、MCP、CLI、RPA 到底有什么区别

## 审计信息

- 来源：本地 Codex / skills / 自动化浏览使用经验；结合 OpenAI、Anthropic、Model Context Protocol、Playwright 的公开一手资料整理。
- 作者：本地整理；公开版由 Codex 脱敏改写。
- 适合读者：刚开始学 AI Agent，看到 Agent、Workflow、Skill、MCP、RPA、浏览器自动化等词容易混淆的新手。
- 目标：让读者先建立“什么时候该用什么”的判断框架，避免一上来被概念、框架和工具名带偏。
- 隐私处理：不包含本地路径、账号、聊天记录、后台数据、私有 skill 源码、密钥或未发布项目。

## 先给结论

不要先问“哪个词更高级”，先问“我要解决什么问题”。

| 词 | 最简单理解 | 典型用途 | 新手最容易误解 |
|---|---|---|---|
| Chatbot | 会回答问题的 AI | 问答、解释、写草稿 | 把所有 AI 问答都叫 Agent |
| Workflow | 按固定步骤跑的流程 | 批处理、审批、资料整理、固定流水线 | 觉得它不如 Agent，其实很多任务更适合 workflow |
| Agent | 能围绕目标自主选择步骤和工具的系统 | 多步任务、信息不完整、需要边做边判断 | 以为越自主越好，忽略验证和边界 |
| Skill | 给 Agent 的可复用操作手册 | 固定场景的工作方法、工具规则、质量标准 | 把普通工具、框架、想法都叫 skill |
| MCP | AI 应用连接外部工具和数据的标准协议 | 多工具共享、权限、审计、长期工具层 | 以为接了 MCP 就自动安全、自动好用 |
| CLI | 命令行工具入口 | 本地脚本、开发工具、快速验证 | 以为不如 MCP 正规，其实很多轻量任务更合适 |
| RPA | 按规则操作软件界面的自动化 | 表格录入、固定后台流程、重复点击 | 把 RPA 和 Agent 混成一件事 |
| 浏览器自动化 | 用程序驱动网页 | 网页测试、资料抓取、页面验证、登录态任务 | 忘记版权、登录、反爬和账号风险 |

## 1. Chatbot 和 Agent 有什么区别

Chatbot 的重点是“回答”。你问一句，它回一句。它可以很聪明，也可以帮你写文章、解释概念、生成代码片段，但它通常不负责持续推进一个外部任务。

Agent 的重点是“做事”。一个实用 Agent 通常会有：

- Model：负责理解、推理和生成。
- Tools：可以访问外部数据、调用 API、读写文件或操作网页。
- Instructions / Guardrails：告诉它目标、边界、质量标准和不能做什么。

OpenAI 的 agent 构建资料也把 agent 的基础组成归纳为 model、tools、instructions。新手可以先记住：

> 如果 AI 只是在聊天，它更像 chatbot；如果它能围绕目标调用工具、检查结果并推进多步任务，它才开始接近 Agent。

例子：

| 任务 | 更像什么 |
|---|---|
| “解释一下 MCP 是什么” | Chatbot |
| “阅读这 3 个官方链接，整理一篇带来源的新手笔记” | Agent |
| “每天 9 点抓取固定页面并生成报告” | Workflow / Automation |
| “发现页面结构变了以后自己调整抓取策略并记录原因” | Agent |

## 2. Workflow 和 Agent 有什么区别

Anthropic 在 agent 工程文章里给过一个很实用的区分：

- Workflow：LLM 和工具按预设代码路径被编排。
- Agent：模型能动态决定自己的流程和工具使用方式。

换成新手语言：

| 维度 | Workflow | Agent |
|---|---|---|
| 步骤 | 预先写好 | 可根据情况调整 |
| 稳定性 | 更强 | 取决于判断和护栏 |
| 适合任务 | 规则清楚、路径固定 | 信息不完整、需要探索 |
| 风险 | 容易僵化 | 容易跑偏 |
| 验收 | 看每一步是否按流程完成 | 看目标是否达成、过程是否可解释 |

很多人一开始追求“全自动 Agent”，但真实工作里，大量任务更适合 workflow：

- 固定格式日报。
- 文件批量转换。
- 表格清洗。
- 文章发布前检查。
- 每次都按同样规则跑的质量门禁。

更好的做法是：

1. 先把固定部分做成 workflow。
2. 把需要判断、探索、取舍的部分交给 Agent。
3. 最终用人工确认或自动验收守住高风险边界。

## 3. Skill 到底是什么

在 Codex / Claude / 许多 Agent 使用场景里，skill 可以理解成：

> 给 Agent 的可复用操作手册。

它通常不是一个普通工具名，也不是一个宏大的框架，而是一份告诉 Agent “什么时候触发、怎么做、用什么工具、怎么验收、哪里不能碰”的说明。

一个好的 skill 至少应该说清：

- 触发场景：用户说什么、任务长什么样时使用。
- 输入：需要哪些资料、文件、链接或约束。
- 操作流程：先做什么，再做什么，遇到失败怎么处理。
- 工具边界：能调用什么，不能调用什么。
- 输出：最终交付什么格式。
- 验收：怎么判断做完了，怎么检查质量。
- 安全边界：隐私、账号、发布、删除、付款、版权等限制。

### 什么不是好 skill

这些内容不应该随便包装成 skill：

- 只有一个标题，没有流程。
- 只是一个软件名或库名。
- 只是“让 AI 更聪明”的泛泛提示词。
- 必须依赖私有账号、聊天记录、客户材料才能讲清价值。
- 和已有 skill 完全重复，只是换个名字。

## 4. MCP 和 Skill 是一回事吗

不是。

MCP 是连接工具和数据的协议。它解决的是“AI 应用如何标准化访问外部系统”。

Skill 是让 Agent 在某类任务中表现稳定的操作手册。它解决的是“Agent 在这个场景里应该怎么做”。

二者可以配合：

| 组合 | 例子 |
|---|---|
| Skill + MCP | skill 说明何时查知识库，MCP Server 提供知识库检索工具 |
| Skill + CLI | skill 说明如何检查 Markdown，CLI 执行 `rg`、lint、脚本 |
| Skill + 浏览器自动化 | skill 说明如何审计网页，浏览器自动化打开页面、截图、提取文本 |
| Skill + 人工确认 | skill 说明发布前必须让用户确认标题、链接、风险 |

新手不要把 MCP 当成 skill，也不要把 skill 当成 MCP。一个是工具连接层，一个是任务方法层。

## 5. MCP 和 CLI 怎么选

详细选型可以看：[Agent 工具调用选型：什么时候用 MCP，什么时候用 CLI](agent-tooling-mcp-vs-cli.md)。

最短判断：

- 要长期复用、多 Agent 共享、权限控制、审计，优先 MCP 或受控 API。
- 要本地快速验证、低风险文件处理、已有成熟命令，优先 CLI。
- 要操作网页、看页面状态、验证 UI，考虑浏览器自动化。
- 要对外发布、付款、删除、修改生产数据，必须人工确认。

## 6. RPA 和 Agent 有什么区别

RPA 更像“按剧本操作软件”。它擅长重复、固定、结构清楚的任务，比如：

- 打开后台。
- 按固定位置点击。
- 把表格数据填到系统里。
- 下载固定报表。
- 按规则归档文件。

Agent 更像“围绕目标做判断”。它更适合：

- 输入不固定。
- 网页结构可能变化。
- 需要读资料、做取舍、解释原因。
- 需要在失败后换策略。
- 需要把结果写成报告或笔记。

但 Agent 不一定比 RPA 更适合所有任务。固定重复任务用 RPA / 脚本 / workflow 往往更稳。Agent 更适合处理模糊和变化，但也更需要护栏。

## 7. 浏览器自动化和 Agent 是什么关系

浏览器自动化是一类工具能力，不等于 Agent。

Playwright 官方把它定位为面向测试、脚本和 AI agent workflows 的浏览器自动化能力，可以驱动 Chromium、Firefox 和 WebKit。

Agent 使用浏览器自动化时，可以做：

- 打开公开网页并提取内容。
- 验证页面上的按钮、表单、布局。
- 对本地网页做截图和回归检查。
- 在用户授权下使用登录态页面。
- 判断网页是否需要登录、是否有反爬或版权边界。

但浏览器自动化有几条红线：

- 不绕过验证码。
- 不绕过付费墙。
- 不批量抓取违反站点规则的内容。
- 不静默操作用户账号。
- 不自动发布、删除、付款或修改外部系统。

## 8. 新手应该怎么开始

不要先装一堆框架。先做一个小闭环：

1. 选一个低风险任务：整理一篇公开网页、检查一个 Markdown、生成一个学习笔记。
2. 判断它更像 chatbot、workflow、agent 还是脚本。
3. 明确输入、输出和验收标准。
4. 只给 Agent 必要工具。
5. 让 Agent 做完后自己检查结果。
6. 把有价值的流程写成一张 skill 草稿。
7. 如果重复使用，再考虑封装成正式 workflow、CLI 脚本或 MCP 工具。

## 9. 判断题

下面这些判断可以帮你快速练习：

| 场景 | 更适合 |
|---|---|
| 每天固定时间把 3 个公开 RSS 摘要成日报 | Workflow |
| 用户临时给 5 个网页，让 AI 判断哪些值得读 | Agent |
| 把一个目录里的 Markdown 全部检查本地路径 | CLI / Workflow |
| 让多个 Agent 都能查同一个内部知识库，并按权限返回 | MCP / API |
| 打开网页看按钮有没有遮挡，截一张图 | 浏览器自动化 |
| 按固定规则把 Excel 录入旧系统 | RPA / 脚本 |
| 写一篇“为什么 MCP 不等于 Agent”的解释 | Chatbot / Agent，取决于是否要查资料 |

## 10. 最小术语表

| 术语 | 一句话解释 |
|---|---|
| Agent | 能围绕目标调用工具、推进多步任务并检查结果的系统 |
| Workflow | 预设路径的多步骤流程 |
| Tool | Agent 可以调用的外部能力 |
| Skill | 给 Agent 的可复用任务说明书 |
| MCP | 连接 AI 应用与外部系统的开放协议 |
| CLI | 命令行工具入口 |
| API | 服务之间交换数据和动作的接口 |
| RPA | 按规则操作软件界面的自动化 |
| Guardrail | 限制 Agent 不能做什么、什么时候要确认的护栏 |
| Eval | 用测试题、案例或指标评估 Agent 是否可靠 |
| Trace | 记录 Agent 每一步做了什么，方便复盘和调试 |
| Context | Agent 当前能看到的任务、资料、历史和规则 |

## 11. 一句话收尾

新手入门 Agent，不要被名词拖着走。先识别任务类型，再选择工具形态，最后用 skill、workflow、guardrail 和 eval 把它变成稳定可复用的能力。

## 参考来源

- [OpenAI Practical Guide to Building Agents](https://cdn.openai.com/business-guides-and-resources/a-practical-guide-to-building-agents.pdf)
- [OpenAI Agents SDK: Agents](https://openai.github.io/openai-agents-python/agents/)
- [Anthropic: Building Effective AI Agents](https://www.anthropic.com/research/building-effective-agents)
- [Anthropic: Effective Context Engineering for AI Agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)
- [Model Context Protocol 官方介绍](https://modelcontextprotocol.io/docs/getting-started/intro)
- [Playwright 官方首页](https://playwright.dev/)
