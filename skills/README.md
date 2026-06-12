# Skills 专题导览（全量审计版）

这一页不是把本地所有 skill 名字搬出来，而是做一次公开分享审计：只推荐能解决具体问题、能说明输入输出、公开后不会暴露隐私的 skills。

本轮审计覆盖：

- 35 个本地自定义 skills。
- Codex 插件缓存中的官方/角色型 skills。
- 第一版已经收录的外部公开 skills。

结论：

- 公开主推：28 个。
- 其中本地已安装或本地整理：21 个。
- 外部公开且适合当前仓库定位：7 个。
- 不公开或待脱敏：本地账号、聊天记录、订单统计、项目专用、运行时密钥/路径、平台发布运营类 workflow。

## 收录标准

一个 skill 进入主推清单，必须满足：

1. 能解决一个明确问题，而不是只提供概念、标准或普通工具名。
2. 有稳定触发场景，能说清输入、输出和验收方式。
3. 不依赖真实账号、聊天记录、客户材料、密钥、私有路径或未发布项目才能讲清价值。
4. 作者或来源可以说明；来源不明确时标注“本地整理”。
5. 和现有条目不重复；重复能力只保留最容易解释、最常用的入口。

## 专题一：网页、资料抓取与自动化验证

| Skill | 来源 | 解决什么问题 | 为什么值得分享 | 公开边界 |
|---|---|---|---|---|
| [`web-access`](https://github.com/eze-is/web-access) | 一泽Eze；本地已安装 | 联网搜索、网页抓取、动态页面、登录态网页操作 | 适合做 Agent 自动化浏览的主入口，比单纯搜索更贴近真实网页任务 | 登录态、账号后台、批量抓取要确认权限和站点规则 |
| `playwright` | 本地整理；底层是 [Microsoft Playwright](https://github.com/microsoft/playwright) | 本地网页测试、表单操作、截图、UI 验证 | 适合前端验证和自动化测试，和 `web-access` 分工清楚 | 不绕过验证码、付费墙或平台限制 |
| `playwright-interactive` | 本地整理 | 持久浏览器 / Electron 交互调试 | 适合复杂 UI 需要反复观察、点击、截图的场景 | 只分享方法，不公开真实账号会话 |

## 专题二：AI 资讯、网页资料与内容入库

| Skill | 来源 | 解决什么问题 | 为什么值得分享 | 公开边界 |
|---|---|---|---|---|
| [`aihot`](https://github.com/KKKKhazix/khazix-skills/tree/main/aihot) | KKKKhazix；数据源 AI HOT；本地已安装 | 查询中文 AI 资讯、AI 日报、选题线索 | 适合做 AI 教学选题、日报和趋势输入 | 摘要要回原文核验，不能当最终引用 |
| [`baoyu-url-to-markdown`](https://github.com/JimLiu/baoyu-skills/tree/main/skills/baoyu-url-to-markdown) | JimLiu / 宝玉 | 把网页整理成干净 Markdown | 适合把网页资料转成知识库原料 | 尊重版权和登录墙边界 |
| [`baoyu-youtube-transcript`](https://github.com/JimLiu/baoyu-skills/tree/main/skills/baoyu-youtube-transcript) | JimLiu / 宝玉 | 提取和整理 YouTube 字幕 | 适合技术视频学习、课程拆解和二次笔记 | 不搬运字幕全文，只做学习摘要 |

## 专题三：内容发布、封面与图文卡片

| Skill | 来源 | 解决什么问题 | 为什么值得分享 | 公开边界 |
|---|---|---|---|---|
| [`baoyu-markdown-to-html`](https://github.com/JimLiu/baoyu-skills/tree/main/skills/baoyu-markdown-to-html) | JimLiu / 宝玉 | Markdown 转适合发布的 HTML | 适合公众号、长文和教程排版 | 不复制第三方模板全文 |
| [`baoyu-cover-image`](https://github.com/JimLiu/baoyu-skills/tree/main/skills/baoyu-cover-image) | JimLiu / 宝玉 | 文章、课程、教程封面方案 | 解决“好内容缺封面”的传播问题 | 商标、肖像、图中文字要人工复核 |
| [`baoyu-xhs-images`](https://github.com/JimLiu/baoyu-skills/tree/main/skills/baoyu-xhs-images) | JimLiu / 宝玉 | 小红书图文卡片和多图方案 | 适合把学习笔记转成可传播图片 | 不放真实账号数据或后台截图 |
| [`baoyu-slide-deck`](https://github.com/JimLiu/baoyu-skills/tree/main/skills/baoyu-slide-deck) | JimLiu / 宝玉 | 分享型 slides / deck 视觉方案 | 适合轻量知识分享和视觉提案 | 需要确认模板授权，不搬运原始素材 |
| `xiaohongshu-tech-content` | 本地整理 | 小红书技术内容标题、正文、封面、评论回复 | 已贴合 Codex、OpenClaw、AI Agent、skills 分享这类主题 | 不公开真实账号、后台数据、未发布运营策略 |

## 专题四：PPT、长 deck、PDF / Word 与打印交付

| Skill | 来源 | 解决什么问题 | 为什么值得分享 | 公开边界 |
|---|---|---|---|---|
| [`ppt-master`](https://github.com/hugohe3/ppt-master/tree/main/skills/ppt-master) | hugohe3 / PPT Master；本地已安装 | PDF、DOCX、URL、Markdown 到 PPTX | 适合课程、汇报、长文档转 PPT | 不上传客户材料、未授权论文全文或私有文档 |
| `longdeck` | 本地整理 | 30-50+ 页长 PPT 的一致性生产 | 解决长 deck 常见的设计漂移、断点续作和全局一致性问题 | 只分享流程，不公开具体商业项目素材 |
| `print-ready-handout-maker` | 本地整理 | 照片、截图、试卷、答案、笔记整理成可打印 PDF / Word | 对教学资料、讲义、家庭打印任务很实用 | 源文件涉及学生、证件、个人信息时必须脱敏 |
| `pdf` | 本地整理 | 创建、读取、渲染、审校 PDF | 强调渲染检查，不只抽文本 | 不上传私有 PDF 原文，只讲方法和验收 |
| `doc` | 本地整理 | 创建、编辑、视觉校验 DOCX | 适合 Word 格式交付和版式检查 | 不公开原始合同、证件、客户材料 |

## 专题五：科研写作、论文图表与学术汇报

| Skill | 来源 | 解决什么问题 | 为什么值得分享 | 公开边界 |
|---|---|---|---|---|
| `nature-polishing` | 本地整理；结合科研写作课笔记和 Academic Phrasebank 方法 | 科研英文润色、结构重写、中文学术稿转英文 | 不只改句子，先判断论文逻辑和 section job | 不上传未公开论文、审稿材料或敏感数据到公开模型 |
| `nature-figure` | 本地整理 | Nature / 高水平期刊图表生成与审计 | 从 figure claim、证据链、导出格式和审稿风险出发 | 不公开私有模板、原始数据和未发表图件 |
| `nature-data` | 本地整理 | Data Availability、FAIR 元数据、仓储与数据引用 | 很适合准备 Nature 系列投稿的数据可用性说明 | 政策可能变化，最终投稿前要查期刊最新要求 |
| `nature-paper2ppt` | 本地整理 | 科研论文转中文组会 / journal club PPTX | 能把论文主张、证据和图表组织成可讲的 deck | 不搬运论文全文；图表引用要保留来源 |

## 专题六：视频脚本、分镜与技术内容导演

| Skill | 来源 | 解决什么问题 | 为什么值得分享 | 公开边界 |
|---|---|---|---|---|
| `video-spec-builder` | 本地整理 | 把模糊视频想法追问成 `video-spec.md` 和分镜表 | 适合 AI 视频、产品演示、教学短片从 0 到可执行规格 | 不公开未发布脚本、账号节奏和素材路径 |
| `tech-explainer-script-director` | 本地整理 | 中文技术讲解脚本：痛点、钩子、证据、可视化 | 解决技术内容像说明书、不像视频的问题 | 技术事实要有来源，不夸大产品能力 |
| `motion-rich-tech-video-director` | 本地整理 | 把脚本拆成持续变化的画面和镜头节奏 | 适合避免 PPT 式静态视频，让观点对应视觉变化 | 不承诺工具做不到的镜头；最终要做画面验收 |

## 专题七：UI / 前端质量、上线与部署验证

| Skill | 来源 | 解决什么问题 | 为什么值得分享 | 公开边界 |
|---|---|---|---|---|
| `ui-ux-pro-max` | 本地整理；来源未见明确作者字段 | UI/UX 设计系统、配色、字体、交互、无障碍和质量检查 | 本地使用痕迹较多，适合做前端体验审计和设计决策 | 公开时只分享规则和方法，不复制内部数据表全集 |
| `html-skill-benchmark` | 本地整理 | 对多个 HTML / 前端 / UI skills 做同题评测 | 适合判断哪个 skill 真能做出好页面，而不是只看描述 | 不公开参赛者私有输出或未授权素材 |
| `public-site-deploy-health` | 本地整理 | 网站部署、线上线下一致性、公开路由健康检查 | 解决“到底上线了吗、线上是不是最新”的真实问题 | 不公开服务器 IP、路径、密钥、项目根目录 |
| `vercel-deploy` | 本地整理；平台为 Vercel | 快速部署预览站点并拿到链接 | 适合教程、Demo、临时预览交付 | 默认 preview；生产发布必须明确确认 |

## 专题八：产品规格、PRD 与 Agent 交接

| Skill | 来源 | 解决什么问题 | 为什么值得分享 | 公开边界 |
|---|---|---|---|---|
| [`qiaomu-ai-prd`](https://github.com/joeseesun/qiaomu-ai-prd) | 向阳乔木 / joeseesun；AIHot 发现；公开仓库已核 | 把一句话产品想法整理成 AI 编程助手能执行的 PRD | 适合新手学习“速读卡、约束层、优先级、状态、数据结构、验收剧本”这些 Agent 交接要素 | 推荐公开仓库和方法，不复制原始长提示词；涉及真实业务、账号、支付、用户数据时必须人工审核 |

## 候选但暂不公开主推

这些 workflows 有价值，但不适合直接放公开主清单。后续可以抽象成方法论笔记或脱敏版 skill。

| 类型 | 处理 | 原因 |
|---|---|---|
| 本地 Agent runtime 修复类 | 暂不公开 | 涉及本机配置、路径、端口、环境变量、API provider 和登录态，适合内部使用 |
| Codex 历史 / 记忆挖掘类 | 暂不公开 | 能发现可沉淀 workflow，但会读取会话历史和记忆摘要，隐私风险高 |
| 抖音 / 公众号生产总控类 | 待脱敏后再讲 | 工作流很有价值，但原 skill 绑定本地内容目录、账号节奏、发布状态和私有素材 |
| 小红书运营管理类 | 待脱敏后再讲 | 可公开的是内容写作方法，不应公开真实账号运营和后台数据 |
| 微信聊天、本地数据库、订单统计类 | 不公开 | 涉及聊天记录、联系人、订单或本地数据库，不能作为公开推荐 |
| 金融交易研究类 | 暂不公开 | 涉及高风险金融判断，公开时必须改成教育/研究边界，不提供投资建议 |
| 项目专用识别 / 运维类 | 暂不公开 | 和具体硬件、客户项目或内部流程绑定，泛化后再考虑 |
| 视频生成账号 / API 队列类 | 暂不公开 | 依赖账号、API、任务状态和平台能力，时效性和隐私风险较高 |
| 用户明确不放的个人娱乐类 skill | 不收录 | 不进入公开仓库 |

## 明确不再放进主清单的类型

| 类型 | 原因 |
|---|---|
| Agent Skills Spec / 官方文档 | 是标准或文档，不是具体 skill |
| OpenClaw / Hermes / Agents SDK / Microsoft Agent Framework | 是 Agent 项目或框架，不是单个可复用 skill |
| MarkItDown / PptxGenJS / Marp / Remotion / Manim | 是工具或库，可以在笔记里讲，不作为 skill 主推 |
| Playwright MCP / browser-use / Stagehand | 和 `web-access`、`playwright` 重复，暂不单独列主推 |
| 只有标题、没有输入输出和验收标准的想法 | 不具备公开分享价值 |

## 维护规则

后续新增 skill 时先做四步审计：

1. 它解决的真实问题是什么？
2. 它和现有主推 skill 是否重复？
3. 它的输入、输出、验收方式是否清楚？
4. 它公开后是否会泄露账号、聊天、路径、客户材料、密钥或未发布项目？

写 skill `description` 前，先读这篇触发边界教程：[Skill 描述怎么写才不误触发](../notes/skill-description-trigger-boundaries.md)。

通过后再进入主清单；没有通过的内容只留在本地候选，不为了数量进入公开仓库。
