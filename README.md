# Codex- 笔记分享频道

这里用来分享和沉淀 AI Agent、自动化浏览、软件操作自动化等方向的技术笔记。

## 笔记目录

| 日期 | 标题 | 主题 |
|---|---|---|
| 2026-06-06 | [OpenClaw / Hermes 类 Agent 操作软件任务的技术方案调研报告](notes/agent-automation-browser.md) | Web Agent、CDP、DOM、UIA、RPA、Computer Use |

## 当前笔记摘要

这篇报告讨论 OpenClaw / Hermes 类 Agent 在操作网页和桌面软件时的技术路线，核心观点是不要把问题简化成“CDP 还是 DOM”或“坐标点击是否可行”。更可靠的工程路线是：

1. API 和结构化接口优先。
2. Web 系统优先使用 Playwright / CDP / DOM / Accessibility Tree。
3. Windows 桌面软件优先使用 UI Automation。
4. 自绘控件、远程桌面、Canvas 等场景再使用截图、OCR、视觉模型和坐标点击兜底。
5. 高风险动作必须保留人工确认、审计日志和状态验证。

## 目录结构

```text
.
├── README.md
└── notes/
    └── agent-automation-browser.md
```

## 更新方式

后续新增笔记建议统一放在 `notes/` 目录，并在本页追加目录索引。
