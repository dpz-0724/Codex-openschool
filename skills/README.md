# 第一期开源 Skills 推荐清单（审计版）

上一版把标准、框架、工具底座和具体 skills 混在一起，定义太宽。这一版重新收窄口径：只有满足下面条件的内容才进入主清单。

## 收录标准

一个条目必须同时满足：

1. 有明确的 `SKILL.md`、skill 目录，或已经以 agent skill 方式分发。
2. 能被 Agent 在实际任务里复用，不只是一个概念、标准、框架或普通库。
3. 能说清楚触发场景、输入、输出和风险边界。
4. 来源可以追溯；作者不明确时必须标注“本地整理”。
5. 不依赖真实账号、聊天记录、客户材料、密钥或本机私有路径才能讲清价值。

因此，Agent Skills Spec、OpenAI 文档、OpenClaw、Hermes Agent、Agents SDK、Manim、Marp、Remotion 这类内容不再放进 Skills 主清单。它们可以作为学习资料或工具底座，但不是这一页要推荐的 skill。

## 审计后主推清单

| # | Skill | 分类 | 做什么 | 作者 / 来源 | 为什么保留 | 风险与边界 |
|---:|---|---|---|---|---|---|
| 1 | [`web-access`](https://github.com/eze-is/web-access) | 自动化浏览 | 统一处理联网搜索、网页抓取、登录态网页和动态页面操作 | 一泽Eze | 真实公开 skill；本地已安装；覆盖浏览器自动化的高频需求 | 登录态网页、账号后台、批量抓取要先确认权限和站点规则 |
| 2 | `playwright` | 浏览器验证 | 用真实浏览器做页面导航、表单、截图、UI 验证和前端调试 | 本地 skill；底层是 [Microsoft Playwright](https://github.com/microsoft/playwright) | 和 `web-access` 不同，它更适合本地前端测试和可重复 UI 验证 | 与 `web-access` 有重叠，不再同时推荐 Playwright MCP、browser-use、Stagehand |
| 3 | [`aihot`](https://github.com/KKKKhazix/khazix-skills/tree/main/aihot) | AI 资讯 | 查询 AI HOT 中文 AI 资讯、日报、精选条目和近期动态 | GitHub：KKKKhazix；数据源：[AI HOT](https://aihot.virxact.com) | 是具体 skill，不是泛泛资讯网站；适合做 AI 日报和教学选题输入 | 摘要需回原文核验；不要把 AIHot 摘要当最终引用 |
| 4 | [`ppt-master`](https://github.com/hugohe3/ppt-master/tree/master/skills/ppt-master) | PPT 生成 | 把 PDF、DOCX、URL、Markdown 等资料转成 SVG 页面并导出 PPTX | GitHub：hugohe3 / PPT Master | 有明确 `skills/ppt-master/SKILL.md`；适合课程、汇报、长文档转 PPT | 示例必须用公开或虚构资料；不要上传客户材料和未授权论文全文 |
| 5 | [`baoyu-url-to-markdown`](https://github.com/JimLiu/baoyu-skills/tree/main/skills/baoyu-url-to-markdown) | 资料整理 | 把网页内容整理成干净 Markdown，便于后续总结、改写和入库 | JimLiu / 宝玉 | 输入输出明确，是内容工作流里很常用的基础 skill | 网页版权和引用边界要保留；不要绕过登录墙抓私有内容 |
| 6 | [`baoyu-markdown-to-html`](https://github.com/JimLiu/baoyu-skills/tree/main/skills/baoyu-markdown-to-html) | 内容发布 | 把 Markdown 文章转换成适合发布的 HTML 视觉稿 | JimLiu / 宝玉 | 适合教学文章、公众号排版和可视化交付 | 不复制第三方模板全文；发布前人工检查排版和链接 |
| 7 | [`baoyu-cover-image`](https://github.com/JimLiu/baoyu-skills/tree/main/skills/baoyu-cover-image) | 视觉生产 | 为文章、课程和教程生成封面图提示词或视觉方案 | JimLiu / 宝玉 | 解决“AI 教程怎么做封面”的真实需求 | 避免商标、肖像和不可授权风格；图中文字要人工复核 |
| 8 | [`baoyu-xhs-images`](https://github.com/JimLiu/baoyu-skills/tree/main/skills/baoyu-xhs-images) | 视觉生产 | 生成小红书风格图文卡片和多图内容方案 | JimLiu / 宝玉 | 适合把学习笔记转成可传播图片 | 不放真实账号数据、后台截图或个人隐私素材 |
| 9 | [`baoyu-slide-deck`](https://github.com/JimLiu/baoyu-skills/tree/main/skills/baoyu-slide-deck) | 视觉演示 | 生成演示文稿、路演或知识分享用的页面方案 | JimLiu / 宝玉 | 和 PPT Master 互补：一个偏视觉方案，一个偏完整 PPT 流水线 | 需要确认具体子 skill 的授权边界；不复制原始模板全文 |
| 10 | [`baoyu-youtube-transcript`](https://github.com/JimLiu/baoyu-skills/tree/main/skills/baoyu-youtube-transcript) | 视频资料 | 提取和整理 YouTube 字幕，作为学习和二次总结输入 | JimLiu / 宝玉 | 适合技术视频学习、课程拆解和资料整理 | 只做摘要和学习笔记，不搬运字幕全文 |
| 11 | `video-spec-builder` | 视频策划 | 把一个模糊视频想法追问成标准化 `video-spec.md` 和分镜表 | 本地整理 | 真实本地 skill；适合教学视频、产品演示和 AI 视频工作流 | 不公开私有素材、账号节奏和未发布项目脚本 |
| 12 | `tech-explainer-script-director` | 技术脚本 | 写和改中文技术讲解脚本，强调痛点、钩子、证据和可视化 | 本地整理 | 解决技术视频“像总结、不像视频”的问题，教学价值高 | 技术事实必须有来源；不夸大产品能力 |
| 13 | `motion-rich-tech-video-director` | 视频导演 | 把技术脚本拆成每个观点对应一个视觉变化，避免 PPT 式静态视频 | 本地整理 | 和 `video-spec-builder`、HyperFrames/Remotion 工作流互补 | 不承诺工具做不到的复杂镜头；输出前要做画面验收 |

## 候选但暂不主推

| 条目 | 处理 | 原因 |
|---|---|---|
| `playwright-interactive` | 暂不主推 | 和 `playwright`、`web-access` 重叠，除非专门讲持久浏览器调试 |
| `sora` | 暂不主推 | 是真实本地 skill，但依赖账号/API/任务队列，公开风险和时效性较高 |
| `ui-ux-pro-max` | 暂不主推 | 可能有用，但作者和公开来源不清晰，需要先做单独审计 |
| `html-skill-benchmark` | 暂不主推 | 偏评测方法，适合未来写成学习笔记，不适合第一期主推 skill |
| `codex-workflow-skill-miner` | 暂不主推 | 很有价值，但读取历史和记忆，隐私风险高，只适合讲思想，不适合直接公开推广 |

## 明确移除项

| 旧条目 | 移除原因 |
|---|---|
| Agent Skills Spec | 是标准，不是 skill |
| OpenAI Codex Agent Skills 文档 | 是文档，不是 skill |
| Anthropic Skills 仓库总入口 | 是样例库总入口，不该作为一个具体 skill 推荐 |
| Playwright MCP / browser-use / Stagehand | 和 `web-access`、`playwright` 重复，且更像工具或框架 |
| OpenClaw / Hermes Agent | 是 Agent 项目，不是具体 skill |
| OpenAI Agents SDK / Microsoft Agent Framework | 是框架，不是 skill |
| MarkItDown / PptxGenJS / Marp / Remotion / Manim | 是工具或库，不是 agent skill；可在学习笔记或工具底座里引用 |

## 下一步审计规则

后续新增 skill 时先补一行审计结论：`通过 / 候选 / 移除`，并说明来源、作者、适用场景、是否本地、是否会触碰隐私。没有通过审计的内容不再为了凑数量放进主清单。
