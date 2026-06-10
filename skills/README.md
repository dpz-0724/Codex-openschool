# 第一期开源 Skills 推荐清单

这份清单不是上传本机 skills 源码，而是整理 20 个值得学习、安装、借鉴或二次封装的 skills、工具和 skill 生态项目。筛选标准是：有明确用途、有公开来源或本地验证价值、适合教学复用，并且能说明风险边界。

## 20 个推荐项

| # | 分类 | 名称 | 做什么 | 作者 / 来源 | 来源状态 | 公开建议 |
|---:|---|---|---|---|---|---|
| 1 | Skill 标准 | [Agent Skills Spec](https://github.com/agentskills/agentskills) | 定义 agent skill 的目录、元数据、脚本、资源和渐进加载方式 | agentskills | 公开仓库，Apache-2.0 | 作为写 skill 的规范底座，不直接改写标准文档 |
| 2 | Skill 标准 | [OpenAI Codex Agent Skills](https://developers.openai.com/codex/skills) | 说明 Codex 中 skill 的作用、结构、插件关系和加载机制 | OpenAI | 官方文档 | 作为 Codex OpenSchool 的 skill 解释入口 |
| 3 | Skill 样例 | [Anthropic Skills](https://github.com/anthropics/skills) | 提供 Claude skills 的官方样例和文档、表格、演示等技能方向 | Anthropic | 公开仓库，部分内容为 source-available | 只链接和学习结构，注意不同子目录许可差异 |
| 4 | 自动化浏览 | [web-access](https://github.com/eze-is/web-access) | 统一处理联网搜索、网页抓取、登录态网页和动态页面自动化 | 一泽Eze | 外部公开项目，本地已安装验证 | 适合重点推荐；登录态页面必须先确认账号安全和网站规则 |
| 5 | 自动化浏览 | [Playwright](https://github.com/microsoft/playwright) | 用真实浏览器做测试、截图、表单、导航和页面状态验证 | Microsoft | 公开项目，Apache-2.0 | 适合作为浏览器自动化的底层工具 |
| 6 | 自动化浏览 | [Playwright MCP](https://github.com/microsoft/playwright-mcp) | 把 Playwright 能力暴露给 LLM 或 Agent 使用 | Microsoft | 公开项目，Apache-2.0 | 适合讲 MCP 化浏览器工具；不要暴露敏感页面 |
| 7 | 浏览器 Agent | [browser-use](https://github.com/browser-use/browser-use) | 让 AI agent 通过浏览器执行网站任务 | Browser Use | 公开项目，MIT | 适合和 Playwright 对比：更 agent 化，但风险也更高 |
| 8 | 浏览器 Agent | [Stagehand](https://github.com/browserbase/stagehand) | 用代码和自然语言混合方式做可维护的浏览器自动化 | Browserbase | 公开项目，MIT | 适合讲“稳定选择器 + 必要 AI 判断”的生产思路 |
| 9 | Agent 桌面 | [OpenClaw](https://github.com/openclaw/openclaw) | 面向个人工作流的 AI assistant，强调工具、workspace 和 skills | OpenClaw | 公开仓库 | 适合和本地自动化浏览笔记配套解读；不要搬部署配置 |
| 10 | Agent 桌面 | [Hermes Agent](https://github.com/NousResearch/hermes-agent) | 自进化 Agent，包含工具、浏览器、记忆和 skill 方向 | NousResearch | 公开仓库，MIT | 适合讲 Agent 自改进和浏览器后端，部署风险需单独说明 |
| 11 | Agent 框架 | [OpenAI Agents SDK Python](https://github.com/openai/openai-agents-python) | 构建 tools、handoff、guardrails、多 Agent 工作流 | OpenAI | 公开仓库，MIT | 适合把 skill 扩展成可编排 agent workflow |
| 12 | Agent 框架 | [Microsoft Agent Framework](https://github.com/microsoft/agent-framework) | 面向生产的多 Agent、工作流、观测和 human-in-the-loop | Microsoft | 公开仓库，MIT | 适合企业 Agent 工程化学习，避免一开始过度架构化 |
| 13 | AI 资讯 | `aihot` | 查询 AI HOT 中文 AI 资讯、日报、精选条目和近期动态 | 来源站点：[AI HOT](https://aihot.virxact.com)；本地 skill 未见明确作者字段 | 本地 skill，依赖公开资讯站点 | 适合做 AI 日报和选题输入；引用时保留来源 |
| 14 | 视觉/效率 | [baoyu-skills](https://github.com/JimLiu/baoyu-skills) | 宝玉整理的 AI Agent 日常效率、图片、Markdown/HTML 等 skills | JimLiu / 宝玉 | 公开仓库；需按单项确认授权 | 适合重点署名推荐；不复制全文，只引用和二次总结方法 |
| 15 | 文档处理 | [MarkItDown](https://github.com/microsoft/markitdown) | 把 Office、PDF、网页、图片等资料转换为 Markdown | Microsoft | 公开项目，MIT | 适合作为文档进入 Agent 工作流的公开底座 |
| 16 | PPT 工作流 | `ppt-master` | 把 PDF、DOCX、URL、Markdown 等资料组织成高质量 SVG/PPT 内容 | 本地自用 skill，未见明确外部作者字段 | 本地整理，不上传源码 | 适合推荐“资料到课件/汇报”的工作流；示例必须用虚构材料 |
| 17 | PPT 生成 | [PptxGenJS](https://github.com/gitbrent/PptxGenJS) | 用 JavaScript 生成可编辑 PowerPoint 文件 | gitbrent | 公开项目，MIT | 适合作为 Codex 生成 PPTX 的工程底座 |
| 18 | Markdown 演示 | [Marp CLI](https://github.com/marp-team/marp-cli) | 把 Markdown 转成 slides、PDF、HTML 或 PPTX | Marp Team | 公开项目，MIT | 适合技术课、短讲义和快速分享 |
| 19 | 程序化视频 | [Remotion](https://github.com/remotion-dev/remotion) | 用 React 生成程序化视频、字幕、动画和数据驱动画面 | Remotion | 公开项目，许可证需按商业使用场景确认 | 适合做技术解释视频底座；商业团队要单独核查许可 |
| 20 | 技术动画 | [Manim](https://github.com/ManimCommunity/manim) | 用代码生成数学、算法和技术解释动画 | Manim Community | 公开项目，MIT | 适合 AI 教程中的动态概念解释；学习曲线较高 |

## 分类建议

### 入门先看

先看 `Agent Skills Spec`、`OpenAI Codex Agent Skills`、`web-access` 和 `Playwright`。这四个能建立对 skill、浏览器自动化和 Agent 工具边界的基本理解。

### 做教学内容

优先看 `ppt-master`、`PptxGenJS`、`Marp CLI`、`Remotion`、`Manim` 和 `baoyu-skills`。它们分别覆盖课件、演示、视频和视觉素材。

### 做工程化 Agent

优先看 `OpenAI Agents SDK Python`、`Microsoft Agent Framework`、`Playwright MCP`、`Stagehand`、`OpenClaw` 和 `Hermes Agent`。这组更适合从“能跑 demo”走向“能控制、能编排、能审计”。

## 未收录原则

以下内容不放入第一期公开清单：含真实聊天数据、真实交易记录、账号后台、客户材料、服务器配置、本机密钥、私有运行时修复、未授权课程原文或无法确认公开边界的本地 skill。
