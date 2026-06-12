# Codex OpenSchool

这里会持续分享我在使用 Codex、AI Agent、自动化工具和内容生产工作流时沉淀下来的公开材料。这个频道面向 AI Agent 新手，目标是帮助读者从“会问 AI”升级到“会让 Agent 做真实任务”。

第一次来，先读：[从这里开始：AI Agent 新手导读](START_HERE.md)。

如果只想先收藏三篇：

1. [AI Agent 新手入门路线图](notes/agent-beginner-learning-path.md)：建立 7 天学习路线。
2. [第一个 Agent 实战任务](notes/first-agent-web-research-task.md)：用公开网页跑通第一个低风险闭环。
3. [Agent 自主权限分级清单](notes/agent-autonomy-permission-ladder.md)：知道哪些事可以让 Agent 做，哪些必须停下来。

当前版本先做一个完整入口，分成七块：

- 新手路线：先给完全小白一条 7 天入门路径，避免一上来被框架和术语淹没。
- 实战练习：把路线、笔记和提示词拆成 7 个低风险小练习，读者可以直接照着做。
- 一手资源：把 OpenAI、Anthropic、Microsoft、MCP 和 GitHub 等官方资料整理成中文导读，告诉新手先读哪篇。
- 新鲜拆解：从 AIHot 和一手来源里提取近期 Agent 值得学的内容，不做热点搬运。
- Skills 分享：全量审计后按专题主推 34 个真实 skills，不再为凑数混入标准、框架或普通工具。
- 学习笔记：审计后只保留已经整理成公开 MD 的高价值笔记，优先服务 Agent 入门、术语表、概念辨析、第一任务、工具调用、浏览器调试、共享上下文、终端 Agent 可重复工作流、新工具 / skill 审计、权限分级、代码审查、skills 触发边界、Spec 模板、AI 可执行 PRD、Goal 指令、长任务环境规格、实战和避坑。
- 提示词模板：审计后只保留和 Codex / Agent / PPT / 技术内容强相关的高价值模板。

所有内容都按“可公开、可复用、可注明来源”的标准整理。本仓库不会上传本地私有 skill 源码、真实聊天记录、账号后台、客户材料、密钥、个人路径或未脱敏截图。

## 内容入口

### 新手路线

- 推荐入口：[从这里开始：AI Agent 新手导读](START_HERE.md)
- 推荐先读：[AI Agent 新手入门路线图](notes/agent-beginner-learning-path.md)
- 目标：7 天内完成“明确任务 -> 找资料 -> 调工具 -> 写结果 -> 验证 -> 保存为笔记”的第一个 Agent 小闭环。
- 边界：不追求全自动，不鼓励越权操作账号、付款、发布或处理未脱敏隐私。

### 实战练习

- 入口：[Agent 新手低风险练习室](labs/README.md)
- 内容：任务分类、公开网页整理、工具选型、权限分级、10 行 Spec、提交前审查和分享短帖。
- 标准：每个练习都有输入、步骤、产物和通过标准；不登录账号，不处理未脱敏材料。

### 一手资源导读

- 入口：[AI Agent 一手资源中文导读](resources/README.md)
- 内容：OpenAI、Anthropic、Microsoft、MCP、GitHub Spec Kit 等一手资料的阅读顺序、误读提醒和落地练习。
- 标准：只收官方或接近一手来源，不复制长篇原文，不把社交媒体摘要当成最终事实。

### Skills 分享

- 数量：34 个审计后保留的真实 skills。
- 入口：[skills/README.md](skills/README.md)
- 内容：自动化浏览、AI 资讯、内容入库、图文发布、PPT/文档、科研学术、视频脚本、代码审查、UI/前端、PRD/Agent 交接和部署验证。
- 标准：只收录具体可用的 skill 或明确外部项目，不把普通方法论、标准或重复能力凑成条目。

### AIHot 新鲜拆解

- 数量：1 期。
- 入口：[digests/README.md](digests/README.md)
- 内容：从近期 Agent 动态中提炼新手可学习的方法，例如权限分级、skills 触发边界、spec 驱动、AI 可执行 PRD 和环境工程。
- 标准：AIHot 只做发现入口；进入主推时优先补官方博客、GitHub、论文或文档链接。

### 学习笔记

- 数量：21 篇已成文、已脱敏、可直接阅读的公开笔记。
- 入口：[notes/README.md](notes/README.md)
- 内容：Agent 新手路线、新手术语表、核心概念 FAQ、第一个 Agent 实战任务、自动化浏览、Codex 浏览器开发者模式、共享上下文与知识编译、终端 Agent 可重复工作流、新工具 / skill 安装前审计、MCP vs CLI 工具调用选型、Agent 自主权限分级、Agent 代码审查工作流、Skill 触发边界、Agent 编程前 Spec 模板、AI 可执行 PRD、Codex Goal 指令、Agent 长任务环境规格、Enterprise Agent Harness 与环境工程、企业数据治理、PPT Master 工作流、个人知识库搭建。
- 标准：先有正文，再进入目录；没有正文的选题只留在本地待办。

### 提示词模板

- 数量：12 个可用入口，其中包含 8 个精选模板和 4 个已展开专题提示词。
- 入口：[prompts/README.md](prompts/README.md)
- 内容：Codex 自我进化、Codex Goal 指令、Agent 新手任务、Agent 审计、PPT 生产、技术内容创作、视觉提示词方法。
- 标准：只保留能直接拿去执行、能说明使用边界的提示词。

## 已展开资源导读

- [从这里开始：AI Agent 新手导读](START_HERE.md)
- [Agent 新手低风险练习室](labs/README.md)
- [AI Agent 一手资源中文导读](resources/README.md)

## 已展开笔记

- [AI Agent 新手入门路线图：从会聊天到会让 Agent 做事](notes/agent-beginner-learning-path.md)
- [AI Agent 新手术语表：从 Agent、Tool 到 Eval、Trace](notes/agent-glossary.md)
- [AI Agent 新手概念 FAQ：Agent、Workflow、Skill、MCP、CLI、RPA 到底有什么区别](notes/agent-concepts-faq.md)
- [第一个 Agent 实战任务：整理一篇公开网页并写成 Markdown 笔记](notes/first-agent-web-research-task.md)
- [Agent 自动化浏览与软件操作技术路线](notes/agent-automation-browser.md)
- [Codex 浏览器开发者模式：把网页调试变成可验证的 Agent 任务](notes/codex-browser-developer-mode.md)
- [Agent 共享上下文与知识编译：别把长期协作塞进聊天记录](notes/agent-shared-context-knowledge-compile.md)
- [终端 Agent 可重复工作流：从一次性提示到可审计任务卡](notes/agent-terminal-workflow-card.md)
- [Agent 新工具 / Skill 安装前审计清单：别被热榜带着装](notes/agent-tool-skill-audit-checklist.md)
- [Agent 工具调用选型：什么时候用 MCP，什么时候用 CLI](notes/agent-tooling-mcp-vs-cli.md)
- [Agent 自主权限分级清单：什么时候放手，什么时候必须停下来](notes/agent-autonomy-permission-ladder.md)
- [Agent 代码审查工作流：从 Auto-review 到 Bugbot](notes/agent-code-review-workflow.md)
- [Skill 描述怎么写才不误触发：description 是触发器，不是宣传语](notes/skill-description-trigger-boundaries.md)
- [Agent 编程前的 10 行 Spec 模板：先把需求写成可验收任务](notes/agent-coding-10-line-spec-template.md)
- [AI 可执行 PRD：把一句话需求写成 Agent 能实现的产品规格](notes/agent-executable-prd.md)
- [Codex Goal 指令怎么写：把模糊需求变成可执行目标](notes/codex-goal-writing-template.md)
- [Agent 长任务环境规格模板：先圈环境，再让 Agent 自主跑](notes/agent-long-task-environment-spec.md)
- [Enterprise Agent Harness 学习笔记](notes/enterprise-agent-harness.md)
- [企业 Agent 数据治理与自助分析落地手册](notes/enterprise-agent-data-governance.md)
- [Codex + PPT Master：从资料到高质量 PPT 的工作流](notes/codex-ppt-master-workflow.md)
- [个人知识库搭建：让 Agent 维护一个会生长的 Wiki](notes/personal-knowledge-base-agent-wiki.md)

## 已发布新鲜拆解

- [AIHot Agent 新鲜内容拆解：Auto-review、Skills、Spec、PRD、Goal 与环境工程](digests/2026-06-12-aihot-agent-trends.md)

## 已展开提示词

- [高价值提示词模板精选](prompts/high-value-prompts.md)
- [Agent 新手任务提示词包：7 天完成第一个可验证闭环](prompts/agent-beginner-task-prompts.md)
- [Codex 自我进化提示词](prompts/codex-self-evolution.md)
- [Codex Goal 指令生成提示词](prompts/codex-goal-command-template.md)
- [AI 教程视觉提示词方法：参考宝玉 skills](prompts/visual-prompts-baoyu-skills.md)

## 收录原则

1. 优先选择已经实际使用过、能解释清楚价值的内容。
2. 外部项目只做推荐、链接和使用建议，不复制源码或长篇原文。
3. 本地内容只发布脱敏后的摘要、方法和模板。
4. 涉及自动化浏览、账号登录、文件操作、发布内容等高风险场景时，必须注明边界和审核点。
5. 作者或来源可确认时尽量标注；无法确认时明确写“本地整理”或“来源未见明确作者字段”。

## 贡献与反馈

- 贡献规范：[CONTRIBUTING.md](CONTRIBUTING.md)
- 内容选题建议：使用 GitHub issue 模板里的“内容选题建议”。
- 链接、错别字或目录问题：使用 GitHub issue 模板里的“链接 / 错别字 / 小修复”。

所有建议都必须先脱敏。不接收账号、聊天记录、客户材料、密钥、本地路径、后台截图或未授权内容。

## 目录结构

```text
.
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── content-suggestion.yml
│   │   └── link-or-typo.yml
│   └── PULL_REQUEST_TEMPLATE.md
├── CONTRIBUTING.md
├── README.md
├── START_HERE.md
├── digests/
│   ├── README.md
│   └── 2026-06-12-aihot-agent-trends.md
├── labs/
│   └── README.md
├── resources/
│   └── README.md
├── skills/
│   └── README.md
├── notes/
│   ├── README.md
│   ├── agent-beginner-learning-path.md
│   ├── agent-glossary.md
│   ├── agent-concepts-faq.md
│   ├── first-agent-web-research-task.md
│   ├── agent-automation-browser.md
│   ├── codex-browser-developer-mode.md
│   ├── agent-shared-context-knowledge-compile.md
│   ├── agent-terminal-workflow-card.md
│   ├── agent-tool-skill-audit-checklist.md
│   ├── agent-tooling-mcp-vs-cli.md
│   ├── agent-autonomy-permission-ladder.md
│   ├── agent-code-review-workflow.md
│   ├── skill-description-trigger-boundaries.md
│   ├── agent-coding-10-line-spec-template.md
│   ├── agent-executable-prd.md
│   ├── codex-goal-writing-template.md
│   ├── agent-long-task-environment-spec.md
│   ├── codex-ppt-master-workflow.md
│   ├── enterprise-agent-data-governance.md
│   ├── enterprise-agent-harness.md
│   └── personal-knowledge-base-agent-wiki.md
├── prompts/
│   ├── README.md
│   ├── agent-beginner-task-prompts.md
│   ├── codex-goal-command-template.md
│   ├── codex-self-evolution.md
│   ├── high-value-prompts.md
│   └── visual-prompts-baoyu-skills.md
```
