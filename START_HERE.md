# 从这里开始：AI Agent 新手导读

这页是 Codex OpenSchool 的新手入口。仓库内容会继续增长，但第一次来不需要从头读完所有文件。

如果你只想先跑通一个低风险闭环，按这条路线走：

```text
先理解 Agent 是什么 -> 做第一个公开网页整理任务 -> 学会工具和权限边界 -> 再看 skills / PRD / 长任务
```

本仓库不教“全自动赚钱”“一键替代人类”或越权操作账号。这里关注的是：让 Agent 在明确边界内完成真实任务，并留下可检查的结果。

想直接做练习，可以打开：[Agent 新手低风险练习室](labs/README.md)。

想回到官方一手资料，可以打开：[AI Agent 一手资源中文导读](resources/README.md)。

## 30 秒判断：你现在该读哪篇

| 你现在的状态 | 先读 | 读完要做什么 |
|---|---|---|
| 完全不知道 Agent 和 ChatGPT 有什么区别 | [AI Agent 新手概念 FAQ](notes/agent-concepts-faq.md) | 分清 Chatbot、Workflow、Agent、Skill、MCP、CLI |
| 听过 Agent，但不知道怎么开始 | [AI Agent 新手入门路线图](notes/agent-beginner-learning-path.md) | 按 7 天路线完成第一个小闭环 |
| 想马上做一个安全练习 | [第一个 Agent 实战任务](notes/first-agent-web-research-task.md) | 把一篇公开网页整理成 Markdown 笔记 |
| 已经开始让 Agent 调工具 | [Agent 工具调用选型](notes/agent-tooling-mcp-vs-cli.md) | 判断什么时候用 MCP、CLI、API、浏览器 |
| 担心 Agent 越权或乱操作 | [Agent 自主权限分级清单](notes/agent-autonomy-permission-ladder.md) | 给任务标 L0-L4 风险级别 |
| 让 Agent 写代码但 diff 不好审 | [Agent 代码审查工作流](notes/agent-code-review-workflow.md) | 建立动作前、提交前、PR 后三段式审查 |
| 想把一句话任务交给 Codex 长时间执行 | [Codex Goal 指令写法](notes/codex-goal-writing-template.md) | 把模糊需求写成有验证、边界和暂停条件的 `/goal` |
| 想把一句话需求交给 Agent 实现 | [AI 可执行 PRD](notes/agent-executable-prd.md) | 写出约束层、状态表和验收剧本 |
| 想让 Agent 跑 30 分钟以上任务 | [Agent 长任务环境规格模板](notes/agent-long-task-environment-spec.md) | 先圈定环境、权限、预算和停止条件 |

## 30 分钟最小练习

不要从登录账号、自动发布、批量抓数据或修改真实项目开始。

最小练习只做一件事：

```text
选一篇公开网页 -> 让 Agent 阅读 -> 生成 Markdown 笔记 -> 检查来源和隐私 -> 保存到知识库
```

推荐顺序：

0. 打开 [Agent 新手低风险练习室](labs/README.md)，先选练习 1。
1. 先读 [第一个 Agent 实战任务](notes/first-agent-web-research-task.md)。
2. 复制里面的任务提示词。
3. 选择一个不需要登录、没有隐私数据的公开网页。
4. 让 Agent 输出结构化笔记。
5. 检查是否有来源链接、过度引用、隐私材料和未验证结论。

练习完成后，你应该得到一个可以放进知识库的 `.md` 文件，而不是一段聊天记录。

## 7 天入门路线

| 天数 | 主题 | 读什么 | 产物 |
|---:|---|---|---|
| Day 1 | 分清概念 | [概念 FAQ](notes/agent-concepts-faq.md) + [术语表](notes/agent-glossary.md) | 解释 Agent、Workflow、Skill、Tool 的区别 |
| Day 2 | 跑第一个任务 | [第一个 Agent 实战任务](notes/first-agent-web-research-task.md) | 一篇公开网页 Markdown 笔记 |
| Day 3 | 工具调用 | [MCP vs CLI](notes/agent-tooling-mcp-vs-cli.md) | 一张工具选型表 |
| Day 4 | 浏览器和软件操作 | [自动化浏览技术路线](notes/agent-automation-browser.md) | 判断任务适合 API、浏览器还是桌面控制 |
| Day 5 | 权限和护栏 | [自主权限分级清单](notes/agent-autonomy-permission-ladder.md) | 一份 L0-L4 风险分级 |
| Day 6 | 代码或产品交接 | [Goal 指令](notes/codex-goal-writing-template.md) + [10 行 Spec](notes/agent-coding-10-line-spec-template.md) + [AI 可执行 PRD](notes/agent-executable-prd.md) | 一个可验收、有边界的小需求规格 |
| Day 7 | 长任务和复盘 | [长任务环境规格模板](notes/agent-long-task-environment-spec.md) | 一份可交给 Agent 执行的环境规格 |

如果你只想先完成一个结果，Day 2 比 Day 1 更重要。先做，再回来看概念。

## 按目标选择路线

### 我想学会用 Agent 做资料整理

1. [第一个 Agent 实战任务](notes/first-agent-web-research-task.md)
2. [个人知识库搭建](notes/personal-knowledge-base-agent-wiki.md)
3. [Agent 新手任务提示词包](prompts/agent-beginner-task-prompts.md)

重点：先做公开资料，不碰账号后台、聊天记录、客户材料和私有文件。

### 我想学会让 Agent 写代码

1. [Codex Goal 指令怎么写](notes/codex-goal-writing-template.md)
2. [Agent 编程前的 10 行 Spec 模板](notes/agent-coding-10-line-spec-template.md)
3. [Agent 代码审查工作流](notes/agent-code-review-workflow.md)
4. [AI 可执行 PRD](notes/agent-executable-prd.md)

重点：先写清目标、不变量和验收命令，再让 Agent 改文件。

### 我想理解 skills 怎么用

1. [Skill 描述怎么写才不误触发](notes/skill-description-trigger-boundaries.md)
2. [Skills 分享目录](skills/README.md)
3. [Codex 自我进化提示词](prompts/codex-self-evolution.md)

重点：skill 不是工具名，也不是宣传语；它应该写清什么时候用、什么时候不用。

### 我想用 Agent 做内容生产

1. [Codex + PPT Master 工作流](notes/codex-ppt-master-workflow.md)
2. [AI 教程视觉提示词方法](prompts/visual-prompts-baoyu-skills.md)
3. [传播素材包](share/README.md)

重点：内容生产也要保留来源、边界和审核点，不要把未脱敏材料拿来展示。

### 我想做企业或长任务 Agent

1. [Enterprise Agent Harness 学习笔记](notes/enterprise-agent-harness.md)
2. [企业 Agent 数据治理与自助分析落地手册](notes/enterprise-agent-data-governance.md)
3. [Agent 长任务环境规格模板](notes/agent-long-task-environment-spec.md)

重点：企业 Agent 的核心不是“提示词更长”，而是数据定义、权限边界、日志、回放和验收题库。

## 新手最容易踩的坑

| 坑 | 为什么危险 | 先看 |
|---|---|---|
| 一上来就让 Agent 登录账号或自动发布 | 失败后可能影响真实外部系统 | [权限分级清单](notes/agent-autonomy-permission-ladder.md) |
| 只让 Agent “看着办” | 目标、边界、产物都不清楚 | [Goal 指令写法](notes/codex-goal-writing-template.md) |
| 把工具越多当成越强 | 工具越多，权限和错误面越大 | [MCP vs CLI](notes/agent-tooling-mcp-vs-cli.md) |
| 把 skill 写成泛泛能力介绍 | 容易误触发或重复触发 | [Skill 触发边界](notes/skill-description-trigger-boundaries.md) |
| 只看 Agent 总结，不看真实 diff 或产物 | 容易把“说完成了”当成完成 | [代码审查工作流](notes/agent-code-review-workflow.md) |
| 让长任务无限跑 | 没有预算、停止条件和回放证据 | [长任务环境规格模板](notes/agent-long-task-environment-spec.md) |

## 推荐阅读顺序

只读 3 篇：

1. [AI Agent 新手入门路线图](notes/agent-beginner-learning-path.md)
2. [第一个 Agent 实战任务](notes/first-agent-web-research-task.md)
3. [Agent 自主权限分级清单](notes/agent-autonomy-permission-ladder.md)

想系统读：

1. [概念 FAQ](notes/agent-concepts-faq.md)
2. [术语表](notes/agent-glossary.md)
3. [第一个 Agent 实战任务](notes/first-agent-web-research-task.md)
4. [MCP vs CLI](notes/agent-tooling-mcp-vs-cli.md)
5. [权限分级清单](notes/agent-autonomy-permission-ladder.md)
6. [Codex Goal 指令写法](notes/codex-goal-writing-template.md)
7. [10 行 Spec 模板](notes/agent-coding-10-line-spec-template.md)
8. [AI 可执行 PRD](notes/agent-executable-prd.md)
9. [长任务环境规格模板](notes/agent-long-task-environment-spec.md)

想直接找资源：

- [低风险练习室](labs/README.md)
- [一手资源中文导读](resources/README.md)
- [学习笔记目录](notes/README.md)
- [Skills 分享目录](skills/README.md)
- [提示词模板目录](prompts/README.md)
- [AIHot 新鲜拆解](digests/README.md)
- [传播素材包](share/README.md)

## 停止线

遇到这些情况，不要继续让 Agent 自主执行：

- 需要登录真实账号、发布内容、付款、下单、删除远端内容。
- 需要读取密钥、cookie、`.env`、浏览器登录态、后台数据。
- 输入里包含客户材料、聊天记录、订单、联系人、未脱敏截图。
- Agent 准备修改大量文件，但没有说明范围和回滚方式。
- 任务已经跑偏，但 Agent 只是在继续生成更多内容。

先停下来，补 spec、补权限边界、补验收标准，再继续。

## 这个仓库怎么持续更新

维护规则见：

- [频道运营手册](CHANNEL_STRATEGY.md)
- [500 Stars 增长维护手册](GROWTH_PLAYBOOK.md)

新内容进入仓库前必须先过三关：

1. 是否解决新手真实问题。
2. 是否有正文、流程、表格或模板。
3. 是否已经脱敏，并保留可核验来源。

宁可少发，也不发空泛内容。
