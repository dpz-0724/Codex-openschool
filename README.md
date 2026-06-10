# Codex OpenSchool

这里会持续分享我在使用 Codex、AI Agent、自动化工具和内容生产工作流时沉淀下来的公开材料。第一期先做一个完整入口，分成三块：

- Skills 分享：审计后主推 13 个真实 skills，不再为凑数混入标准、框架或普通工具。
- 学习笔记：审计后只保留已经整理成公开 MD 的高价值笔记。
- 提示词模板：审计后只保留和 Codex / Agent / PPT / 技术内容强相关的高价值模板。

所有内容都按“可公开、可复用、可注明来源”的标准整理。本仓库不会上传本地私有 skill 源码、真实聊天记录、账号后台、客户材料、密钥、个人路径或未脱敏截图。

## 第一期开源内容

| 方向 | 数量 | 入口 | 说明 |
|---|---:|---|---|
| Skills 分享 | 13 | [skills/README.md](skills/README.md) | 审计后只保留真实 skill：自动化浏览、AI 资讯、PPT、宝玉内容/视觉 skills、视频脚本和视频导演 |
| 学习笔记 | 4 | [notes/README.md](notes/README.md) | 只保留已成文、已脱敏、能直接阅读的公开笔记 |
| 提示词模板 | 8 + 2 | [prompts/README.md](prompts/README.md) | 8 个精选模板，加 2 个已展开专题提示词 |

## 已展开笔记

- [Agent 自动化浏览与软件操作技术路线](notes/agent-automation-browser.md)
- [Enterprise Agent Harness 学习笔记](notes/enterprise-agent-harness.md)
- [企业 Agent 数据治理与自助分析落地手册](notes/enterprise-agent-data-governance.md)
- [Codex + PPT Master：从资料到高质量 PPT 的工作流](notes/codex-ppt-master-workflow.md)

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

## 目录结构

```text
.
├── README.md
├── skills/
│   └── README.md
├── notes/
│   ├── README.md
│   ├── agent-automation-browser.md
│   ├── codex-ppt-master-workflow.md
│   ├── enterprise-agent-data-governance.md
│   ├── enterprise-agent-harness.md
└── prompts/
    ├── README.md
    ├── codex-self-evolution.md
    ├── high-value-prompts.md
    └── visual-prompts-baoyu-skills.md
```
