# Codex OpenSchool

这里会持续分享我在使用 Codex、AI Agent、自动化工具和内容生产工作流时沉淀下来的公开材料。这个频道面向 AI Agent 新手，目标是帮助读者从“会问 AI”升级到“会让 Agent 做真实任务”。

当前版本先做一个完整入口，分成四块：

- 新手路线：先给完全小白一条 7 天入门路径，避免一上来被框架和术语淹没。
- Skills 分享：全量审计后按专题主推 27 个真实 skills，不再为凑数混入标准、框架或普通工具。
- 学习笔记：审计后只保留已经整理成公开 MD 的高价值笔记，优先服务 Agent 入门、实战和避坑。
- 提示词模板：审计后只保留和 Codex / Agent / PPT / 技术内容强相关的高价值模板。

所有内容都按“可公开、可复用、可注明来源”的标准整理。本仓库不会上传本地私有 skill 源码、真实聊天记录、账号后台、客户材料、密钥、个人路径或未脱敏截图。

## 内容入口

### 新手路线

- 推荐先读：[AI Agent 新手入门路线图](notes/agent-beginner-learning-path.md)
- 目标：7 天内完成“明确任务 -> 找资料 -> 调工具 -> 写结果 -> 验证 -> 保存为笔记”的第一个 Agent 小闭环。
- 边界：不追求全自动，不鼓励越权操作账号、付款、发布或处理未脱敏隐私。

### Skills 分享

- 数量：27 个审计后保留的真实 skills。
- 入口：[skills/README.md](skills/README.md)
- 内容：自动化浏览、AI 资讯、内容入库、图文发布、PPT/文档、科研学术、视频脚本、UI/前端和部署验证。
- 标准：只收录具体可用的 skill 或明确外部项目，不把普通方法论、标准或重复能力凑成条目。

### 学习笔记

- 数量：6 篇已成文、已脱敏、可直接阅读的公开笔记。
- 入口：[notes/README.md](notes/README.md)
- 内容：Agent 新手路线、自动化浏览、Enterprise Agent Harness、企业数据治理、PPT Master 工作流、个人知识库搭建。
- 标准：先有正文，再进入目录；没有正文的选题只留在本地待办。

### 提示词模板

- 数量：10 个可用入口，其中包含 8 个精选模板和 2 个已展开专题提示词。
- 入口：[prompts/README.md](prompts/README.md)
- 内容：Codex 自我进化、Agent 审计、PPT 生产、技术内容创作、视觉提示词方法。
- 标准：只保留能直接拿去执行、能说明使用边界的提示词。

## 已展开笔记

- [AI Agent 新手入门路线图：从会聊天到会让 Agent 做事](notes/agent-beginner-learning-path.md)
- [Agent 自动化浏览与软件操作技术路线](notes/agent-automation-browser.md)
- [Enterprise Agent Harness 学习笔记](notes/enterprise-agent-harness.md)
- [企业 Agent 数据治理与自助分析落地手册](notes/enterprise-agent-data-governance.md)
- [Codex + PPT Master：从资料到高质量 PPT 的工作流](notes/codex-ppt-master-workflow.md)
- [个人知识库搭建：让 Agent 维护一个会生长的 Wiki](notes/personal-knowledge-base-agent-wiki.md)

## 已展开提示词

- [高价值提示词模板精选](prompts/high-value-prompts.md)
- [Codex 自我进化提示词](prompts/codex-self-evolution.md)
- [AI 教程视觉提示词方法：参考宝玉 skills](prompts/visual-prompts-baoyu-skills.md)

## 收录原则

1. 优先选择已经实际使用过、能解释清楚价值的内容。
2. 外部项目只做推荐、链接和使用建议，不复制源码或长篇原文。
3. 本地内容只发布脱敏后的摘要、方法和模板。
4. 涉及自动化浏览、账号登录、文件操作、发布内容等高风险场景时，必须注明边界和审核点。
5. 作者或来源可确认时尽量标注；无法确认时明确写“本地整理”或“来源未见明确作者字段”。

## 维护目标

这个仓库按长期频道维护，不是一次性资料夹。阶段目标和更新规则见：[Codex OpenSchool 频道运营手册](CHANNEL_STRATEGY.md)。

## 目录结构

```text
.
├── CHANNEL_STRATEGY.md
├── README.md
├── skills/
│   └── README.md
├── notes/
│   ├── README.md
│   ├── agent-beginner-learning-path.md
│   ├── agent-automation-browser.md
│   ├── codex-ppt-master-workflow.md
│   ├── enterprise-agent-data-governance.md
│   ├── enterprise-agent-harness.md
│   └── personal-knowledge-base-agent-wiki.md
└── prompts/
    ├── README.md
    ├── codex-self-evolution.md
    ├── high-value-prompts.md
    └── visual-prompts-baoyu-skills.md
```
