# Codex OpenSchool 频道运营手册

## 目标

把这个仓库维护成中文 AI Agent 新手的高质量入门频道。

阶段性公开目标：

- GitHub Star / 收藏目标：500。
- 基线：2026-06-12，公开 GitHub API 显示 2 Stars。
- 核心读者：想从“会问 ChatGPT”升级到“会让 Agent 做真实任务”的新手、教师、内容创作者、产品/运营/开发学习者。

这个目标不能靠堆链接完成。仓库必须持续提供三类价值：

1. 新手能照着走的学习路线。
2. 真实可复用的 skills、提示词和工作流。
3. 经审计、脱敏、有判断的学习笔记。

## 频道定位

一句话定位：

> AI Agent 新手入门与实战工作流频道。

不做：

- AI 新闻搬运站。
- 大而全工具导航。
- 私有素材展示柜。
- 未验证项目的链接堆。
- 只追热点、不沉淀方法的短期内容。

要做：

- 把复杂 Agent 概念翻译成新手能执行的任务。
- 把本地真实使用过的工作流整理成公开方法。
- 把优质外部资料转成中文学习路径和实战卡片。
- 把“能不能用、什么时候用、风险在哪里”讲清楚。

## 内容栏目

### 1. 新手路线

目标：解决“我从哪里开始”的问题。

内容形态：

- Agent 入门路线图。
- 7 天 / 14 天学习计划。
- 第一个 Agent 任务清单。
- 常见误区：聊天机器人、工作流、Agent、自动化脚本的区别。

验收标准：

- 读者不需要先懂框架。
- 每一步都有产物。
- 不出现空泛鼓励。

### 2. Skills 分享

目标：解决“有什么能直接复用”的问题。

内容形态：

- 按场景分类的 skill 推荐。
- 本地用过的 skill 经验总结。
- 外部优秀 skill 的来源、作者、用法和风险边界。

验收标准：

- 每个 skill 都说明输入、输出、适用场景和不适用场景。
- 不把框架、标准、普通库包装成 skill。
- 不公开本地私有 skill 源码、路径、账号和数据。

### 3. 学习笔记

目标：解决“我应该理解哪些关键概念”的问题。

内容形态：

- Agent 自动化浏览。
- 上下文工程。
- 工具调用与权限边界。
- MCP vs CLI：什么时候标准化，什么时候保持轻量。
- Agent harness、eval、trace、replay、guardrail。
- 个人知识库与 Agent 维护。

验收标准：

- 必须有正文。
- 必须有问题意识。
- 必须讲清为什么重要、怎么实践、哪里有坑。

### 4. 提示词模板

目标：解决“我怎么让 Agent 稳定做事”的问题。

内容形态：

- 调研提示词。
- 审计提示词。
- 代码/文档交付提示词。
- PPT / 视频 / 内容生产提示词。
- 自我进化和复盘提示词。

验收标准：

- 能直接复制使用。
- 有输入变量和输出格式。
- 有边界条件，不鼓励越权、绕过限制或处理隐私数据。

### 5. 实战案例

目标：解决“学了之后能做什么”的问题。

内容形态：

- 让 Agent 自动整理网页资料。
- 让 Agent 生成并审计 PPT。
- 让 Agent 把学习笔记变成文章。
- 让 Agent 做一次浏览器自动化验证。
- 让 Agent 维护个人知识库。

验收标准：

- 只用公开或虚构数据。
- 有步骤、有截图或文字证据、有失败边界。
- 不把演示包装成生产可用承诺。

## 500 Star 路线

### 0-50 Stars：把仓库做得可信

重点：

- 首页一句话讲清定位。
- 新手路线图完整。
- Skills 清单有审计标准。
- 10 篇以内高质量笔记，不追数量。
- 所有链接可点，所有目录无空文件。

判断标准：

- 一个完全陌生的新手能在 5 分钟内知道先读哪篇。
- 一个有经验的读者能看出这里不是链接农场。

### 50-150 Stars：形成可传播内容

重点：

- 每周至少 1 篇实战型笔记。
- 每篇笔记都能转成小红书 / 公众号 / X 的传播摘要。
- 建立“本周推荐 skill / 本周 Agent 任务”栏目。
- 增加 3-5 个可复制实战任务。

判断标准：

- 每篇新增内容都有一个明确传播角度。
- 仓库不是只给开发者看，非开发读者也能上手。

### 150-300 Stars：形成系列感

重点：

- 做成完整的 Agent 入门系列。
- 增加“新手常见问题”和“术语表”。
- 对外部优质资源做中文导读，而不是只放链接。
- 每月做一次内容清理和链接巡检。

判断标准：

- 读者愿意把仓库发给“刚开始学 Agent 的朋友”。
- 搜索流量和社交转发有稳定入口。

### 300-500 Stars：做成中文入口

重点：

- 形成清晰学习地图。
- 有稳定更新记录。
- 有贡献规范和选题池。
- 开始吸收读者反馈，补齐薄弱章节。

判断标准：

- 仓库能回答“AI Agent 到底怎么入门、怎么实践、怎么避免踩坑”。
- Star 增长来自内容价值，而不是一次性宣传。

## 选题池

优先级 P0：

- AI Agent 新手入门路线图。
- 第一个 Agent 自动化浏览任务。
- Agent、Workflow、RPA、脚本、Chatbot 的区别。
- 什么是工具调用：Data / Action / Orchestration。
- MCP vs CLI 工具调用选型：不要为了协议牺牲任务闭环。
- 上下文工程入门：为什么不是提示词越长越好。
- Skills 怎么用：为什么它是 Agent 的操作手册。

优先级 P1：

- 用 Codex 整理一篇网页资料并写入知识库。
- 用 PPT Master 从资料生成一次课程 PPT。
- 用 Playwright 做一次本地页面验收。
- 用 Agent 做一次论文 / 技术文章精读。
- 用 Agent 把学习笔记改成小红书图文。

优先级 P2：

- 多 Agent 什么时候有必要。
- Agent eval、trace、replay 入门。
- 个人知识库如何和 Agent 配合。
- 自动化浏览的权限和安全边界。
- 如何判断一个 skill 是否值得安装。

## 外部参考原则

可以参考一手来源，但不能搬运原文：

- [OpenAI Building agents](https://developers.openai.com/tracks/building-agents)：用于定义 agent、tools、guardrails、orchestration。
- [OpenAI practical guide](https://cdn.openai.com/business-guides-and-resources/a-practical-guide-to-building-agents.pdf)：用于 agent use case、model choice、tool design、guardrails。
- [Anthropic Building effective agents](https://www.anthropic.com/engineering/building-effective-agents)：用于 workflow vs agent、simple composable patterns。
- [Anthropic context engineering](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)：用于解释上下文是有限资源，需要持续筛选。
- [Microsoft AI Agents for Beginners](https://github.com/microsoft/ai-agents-for-beginners)：用于参考课程化结构和 lesson 组织方式。
- [Model Context Protocol 官方文档](https://modelcontextprotocol.io/docs/getting-started/intro)：用于解释 MCP 的定位、工具规范、授权和安全边界。
- [Anthropic Code execution with MCP](https://www.anthropic.com/engineering/code-execution-with-mcp)：用于解释工具过多时的上下文成本和按需调用思路。

所有外部内容只做：

- 摘要。
- 中文导读。
- 实战转译。
- 链接和来源说明。

不做：

- 长篇复制。
- 未标注来源的改写。
- 把官方观点伪装成本地原创。

## 更新节奏

默认节奏：

- 每周新增或深度打磨 1 篇内容。
- 每月做 1 次链接巡检和敏感扫描。
- 每达到 50 个 Star 做一次路线复盘。

每次更新前必须问：

1. 这次更新是否让新手更容易开始？
2. 是否解决了一个具体问题？
3. 是否有脱敏风险？
4. 是否能被读者转发给别人？

如果答案不明确，先不发布。

## 隐私与安全红线

永远不上传：

- 本地绝对路径。
- 真实聊天记录。
- 账号后台截图或数据。
- 客户材料。
- 私有 skill 源码。
- API key、token、cookie、auth 文件。
- 未脱敏的截图、订单、联系人、数据库内容。

涉及自动化浏览、登录态、文件上传、发布内容、金融、医疗、法律或生产环境操作时，必须写明边界和人工确认点。

## 维护者工作流

每次维护按这个顺序：

1. 查当前仓库状态。
2. 明确本次更新的读者收益。
3. 搜索或读取来源。
4. 写成公开可读内容。
5. 做质量审计：是否空泛、是否重复、是否真的能用。
6. 做敏感扫描。
7. 提交并推送。
8. 远程读取确认 GitHub 已更新。
