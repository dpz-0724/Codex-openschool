# AI Agent 新手入门路线图：从会聊天到会让 Agent 做事

## 审计信息

- 来源：本地使用 Codex、skills、自动化浏览、PPT、知识库维护等经验；结合 OpenAI、Anthropic、Microsoft 的公开一手资料做结构化整理。
- 作者：本地整理；公开版由 Codex 脱敏改写。
- 适合读者：听过 AI Agent，但还不知道怎么开始实践的新手。
- 目标：让读者知道先学什么、避开什么坑、第一周做出哪些可见产物。
- 隐私处理：不包含本地路径、账号、聊天记录、客户材料、密钥、后台数据或未发布项目。

## 1. 先把 Agent 讲清楚

如果一个 AI 只是回答问题，它更像聊天机器人。

如果一个 AI 能根据目标调用工具、读取资料、操作文件、访问网页、检查结果，并在多步骤任务里持续推进，它才开始接近 Agent。

一个实用的 Agent 至少有四个部分：

| 部分 | 新手理解 | 例子 |
|---|---|---|
| 指令 | 它应该做什么 | “你是一个资料整理助手” |
| 工具 | 它能做什么 | 搜索网页、读取 PDF、操作浏览器、写文件 |
| 上下文 | 它当前知道什么 | 用户目标、已读资料、当前文件、历史决策 |
| 护栏 | 它不能做什么 | 不泄露隐私、不越权发布、不凭空编数据 |

OpenAI 的 Agent 入门材料把 Agent 概括为有指令、护栏和工具访问能力，并能代表用户采取行动的系统。Anthropic 则强调一个重要区分：workflow 是预设路径，agent 是模型能动态决定流程和工具使用。

新手不要一开始就追求“全自动”。先让 Agent 做一个明确的小任务，然后逐步加工具、加验证、加边界。

## 2. 第一周学习路线

### Day 1：分清 Chatbot、Workflow 和 Agent

目标：不要把所有 AI 自动化都叫 Agent。

要弄懂：

- Chatbot：主要回答问题。
- Workflow：按预设步骤执行。
- Agent：能根据目标动态选择步骤和工具。
- RPA / 脚本：确定性强，但不擅长处理模糊输入。

产物：

- 写一页笔记：你最想让 Agent 解决的 3 个任务。
- 给每个任务标注：它更像聊天、workflow、脚本，还是 agent。

### Day 2：学会让 Agent 读资料

目标：让 Agent 从“凭记忆回答”变成“基于资料回答”。

练习：

- 选一篇公开文章。
- 让 Agent 提取核心观点。
- 让 Agent 标注不确定的地方。
- 让 Agent 生成一份可复用 Markdown 笔记。

产物：

- 一篇资料整理笔记。
- 一段“查资料再回答”的提示词。

推荐阅读：

- [第一个 Agent 实战任务：整理一篇公开网页并写成 Markdown 笔记](first-agent-web-research-task.md)
- [个人知识库搭建：让 Agent 维护一个会生长的 Wiki](personal-knowledge-base-agent-wiki.md)

### Day 3：学会工具调用

目标：理解 Agent 为什么需要工具。

工具可以分三类：

| 工具类型 | 用途 | 新手例子 |
|---|---|---|
| Data | 获取信息 | 搜索网页、读取 PDF、查表格 |
| Action | 执行动作 | 写文件、提交表单、生成 PPT |
| Orchestration | 组织流程 | 调用另一个 Agent、分派任务、合并结果 |

练习：

- 让 Agent 读取一个 Markdown 文件。
- 让 Agent 修改一个小文档。
- 让 Agent 自己检查修改是否成功。

产物：

- 一次“读取 -> 修改 -> 验证”的完整记录。

### Day 4：做一次自动化浏览

目标：让 Agent 从网页获取真实信息，而不是只靠搜索摘要。

练习：

- 选择一个公开网页。
- 让 Agent 打开页面、提取标题、正文、链接。
- 让 Agent 判断页面是否需要登录、是否有反爬或版权边界。
- 让 Agent 输出摘要和来源链接。

产物：

- 一篇网页资料卡片。
- 一段“自动化浏览任务说明”。

推荐阅读：

- [第一个 Agent 实战任务：整理一篇公开网页并写成 Markdown 笔记](first-agent-web-research-task.md)
- [Agent 自动化浏览与软件操作技术路线](agent-automation-browser.md)
- [Skills 专题导览](../skills/README.md)

### Day 5：学习上下文工程

目标：不要把所有内容都塞进提示词。

Agent 的上下文是有限资源。资料越多，不一定越好。真正重要的是把高信号内容放进去，把低价值内容留在外面。

练习：

- 给 Agent 一份长资料。
- 让它先做索引，再回答问题。
- 让它把有长期价值的回答写成笔记。

产物：

- 一个小型 `index.md`。
- 一篇 output 笔记。

### Day 6：给 Agent 加护栏

目标：让 Agent 做事前知道边界。

常见护栏：

- 不处理隐私数据。
- 不自动发布内容。
- 不自动付款或下单。
- 不绕过登录、验证码、付费墙。
- 涉及医疗、法律、金融，只做学习和信息整理，不做决策承诺。
- 每次外部行动前需要人工确认。

练习：

- 写一段“自动化浏览安全边界”。
- 写一段“文件修改前确认规则”。
- 写一段“发布内容前人工审核规则”。

产物：

- 一份 Agent 使用边界清单。

### Day 7：做第一个完整 Agent 小项目

推荐项目：把一篇公开文章变成一份学习卡片。

流程：

1. 选一篇公开文章。
2. 让 Agent 读取来源。
3. 让 Agent 摘要、提炼概念、列出行动建议。
4. 让 Agent 生成 Markdown 笔记。
5. 让 Agent 自查：有没有编造、有没有缺来源、有没有隐私风险。
6. 人工审核后保存。

产物：

- 一篇公开学习笔记。
- 一段可复用提示词。
- 一份自查清单。

## 3. 新手最容易踩的坑

### 坑 1：一开始就追求多 Agent

多 Agent 听起来强，但它会带来上下文分裂、协调成本、错误传递和调试困难。

更稳的路线是：

```text
单次提示词 -> 单 Agent + 工具 -> 单 Agent + 验证 -> 多 Agent
```

OpenAI 的实践建议也强调先最大化单 Agent 能力，只有当工具相似、指令复杂或职责冲突时，再考虑拆成多 Agent。

### 坑 2：只有生成，没有验证

Agent 最大的问题不是不会写，而是会自信地写错。

每个任务都应该有验证动作：

- 写文件后检查文件是否存在。
- 改网页后截图。
- 做 PPT 后检查页数和图片。
- 总结资料后保留来源。
- 涉及事实时回到原文确认。

### 坑 3：把提示词当全部

提示词重要，但 Agent 的稳定性更依赖：

- 工具是否清楚。
- 上下文是否干净。
- 输出格式是否固定。
- 验收标准是否明确。
- 失败时是否有回退路线。

### 坑 4：不给权限边界

Agent 一旦能访问浏览器、文件和账号，能力就变成风险。

新手默认规则：

- 可读公开资料。
- 可写本地草稿。
- 可建议发布。
- 不自动发布。
- 不自动付款。
- 不处理未脱敏隐私。

## 4. 推荐先读本仓库哪些内容

按顺序读：

1. [Agent 自动化浏览与软件操作技术路线](agent-automation-browser.md)
2. [个人知识库搭建：让 Agent 维护一个会生长的 Wiki](personal-knowledge-base-agent-wiki.md)
3. [高价值提示词模板精选](../prompts/high-value-prompts.md)
4. [Skills 专题导览](../skills/README.md)
5. [Enterprise Agent Harness 学习笔记](enterprise-agent-harness.md)

读完后的目标不是“懂很多名词”，而是能完成一个小闭环：

```text
明确任务 -> 找资料 -> 调工具 -> 写结果 -> 验证 -> 保存为笔记
```

## 5. 推荐外部一手资料

- [OpenAI Building agents](https://developers.openai.com/tracks/building-agents)：适合建立核心概念，理解 instructions、tools、guardrails、orchestration。
- [OpenAI A practical guide to building agents](https://cdn.openai.com/business-guides-and-resources/a-practical-guide-to-building-agents.pdf)：适合理解 use case、工具设计、guardrails 和从小到大的构建路径。
- [Anthropic Building effective agents](https://www.anthropic.com/engineering/building-effective-agents)：适合理解 workflow 和 agent 的区别，以及为什么简单、可组合的模式通常更可靠。
- [Anthropic Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)：适合理解为什么上下文是有限资源，不是越多越好。
- [Microsoft AI Agents for Beginners](https://github.com/microsoft/ai-agents-for-beginners)：适合参考系统课程结构和 lesson 式学习路径。

## 6. 入门判断标准

当你能做到下面这些事，就算真正入门了：

- 能说清 Agent 和普通聊天机器人的区别。
- 能设计一个明确任务，而不是只说“帮我自动化一下”。
- 能让 Agent 使用一个工具，并检查结果。
- 能写出权限边界。
- 能把一次有价值的回答保存成笔记。
- 能判断什么时候不该用 Agent。

这就是第一阶段的目标：不是炫技，而是让 Agent 稳定完成一件真实小事。
