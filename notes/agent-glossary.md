# AI Agent 新手术语表：从 Agent、Tool 到 Eval、Trace

## 审计信息

- 来源：本地 Codex / skills / 自动化浏览 / 知识库维护经验；结合 OpenAI Agents SDK、OpenAI Building agents、Anthropic agent 工程文章、MCP 官方文档整理。
- 作者：本地整理；公开版由 Codex 脱敏改写。
- 适合读者：刚开始看 Agent 教程，遇到英文术语和工程词汇容易卡住的新手。
- 目标：提供一张可查、可转发、可串联到仓库内其他笔记的中文术语表。
- 隐私处理：不包含本地路径、账号、聊天记录、后台数据、私有 skill 源码、密钥或未发布项目。

## 怎么用这张表

这不是官方词典，而是面向新手的实战解释。

建议用法：

1. 第一次读 Agent 教程时，遇到不懂的词先查这里。
2. 做第一个任务前，重点看 Agent、Tool、Context、Guardrail、Eval、Trace。
3. 看到很像的词时，先看“容易混淆”栏。
4. 真要落地时，再打开“延伸阅读”里的专题笔记。

## 核心对象

| 术语 | 一句话解释 | 新手容易混淆 | 延伸阅读 |
|---|---|---|---|
| Agent | 配好指令、工具和运行边界，能围绕目标推进任务的系统 | 不是所有聊天机器人都是 Agent | [概念 FAQ](agent-concepts-faq.md) |
| Chatbot | 主要通过对话回答问题的 AI | 会聊天不等于能自主做事 | [新手路线](agent-beginner-learning-path.md) |
| Workflow | 按预设步骤执行的流程 | 很多任务用 workflow 比 Agent 更稳 | [概念 FAQ](agent-concepts-faq.md) |
| Tool | Agent 可以调用的外部能力 | 工具不是越多越好 | [MCP vs CLI](agent-tooling-mcp-vs-cli.md) |
| Skill | 给 Agent 的可复用任务说明书 | 不是普通工具名，也不是空泛提示词 | [Skills 导览](../skills/README.md) |
| Model | 负责理解、推理和生成的模型 | 模型强不代表系统可靠 | [新手路线](agent-beginner-learning-path.md) |
| Instructions | 给 Agent 的目标、身份、规则和行为要求 | 不是越长越好，关键是清楚和可执行 | [第一个任务](first-agent-web-research-task.md) |

## 工具和接口

| 术语 | 一句话解释 | 新手容易混淆 | 延伸阅读 |
|---|---|---|---|
| API | 服务之间交换数据和动作的接口 | API 适合稳定系统集成，不等于网页操作 | [MCP vs CLI](agent-tooling-mcp-vs-cli.md) |
| CLI | 命令行工具入口 | 不比 MCP 低级，很多低风险任务更适合 CLI | [MCP vs CLI](agent-tooling-mcp-vs-cli.md) |
| MCP | 连接 AI 应用与外部工具、数据源和 workflow 的开放协议 | MCP 是协议，不是 skill，也不是安全保证 | [MCP vs CLI](agent-tooling-mcp-vs-cli.md) |
| Function tool | 把一个函数包装成模型可调用的工具 | 要写清参数、返回值和边界 | [概念 FAQ](agent-concepts-faq.md) |
| Browser automation | 用程序驱动浏览器打开、点击、截图、提取页面内容 | 不等于可以绕过登录、付费墙或验证码 | [自动化浏览路线](agent-automation-browser.md) |
| Computer use | 让模型观察并操作软件界面 | 风险更高，适合有人工确认的场景 | [自动化浏览路线](agent-automation-browser.md) |
| RPA | 按规则操作软件界面的自动化 | 适合固定流程，不擅长模糊判断 | [概念 FAQ](agent-concepts-faq.md) |

## 上下文和记忆

| 术语 | 一句话解释 | 新手容易混淆 | 延伸阅读 |
|---|---|---|---|
| Context | Agent 当前能看到的任务、资料、历史、规则和工具结果 | 不是把所有东西塞进去就更好 | [个人知识库](personal-knowledge-base-agent-wiki.md) |
| Context window | 模型一次能处理的上下文容量 | 容量大不等于信息质量高 | [个人知识库](personal-knowledge-base-agent-wiki.md) |
| Context engineering | 选择、整理、压缩和更新上下文的工程方法 | 不只是写提示词，而是决定给模型看什么 | [个人知识库](personal-knowledge-base-agent-wiki.md) |
| Memory | 跨任务或跨会话保留下来的信息 | 记得多不一定好，要可审计、可更新 | [个人知识库](personal-knowledge-base-agent-wiki.md) |
| Session | 一段连续运行或对话状态 | session 不是长期知识库 | [个人知识库](personal-knowledge-base-agent-wiki.md) |
| Grounding | 让回答建立在资料、工具结果或外部证据上 | 不是凭模型记忆猜 | [第一个任务](first-agent-web-research-task.md) |
| Retrieval | 从文档、网页或数据库取回相关资料 | 检索结果要验来源，不等于事实本身 | [第一个任务](first-agent-web-research-task.md) |

## 安全和质量

| 术语 | 一句话解释 | 新手容易混淆 | 延伸阅读 |
|---|---|---|---|
| Guardrail | 限制 Agent 不能做什么、何时要检查或确认的护栏 | 不是一句“注意安全”就够了 | [新手路线](agent-beginner-learning-path.md) |
| Human-in-the-loop | 高风险动作前让人确认或接管 | 不代表 Agent 失败，而是降低风险 | [第一个任务](first-agent-web-research-task.md) |
| Permission | 工具、文件、账号、数据的访问权限 | 能调用不代表应该调用 | [MCP vs CLI](agent-tooling-mcp-vs-cli.md) |
| Sandbox | 隔离运行环境，降低操作外部系统的风险 | sandbox 也要配合权限和日志 | [Enterprise Harness](enterprise-agent-harness.md) |
| Eval | 用案例、指标或人工标准评估 Agent 是否可靠 | 不是跑一次成功就算可靠 | [Enterprise Harness](enterprise-agent-harness.md) |
| Golden case | 代表性测试样例，用来检查系统是否退化 | 不只是 demo，要覆盖真实风险点 | [Enterprise Harness](enterprise-agent-harness.md) |
| Regression | 以前能做对的事后来做错了 | Agent 更新后必须防回退 | [Enterprise Harness](enterprise-agent-harness.md) |
| Trace | 记录 Agent 每一步做了什么、调用了什么工具、得到什么结果 | 没有 trace 就很难复盘错误 | [Enterprise Harness](enterprise-agent-harness.md) |
| Replay | 用历史输入和轨迹重新跑或复查问题 | 适合调试和版本对比 | [Enterprise Harness](enterprise-agent-harness.md) |

## 编排和协作

| 术语 | 一句话解释 | 新手容易混淆 | 延伸阅读 |
|---|---|---|---|
| Orchestration | 组织多个步骤、工具或 Agent 的方式 | 复杂编排不是第一步 | [新手路线](agent-beginner-learning-path.md) |
| Handoff | 一个 Agent 把任务交给另一个更合适的 Agent | handoff 需要清楚交接上下文 | [Enterprise Harness](enterprise-agent-harness.md) |
| Manager / Worker | 一个主控 Agent 分派任务给多个工作 Agent | 不是 Agent 越多越好 | [概念 FAQ](agent-concepts-faq.md) |
| Router | 根据输入类型把任务分到不同流程或 Agent | 路由错误会让后续全错 | [Enterprise Harness](enterprise-agent-harness.md) |
| Tool use loop | Agent 调工具、看结果、再决定下一步的循环 | 没有停止条件容易失控 | [MCP vs CLI](agent-tooling-mcp-vs-cli.md) |
| Stopping condition | 让 Agent 停下来的条件 | 不能只靠“它觉得完成了” | [Enterprise Harness](enterprise-agent-harness.md) |

## 内容生产和知识库

| 术语 | 一句话解释 | 新手容易混淆 | 延伸阅读 |
|---|---|---|---|
| Markdown note | 可长期保存和链接的文本笔记 | 比聊天记录更适合沉淀知识 | [第一个任务](first-agent-web-research-task.md) |
| Knowledge base | 被持续整理、索引和复用的知识集合 | 不是文件越多越好 | [个人知识库](personal-knowledge-base-agent-wiki.md) |
| Index | 帮你快速找到笔记的目录或地图 | 没有索引，知识库会变成文件堆 | [个人知识库](personal-knowledge-base-agent-wiki.md) |
| Source | 原始资料或证据链接 | 没有 source 的总结很难复查 | [第一个任务](first-agent-web-research-task.md) |
| Audit | 对内容、来源、隐私、质量做检查 | 不是发布后再说 | [贡献规范](../CONTRIBUTING.md) |
| Prompt template | 可复用的任务提示词模板 | 模板要有输入、输出和边界 | [提示词目录](../prompts/README.md) |

## 新手最该先记住的 10 个词

如果你只想先记最重要的，按这个顺序：

1. Agent
2. Workflow
3. Tool
4. Context
5. Guardrail
6. Skill
7. MCP
8. CLI
9. Eval
10. Trace

这 10 个词基本覆盖了“Agent 是什么、怎么做事、怎么接工具、怎么不乱跑、怎么验证”的主线。

## 常见误读

| 误读 | 更准确的说法 |
|---|---|
| Agent 就是 ChatGPT 加自动化 | Agent 是模型、工具、指令、状态、护栏和验证组成的系统 |
| MCP 是 Agent | MCP 是连接工具和数据的协议，不是 Agent 本身 |
| Skill 是一个工具 | Skill 更像任务说明书，可能调用多个工具 |
| 上下文越多越好 | 高信号上下文比大上下文更重要 |
| 有 guardrail 就不会出错 | guardrail 降低风险，但还需要 eval、trace、人工确认 |
| 只要 demo 跑通就能上线 | 还需要测试样例、权限、日志、回放和回归检查 |
| 多 Agent 一定更强 | 多 Agent 增加协作成本，任务边界不清会更乱 |

## 推荐阅读顺序

1. [AI Agent 新手入门路线图](agent-beginner-learning-path.md)
2. [AI Agent 新手概念 FAQ](agent-concepts-faq.md)
3. [第一个 Agent 实战任务](first-agent-web-research-task.md)
4. [Agent 工具调用选型：MCP vs CLI](agent-tooling-mcp-vs-cli.md)
5. [Enterprise Agent Harness 学习笔记](enterprise-agent-harness.md)

## 参考来源

- [OpenAI Agents SDK: Agents](https://openai.github.io/openai-agents-python/agents/)
- [OpenAI Agents SDK: Tools](https://openai.github.io/openai-agents-python/tools/)
- [OpenAI Agents SDK: Guardrails](https://openai.github.io/openai-agents-python/guardrails/)
- [OpenAI Agents SDK: Tracing](https://openai.github.io/openai-agents-python/tracing/)
- [OpenAI Building agents](https://developers.openai.com/tracks/building-agents)
- [Anthropic Building effective agents](https://www.anthropic.com/engineering/building-effective-agents)
- [Anthropic Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)
- [Model Context Protocol 官方介绍](https://modelcontextprotocol.io/docs/getting-started/intro)
