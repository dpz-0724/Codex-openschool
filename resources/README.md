# AI Agent 一手资源中文导读

## 审计信息

- 整理时间：2026-06-12。
- 来源标准：官方文档、官方博客、官方 GitHub 仓库或协议官网。
- 作者：本地整理；公开版由 Codex 脱敏改写。
- 适合读者：已经读过本仓库入门路线，想回到一手资料确认概念和工程边界的新手。
- 目标：告诉读者先读哪几份官方资料、为什么读、读完要落到哪一个练习或笔记。
- 隐私处理：不包含本地路径、账号、聊天记录、客户材料、私有 skill 源码、密钥或未发布项目。

## 先说结论

一手资料不是越多越好。新手最容易犯的错误是一次打开十几篇官方文档，最后只记住几个术语。

这页只保留当前最值得反复回看的几类资料：

1. Agent 到底是什么。
2. Workflow 和 Agent 怎么分。
3. Tools、MCP、skills、guardrails 怎么理解。
4. 为什么上下文和环境比“神奇提示词”更重要。
5. 什么时候需要 spec，而不是直接让 Agent 写代码。

读官方资料的目标不是背概念，而是把它转成本仓库里的练习、模板和判断表。

## 30 分钟阅读路线

如果你只想快速建立正确直觉，按这个顺序读：

| 顺序 | 资料 | 读它为了解决什么 | 读完落到仓库哪里 |
|---:|---|---|---|
| 1 | [Anthropic: Building effective agents](https://www.anthropic.com/engineering/building-effective-agents) | 分清 workflow 和 agent，不要一上来追复杂框架 | [概念 FAQ](../notes/agent-concepts-faq.md) |
| 2 | [OpenAI: Building agents](https://developers.openai.com/tracks/building-agents) | 建立 agent = instructions + guardrails + tools + action 的基本框架 | [新手路线图](../notes/agent-beginner-learning-path.md) |
| 3 | [OpenAI: A practical guide to building agents](https://cdn.openai.com/business-guides-and-resources/a-practical-guide-to-building-agents.pdf) | 判断什么时候该做 agent、怎么设计工具、护栏和人在回路 | [权限分级清单](../notes/agent-autonomy-permission-ladder.md) |
| 4 | [Model Context Protocol: What is MCP?](https://modelcontextprotocol.io/docs/getting-started/intro) | 理解 MCP 是连接协议，不是万能自动化方案 | [MCP vs CLI](../notes/agent-tooling-mcp-vs-cli.md) |
| 5 | [Anthropic: Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) | 理解上下文是有限资源，不是把资料全部塞进去 | [长任务环境规格](../notes/agent-long-task-environment-spec.md) |

不建议第一天就读完所有链接。先读 1-2 篇，然后做 [Agent 新手低风险练习室](../labs/README.md) 的练习 1 和练习 2。

## 按问题找资料

### 我还分不清 Agent、Workflow、Chatbot

先读：

- [Anthropic: Building effective agents](https://www.anthropic.com/engineering/building-effective-agents)
- [OpenAI: Building agents](https://developers.openai.com/tracks/building-agents)

读法：

- 只看定义、workflow / agent 区别、工具和护栏这几段。
- 不急着看所有架构图。
- 读完后用自己的话写 3 句话：什么不是 agent，什么时候 workflow 已经够用，什么时候才需要 agent。

落地：

- [AI Agent 新手概念 FAQ](../notes/agent-concepts-faq.md)
- [AI Agent 新手术语表](../notes/agent-glossary.md)

### 我想知道什么时候该做工具或 MCP

先读：

- [Model Context Protocol: What is MCP?](https://modelcontextprotocol.io/docs/getting-started/intro)
- [MCP Security Best Practices](https://modelcontextprotocol.io/docs/tutorials/security/security_best_practices)

读法：

- 先理解 MCP 是把 AI 应用接到外部数据、工具和 workflow 的标准化方式。
- 再读安全页，特别注意授权、同意、token、代理服务和最小权限。
- 不要把“支持 MCP”理解成“天然安全”。

落地：

- [Agent 工具调用选型：什么时候用 MCP，什么时候用 CLI](../notes/agent-tooling-mcp-vs-cli.md)
- [Agent 自主权限分级清单](../notes/agent-autonomy-permission-ladder.md)

### 我想让 Agent 写代码，但不想反复返工

先读：

- [GitHub Spec Kit](https://github.com/github/spec-kit)
- [warpdotdev/common-skills](https://github.com/warpdotdev/common-skills)

读法：

- 关注 spec、clarify、plan、tasks、implement 的顺序。
- 重点不是安装哪个工具，而是先把功能需求、技术计划和验收拆开。
- 小任务不用完整 SDD，10 行 spec 就够。

落地：

- [Agent 编程前的 10 行 Spec 模板](../notes/agent-coding-10-line-spec-template.md)
- [AI 可执行 PRD](../notes/agent-executable-prd.md)

### 我想系统学一门 Agent 课程

先读：

- [Microsoft AI Agents for Beginners](https://github.com/microsoft/ai-agents-for-beginners)

读法：

- 它适合作为课程型补充，不适合替代本仓库的低风险入门练习。
- 先看 Intro、Tool Use、Trustworthy Agents、Planning、Production、Protocols 这几课。
- 代码样例可能依赖 Microsoft 生态，初学者可以先读概念和设计模式。

落地：

- [从这里开始：AI Agent 新手导读](../START_HERE.md)
- [Agent 新手低风险练习室](../labs/README.md)

### 我想理解长任务为什么容易跑偏

先读：

- [Anthropic: Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)
- [OpenAI: A practical guide to building agents](https://cdn.openai.com/business-guides-and-resources/a-practical-guide-to-building-agents.pdf)

读法：

- 关注 context 是有限资源、长循环需要持续筛选信息。
- 关注 guardrails 和 human intervention，不要把“能自主跑更久”当成目标本身。
- 读完后先写环境规格，再交给 Agent 跑长任务。

落地：

- [Agent 长任务环境规格模板](../notes/agent-long-task-environment-spec.md)
- [Enterprise Agent Harness 学习笔记](../notes/enterprise-agent-harness.md)

## 新手容易误读的 7 件事

| 误读 | 更稳的理解 |
|---|---|
| Agent 就是更会聊天的模型 | Agent 要能在边界内使用工具并替用户推进任务 |
| Workflow 不如 Agent 高级 | 固定流程能解决的问题，workflow 更可控、更便宜、更容易验收 |
| MCP 等于自动化能力 | MCP 是连接协议，具体能做什么取决于 server、权限和工具设计 |
| 工具越多越强 | 工具越多，权限面、错误面和上下文成本也越大 |
| 提示词越长越稳 | 长上下文会稀释注意力，要筛选、压缩、按需取回 |
| Spec 是浪费时间 | 模糊任务先写 spec，通常比让 Agent 猜完再返工更快 |
| 人在回路代表不够智能 | 高风险动作和早期部署需要人来确认、接管和建立评估循环 |

## 把一手资料转成仓库内容的方法

每次看到一篇官方资料，不要直接摘抄。按这张表处理：

| 步骤 | 问题 | 产物 |
|---|---|---|
| 1. 定位 | 它解决什么真实问题？ | 一句话问题 |
| 2. 过滤 | 哪些内容对新手暂时没必要？ | 删除清单 |
| 3. 转译 | 能不能变成表格、判断树、提示词或练习？ | 可执行结构 |
| 4. 验收 | 读者做完后能产生什么结果？ | 通过标准 |
| 5. 风险 | 是否涉及隐私、版权、账号、权限或高风险动作？ | 边界说明 |

如果一篇资料只能转成“这里有一个链接”，它暂时不该进入主入口。

## 可复制读法提示词

```text
请帮我精读下面这篇 AI Agent 官方资料。

资料链接：
[粘贴链接]

我的目标：
我是 AI Agent 新手，想知道这篇资料对实际使用 Codex / Agent / skills 有什么帮助。

请输出：
1. 这篇资料解决的核心问题。
2. 适合新手先读的 3-5 个部分。
3. 可以暂时跳过的部分。
4. 3 条最重要的工程原则。
5. 它和 tools、MCP、skills、guardrails、context、spec 的关系。
6. 我读完后可以做的一个低风险练习。
7. 需要人工确认或注意隐私的边界。

要求：
- 不复制长篇原文。
- 涉及事实必须保留原链接。
- 不确定的地方写“待核验”。
```

## 来源索引

- [OpenAI: Building agents](https://developers.openai.com/tracks/building-agents)
- [OpenAI: A practical guide to building agents](https://cdn.openai.com/business-guides-and-resources/a-practical-guide-to-building-agents.pdf)
- [Anthropic: Building effective agents](https://www.anthropic.com/engineering/building-effective-agents)
- [Anthropic: Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)
- [Microsoft AI Agents for Beginners](https://github.com/microsoft/ai-agents-for-beginners)
- [Model Context Protocol: What is MCP?](https://modelcontextprotocol.io/docs/getting-started/intro)
- [MCP Security Best Practices](https://modelcontextprotocol.io/docs/tutorials/security/security_best_practices)
- [GitHub Spec Kit](https://github.com/github/spec-kit)
- [warpdotdev/common-skills](https://github.com/warpdotdev/common-skills)

## 维护规则

这个目录只收一手或接近一手的资料。后续新增资源必须满足：

1. 能确认来源和作者。
2. 能说明适合谁、解决什么问题。
3. 能链接到本仓库某篇笔记、提示词或练习。
4. 不复制长篇原文。
5. 不把过期 API、未经核验的工具能力或社交媒体摘要当成官方事实。
