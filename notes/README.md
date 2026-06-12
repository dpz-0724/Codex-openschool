# 学习笔记目录（审计版）

这一页只放已经整理成公开 MD、读者打开就能获得方法或框架的笔记。不再放只有标题、没有正文的占位内容。

## 收录标准

一篇学习笔记必须同时满足：

1. 仓库里有可直接阅读的 `.md` 正文。
2. 内容有明确问题意识、方法框架或操作流程，不只是标题清单。
3. 已经脱敏：不包含账号后台、真实聊天、客户材料、个人路径、密钥、非公开数据或采集细节。
4. 能说明适合谁读、读完能拿走什么。

## 已发布笔记

| # | 笔记 | 适合谁 | 价值判断 | 审计结论 |
|---:|---|---|---|---|
| 1 | [AI Agent 新手入门路线图：从会聊天到会让 Agent 做事](agent-beginner-learning-path.md) | 刚开始接触 Agent、还不知道从哪里学起的新手 | 给出 7 天学习路线、产物要求、工具调用、上下文和护栏入门 | 通过 |
| 2 | [AI Agent 新手术语表：从 Agent、Tool 到 Eval、Trace](agent-glossary.md) | 刚开始看 Agent 教程、容易被英文术语卡住的新手 | 把核心术语整理成可查表格，并串联到仓库内的路线、FAQ、实战和工程化笔记 | 通过 |
| 3 | [AI Agent 新手概念 FAQ：Agent、Workflow、Skill、MCP、CLI、RPA 到底有什么区别](agent-concepts-faq.md) | 被 Agent、workflow、skill、MCP、CLI、RPA 等术语绕晕的新手 | 用一篇 FAQ 建立任务类型判断框架，帮助读者先选对工具形态，再谈复杂架构 | 通过 |
| 4 | [第一个 Agent 实战任务：整理一篇公开网页并写成 Markdown 笔记](first-agent-web-research-task.md) | 已经理解基本概念、但还没让 Agent 做过完整任务的新手 | 用 30 分钟完成“公开资料 -> 结构化笔记 -> 自检 -> 入库”的第一个低风险闭环 | 通过 |
| 5 | [Agent 自动化浏览与软件操作技术路线](agent-automation-browser.md) | 想理解浏览器自动化、Computer Use、RPA 和 Agent 工具边界的人 | 有清晰技术分层，能帮助判断“该用 API、浏览器还是桌面控制” | 通过 |
| 6 | [Agent 工具调用选型：什么时候用 MCP，什么时候用 CLI](agent-tooling-mcp-vs-cli.md) | 已经知道 Agent 可以用工具、但不确定该接 MCP、CLI、API 还是浏览器自动化的新手 | 用本地决策经验和官方 MCP 文档整理出工具层选型表、判断流程和安全边界 | 通过 |
| 7 | [Agent 自主权限分级清单：什么时候放手，什么时候必须停下来](agent-autonomy-permission-ladder.md) | 已经开始让 Agent 调工具、改文件、浏览网页、发布草稿的新手 | 把 AIHot 发现的 Auto-review 思路转成 L0-L4 权限分级、工具前检查表和可复制提示词 | 通过 |
| 8 | [Agent 代码审查工作流：从 Auto-review 到 Bugbot](agent-code-review-workflow.md) | 已经开始让 Agent 写代码、改文件、提交 PR，但还没有稳定审查流程的新手 | 把 AIHot 里的 Cursor Auto-review 和 Bugbot 更新拆成动作前、提交前、PR 后三段式审查闭环 | 通过 |
| 9 | [Skill 描述怎么写才不误触发：description 是触发器，不是宣传语](skill-description-trigger-boundaries.md) | 想安装、创建或审核 Agent skills，但不确定怎么写触发边界的新手 | 把 AIHot 近期 Skills 动态和 Replit 官方资料拆成 description 写法、误触发诊断和发布前审计表 | 通过 |
| 10 | [Agent 编程前的 10 行 Spec 模板：先把需求写成可验收任务](agent-coding-10-line-spec-template.md) | 已经会让 Agent 写代码或改文件，但经常遇到“能跑却不是我要的”的新手 | 把 AIHot 里的 Spec 驱动开发趋势转成 10 行可复制模板、执行提示和验收审计表 | 通过 |
| 11 | [AI 可执行 PRD：把一句话需求写成 Agent 能实现的产品规格](agent-executable-prd.md) | 想让 AI 编程助手做页面、工具或产品，但经常返工的新手 | 把 AIHot 里的 `qiaomu-ai-prd` 和 Spec workflow 拆成可复制的 PRD 结构、约束层、状态表和验收剧本 | 通过 |
| 12 | [Agent 长任务环境规格模板：先圈环境，再让 Agent 自主跑](agent-long-task-environment-spec.md) | 想把任务交给 Agent 跑 30 分钟以上，但担心越权、跑偏或无证据的新手 | 把 EurekAgent 的环境工程和 OpenAI Ona 公告里的持久执行环境思路，拆成权限、产物、预算、人在回路和回放模板 | 通过 |
| 13 | [Enterprise Agent Harness 学习笔记](enterprise-agent-harness.md) | 想把 Agent 从 demo 做成可测试、可审计系统的人 | 有完整工程化框架，覆盖环境工程、golden case、trace、replay、guardrail、audit | 通过 |
| 14 | [企业 Agent 数据治理与自助分析落地手册](enterprise-agent-data-governance.md) | 做企业数据 Agent、BI Agent、自助分析的人 | 解释业务定义、语义层、canonical model、SOP 和验收题库如何组合 | 通过 |
| 15 | [Codex + PPT Master：从资料到高质量 PPT 的工作流](codex-ppt-master-workflow.md) | 想用 Codex 做课程、汇报、长文档转 PPT 的人 | 给出稳定流程和验收点，不只是“让 AI 做 PPT” | 通过 |
| 16 | [个人知识库搭建：让 Agent 维护一个会生长的 Wiki](personal-knowledge-base-agent-wiki.md) | 想用 Obsidian、Markdown、Codex 或 Agent 搭建长期知识库的人 | 从本地 notebook 的成熟方法中提炼出分层架构、入库门禁、查询回写和 lint 流程 | 通过 |

## 已下架内容

旧版候选主题摘要已移除。原因是它只是标题清单，很多条目没有对应正文，不应该作为公开分享内容发布。

后续新增笔记时，先写正文，再进目录；没有正文的选题只留在本地待办，不进入公开仓库。
