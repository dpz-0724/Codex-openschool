# Codex OpenSchool

这里会持续分享我自己在使用 Codex、AI Agent 和自动化工具过程中的一些实践内容，主要分成三类：自用 Skills、学习笔记和好用提示词。

## Skills 分享

第一期先整理一批适合教学和复用的 skills，不直接上传本地源码，只做用途、来源和风险说明：

- [第一期开源 Skills 推荐清单](skills/README.md)

已覆盖方向：自动化浏览、AI 资讯、文档处理、PPT、UI/前端评测、视频内容生产和学术写作。

## 学习笔记

这里会沉淀一些学习和调研笔记，主题主要围绕 AI Agent、自动化、编程工具、产品实践和效率工作流。

| 日期 | 标题 | 主题 |
|---|---|---|
| 2026-06-06 | [OpenClaw / Hermes 类 Agent 操作软件任务的技术方案调研报告](notes/agent-automation-browser.md) | Web Agent、CDP、DOM、UIA、RPA、Computer Use |
| 2026-06-10 | [Enterprise Agent Harness 学习笔记](notes/enterprise-agent-harness.md) | Agent 工程化、测试、回放、审计、上线门禁 |

## 提示词分享

第一期先放两类可复用提示词：

- [提示词清单](prompts/README.md)
- [Codex 自我进化提示词](prompts/codex-self-evolution.md)
- [AI 教程视觉提示词方法：参考宝玉 skills](prompts/visual-prompts-baoyu-skills.md)

提示词会尽量附上使用场景和可替换变量，避免只是一段孤立文本。涉及个人记录、账号后台、客户材料、本机配置的内容不会原样公开。

## 目录结构

```text
.
├── README.md
├── skills/
│   └── README.md
├── notes/
│   ├── agent-automation-browser.md
│   └── enterprise-agent-harness.md
└── prompts/
    ├── README.md
    ├── codex-self-evolution.md
    └── visual-prompts-baoyu-skills.md
```

后续新增内容会按 `skills/`、`notes/`、`prompts/` 三个方向继续整理。
