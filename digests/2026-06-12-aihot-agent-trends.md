# AIHot Agent 新鲜内容拆解：Auto-review、Skills、Spec、PRD 与环境工程

## 审计信息

- 检索时间：2026-06-12。
- 来源：AIHot 最近 7 天精选条目，关键词 `Agent`；进入主推的条目补充了一手链接或稳定公开入口。
- 作者：本地整理；公开版由 Codex 脱敏改写。
- 适合读者：想知道近期 Agent 方向有什么值得学，但不想被热点列表淹没的新手。
- 目标：从新鲜动态里提取能落地到学习路线、提示词、skill 和安全边界的内容。
- 隐私处理：不包含本地路径、账号、聊天记录、后台数据、私有 skill 源码、密钥或未发布项目。

## 本期结论

这期 AIHot 里 Agent 相关内容很多，但真正值得新手学习的不是“又出了一个工具”，而是 5 个方法主题：

1. Agent 自主性需要按风险分层，而不是只有“全自动 / 每步确认”两个档位。
2. Skills 正在变成团队约定和任务方法的载体，关键是触发边界要写清楚。
3. Spec 驱动开发在 Agent 编程里继续升温，因为它能把“先想清楚再实现”固定成流程。
4. AI 可执行 PRD 的价值是让 Agent 少猜：把核心循环、约束层、状态和验收剧本写清楚。
5. 长任务 Agent 的瓶颈不只是提示词，而是环境：权限、产物、预算、人工介入。

本期已经落地到仓库的动作：新增 [Agent 新手任务提示词包](../prompts/agent-beginner-task-prompts.md)，把“任务判断、工具选择、浏览边界、护栏、验收”做成可复制模板。

## 2026-06-12 追加：AIHot 最新条目审核表

这次只把有稳定公开入口、能讲清输入输出、对新手有实操价值的条目推进到主推清单。产品动态、只有社交线程或还没实测的工具先放观察。

| AIHot 条目 | 稳定入口 | 审核结论 | 新手能学什么 | 已落地位置 |
|---|---|---|---|---|
| 小互开源公众号自动排版技能组合 | [xiaohu-wechat-format](https://github.com/xiaohuailabs/xiaohu-wechat-format) | 进入 Skills 主推 | 内容发布 skill 不能只讲“一键发布”，必须把排版预览、封面、草稿箱推送和人工确认拆开 | [Skills 专题导览](../skills/README.md) |
| qiaomu-ai-prd | [joeseesun/qiaomu-ai-prd](https://github.com/joeseesun/qiaomu-ai-prd) | 已进入主推并沉淀成笔记 | PRD 要写给 Agent 执行和验收，不是只给人读 | [AI 可执行 PRD](../notes/agent-executable-prd.md) |
| Spec 驱动开发三个 Skills | [warpdotdev/common-skills](https://github.com/warpdotdev/common-skills) | 进入 Skills 主推 | 大任务先写 Product Spec / Tech Spec / Verify，减少 Agent 猜测空间 | [10 行 Spec 模板](../notes/agent-coding-10-line-spec-template.md) |
| Text-To-Lottie | [diffusionstudio/lottie](https://github.com/diffusionstudio/lottie) | 进入 Skills 主推 | 好 skill 不只生成文件，还要有本地预览、定位帧和验收闭环 | [Skills 专题导览](../skills/README.md) |
| baoyu-design 更新 | [JimLiu/baoyu-design](https://github.com/JimLiu/baoyu-design) | 进入 Skills 主推 | 设计类 skill 的关键是复用设计系统，同时保护 Figma 文件和品牌资产 | [Skills 专题导览](../skills/README.md) |
| Cursor Auto-review | [Cursor Blog](https://cursor.com/blog/agent-autonomy-auto-review) | 已沉淀成常青笔记 | Agent 自主权限要按风险分层，而不是二选一 | [权限分级清单](../notes/agent-autonomy-permission-ladder.md) |
| Replit Agent Skills | [Replit Blog](https://replit.com/blog/custom-skills) | 作为趋势来源，不单列 skill | Custom Instructions 是长期约定，Skills 是按任务加载的操作手册 | [Skill 触发边界](../notes/skill-description-trigger-boundaries.md) |
| GitHub Copilot CLI 自定义 Agent | [GitHub Blog](https://github.blog/ai-and-ml/github-copilot/from-one-off-prompts-to-workflows-how-to-use-custom-agents-in-github-copilot-cli) | 观察，不进入 Skills 主推 | 终端里的“一次性提示”正在变成可复用 workflow，但需等更多实测边界 | 后续做 CLI workflow 专题 |
| Codex 浏览器开发者模式 | [OpenAI Codex Chrome extension docs](https://developers.openai.com/codex/app/chrome-extension) | 观察，不进入 Skills 主推 | 浏览器调试能力应纳入自动化浏览路线，但产品能力不是单独 skill | 后续更新自动化浏览笔记 |

更新补充：2026-06-12 再看 AIHot 的 Skills 相关条目，`qiaomu-ai-prd`、Spec 驱动 Skills、Replit Agent Skills、`baoyu-design`、Text-To-Lottie、Teach skill 共同指向同一个问题：skill 的价值不在于名字多，而在于触发边界、输入输出和验收方式清楚。这个方向已扩展成常青教程：[Skill 描述怎么写才不误触发](../notes/skill-description-trigger-boundaries.md)。

再次更新：`qiaomu-ai-prd` 已核到公开 GitHub 仓库，并扩展成常青教程：[AI 可执行 PRD](../notes/agent-executable-prd.md)。这篇教程不搬运原始长提示词，而是提炼新手真正需要的结构：速读卡、核心循环、约束层、状态表、数据结构和验收剧本。

## 1. Cursor Auto-review：Agent 权限不是开关，是风险刻度

- AIHot 条目：Cursor 推出 Auto-review 机制。
- 一手来源：[Cursor Blog: Governing agent autonomy with Auto-review](https://cursor.com/blog/agent-autonomy-auto-review)
- 适合谁：已经开始让 Agent 调工具、改文件、跑命令的人。

### 提炼

Cursor 的思路不是让用户批准每一个动作，也不是把 Agent 完全放开，而是在工具调用前用一个分类器 Agent 判断动作风险。低风险动作放行，高风险动作会被拦下或转成更安全的路径。

这对新手最重要的一点是：权限管理不能只写成一句“遇到风险要小心”。你需要把动作按后果分层。

### 新手可以怎么学

把自己的 Agent 任务分成三档：

| 风险档 | 例子 | 处理方式 |
|---|---|---|
| 低风险 | 读取公开网页、整理 Markdown 草稿 | 可以自动执行，但要保留来源 |
| 中风险 | 修改本地文件、运行脚本、批量整理资料 | 执行前说明计划，执行后检查结果 |
| 高风险 | 发布内容、提交代码、付款、改账号、读密钥 | 必须人工确认或直接禁止 |

### 可落地内容

- 加到提示词里的字段：`必须人工确认的动作`。
- 加到 skill 里的字段：`什么时候不要使用这个 skill`。
- 加到实战笔记里的验收：工具调用前后都要有证据。

## 2. Replit Agent Skills：Skill 的核心是触发边界

- AIHot 条目：Replit Agent 新增自定义指令与技能功能。
- 一手来源：[Replit Blog: Customize Replit Agent with Skills & Custom Instructions](https://replit.com/blog/custom-skills)
- 适合谁：想把重复提示词沉淀成可复用工作流的人。

### 提炼

Replit 把 Custom Instructions 和 Skills 分开：前者是长期生效的团队约定，后者只在相关任务出现时加载。它特别强调 skill 的 description，因为 Agent 会先读 description 决定这个 skill 是否适用。

这和我们之前对 skills 的审计标准一致：skill 不是工具名，也不是泛泛方法论，而是一份“在什么场景用、什么场景不用”的任务说明书。

### 新手可以怎么学

写 skill 前先回答：

1. 这个任务是否会重复出现？
2. 输入和输出是否稳定？
3. 是否有明确通过标准？
4. 是否能写出“不适用场景”？
5. 是否和已有 skill 重复？

如果第 4 条写不出来，通常说明这个 skill 太泛。

### 可落地内容

- 已扩展成常青教程：[Skill 描述怎么写才不误触发](../notes/skill-description-trigger-boundaries.md)。
- 已和 [Codex 自我进化提示词](../prompts/codex-self-evolution.md) 呼应：重复、稳定、可验证才沉淀成 skill。

## 3. Spec 驱动开发 Skills：先写清不变量，再让 Agent 实现

- AIHot 条目：Spec 驱动开发的三个 Skills，覆盖 Spec -> Implement -> Verify 闭环。
- 稳定入口：[warpdotdev/common-skills](https://github.com/warpdotdev/common-skills)
- 适合谁：让 Agent 写代码时经常遇到“能跑但不符合预期”的人。

### 提炼

Spec 驱动开发的价值不是多写文档，而是先让用户故事、行为不变量、边界条件、实现约束和验证方式变成可审查材料。然后再让 Agent 实现，最后检查实现是否匹配 spec。

对新手来说，这比“直接让 Agent 写一个功能”稳定得多。

### 新手可以怎么学

把任何 AI 编程任务拆成三步：

```text
Product spec：用户看见什么、能做什么、边界是什么。
Tech spec：准备怎么实现、会改哪些模块、风险是什么。
Verify：实现是否真的匹配前两份 spec。
```

如果任务很小，也可以用简化版：

```text
目标：
用户故事：
必须满足的不变量：
不做什么：
验收命令：
```

### 可落地内容

- 已扩展成常青教程：[Agent 编程前的 10 行 Spec 模板](../notes/agent-coding-10-line-spec-template.md)。
- 当前提示词包的 Day 1 和 Day 7 已经采用同样思路：先定义完成标准，再执行。

## 3.5 qiaomu-ai-prd：PRD 的价值是让 Agent 少猜

- AIHot 条目：qiaomu-ai-prd：面向 AI 的 PRD 生成 Prompt。
- 稳定入口：[joeseesun/qiaomu-ai-prd](https://github.com/joeseesun/qiaomu-ai-prd)
- 适合谁：想把一句话产品想法交给 AI 编程助手实现，但又不想让 Agent 乱猜范围的人。

### 提炼

`qiaomu-ai-prd` 的价值不只是“生成一份 PRD”。它把一句话需求拆成 AI 速读卡、产品定位、用户场景、约束层、页面或模块结构、数据模型、优先级、性能指标和验收剧本。

对新手最重要的一点是：PRD 不是越长越好，而是要把 Agent 最容易猜错的地方写清楚。

### 新手可以怎么学

把 PRD 分成三层：

| 层级 | 作用 | 例子 |
|---|---|---|
| 硬约束 | 不能违反，违反就算失败 | 不读取私有数据；P0 必须跑通核心闭环 |
| 推荐默认 | 没有更好理由时按这个做 | Markdown 输出、移动优先、本地保存 |
| 发挥空间 | 允许 Agent 做得更好 | 空状态文案、动效、卡片视觉、快捷入口 |

然后再补一组验收剧本：正常路径、失败路径、隐私/权限边界。这样 Agent 才能实现后自检，而不是只说“已完成”。

### 可落地内容

- 已扩展成常青教程：[AI 可执行 PRD：把一句话需求写成 Agent 能实现的产品规格](../notes/agent-executable-prd.md)。
- 已把 `qiaomu-ai-prd` 放入 [Skills 专题导览](../skills/README.md)，标注为外部公开 skill，并注明不复制原始长提示词。

## 4. EurekAgent：长任务 Agent 的关键是环境工程

- AIHot 条目：EurekAgent 环境工程化实现自主科学发现。
- 论文入口：[Hugging Face Papers: EurekAgent](https://huggingface.co/papers/2606.13662)
- 适合谁：已经理解基础 Agent，想知道长期任务为什么容易失控的人。

### 提炼

EurekAgent 的启发不在于新手马上去做科研 Agent，而在于它把“环境工程”放到核心位置：权限、产物、预算、人工介入共同决定 Agent 能否可靠探索。

这和本仓库的入门原则一致：不要只优化提示词。真正能让 Agent 稳定做事的是任务环境。

### 新手可以怎么学

任何长任务都问四个问题：

| 维度 | 新手问题 |
|---|---|
| 权限 | Agent 能读写什么，哪些动作必须禁止？ |
| 产物 | 每一步是否留下文件、日志、来源或可复查结果？ |
| 预算 | 时间、次数、token、工具调用是否有上限？ |
| 人在回路 | 哪些地方必须让人确认或接管？ |

### 可落地内容

- 已扩展 [Enterprise Agent Harness 学习笔记](../notes/enterprise-agent-harness.md)，加入环境工程视角。
- 对新手练习来说，先在低风险 Markdown 任务里练“产物和自检”，不要直接做长期自主执行。

## 观察中：暂不主推的条目

| 条目 | 暂不主推原因 | 后续处理 |
|---|---|---|
| Perplexity Computer 集成 Deep Research | 主要是产品能力更新，新手可操作细节不足 | 等官方文档或实测路径更清晰 |
| Hermes Agent Desktop / Meoo CLI / WorkBuddy | 工具属性强，需要安装体验和边界验证 | 进入后续“工具实测”候选池 |
| MiMo Code V0.1.0 | 亮点在记忆、会话检查点和终端 Agent，但目前只看到 AIHot 摘要和公众号入口 | 先核 GitHub、安装门槛、隐私边界，再决定是否做“国产终端 Agent 实测” |
| Google DeepMind 多智能体安全研究资助 | 偏行业和研究资助，新手短期可操作性弱 | 观察是否出现可直接学习的多 Agent 安全案例 |
| GitHub Copilot CLI 自定义 Agent | 官方博客已发布，但本仓库还没有实测其 workflow 文件组织和权限边界 | 等做“终端 Agent 可重复工作流”专题时再展开 |
| OpenRouter 与 Cursor 集成 | 更像模型接入配置指南，不是独立 skill | 只有在做“编码 Agent 模型路由”专题时再收录 |

## 本期给仓库的更新建议

已经执行：

- 新增 [Agent 新手任务提示词包](../prompts/agent-beginner-task-prompts.md)，把“工具选择、浏览边界、护栏、验收”做成可复制模板。
- 新增 `digests/` 栏目，把 AIHot 新内容拆解和常青学习笔记分开。
- 已把 Cursor Auto-review 方向扩展成常青教程：[Agent 自主权限分级清单](../notes/agent-autonomy-permission-ladder.md)。
- 已把 Replit Skills / AIHot Skills 趋势扩展成常青教程：[Skill 描述怎么写才不误触发](../notes/skill-description-trigger-boundaries.md)。
- 已把 Spec 驱动开发方向扩展成常青教程：[Agent 编程前的 10 行 Spec 模板](../notes/agent-coding-10-line-spec-template.md)。
- 已把 `qiaomu-ai-prd` 拆成常青教程：[AI 可执行 PRD](../notes/agent-executable-prd.md)，并加入 Skills 导览。
- 已把 EurekAgent 的环境工程视角补进常青教程：[Enterprise Agent Harness 学习笔记](../notes/enterprise-agent-harness.md)。
- 已把“长任务环境规格”单独扩展成可复制模板：[Agent 长任务环境规格模板](../notes/agent-long-task-environment-spec.md)。
- 已给 4 篇适合拉新手入门的内容补传播素材：[Codex OpenSchool 传播素材包](../share/README.md)。
- 已把 Cursor Auto-review 和 Bugbot 更新合并沉淀成常青教程：[Agent 代码审查工作流](../notes/agent-code-review-workflow.md)。

下一步优先级：

1. 工具实测候选池：Hermes Agent Desktop、Meoo CLI、WorkBuddy，确认安装门槛、隐私边界和可替代性后再决定是否进入主推。
2. 继续观察 MiMo Code、GitHub Copilot CLI 自定义 Agent、Codex 浏览器开发者模式等终端型或产品型能力，只在能写出操作步骤、边界和验收时进入主推。
3. 实际发布传播素材后，记录平台链接和 Star 变化，保留能带来真实读者的表达。

## 参考来源

- [AIHot](https://aihot.virxact.com)
- [Cursor Blog: Governing agent autonomy with Auto-review](https://cursor.com/blog/agent-autonomy-auto-review)
- [Replit Blog: Customize Replit Agent with Skills & Custom Instructions](https://replit.com/blog/custom-skills)
- [warpdotdev/common-skills](https://github.com/warpdotdev/common-skills)
- [GitHub Spec Kit](https://github.com/github/spec-kit)
- [qiaomu-ai-prd](https://github.com/joeseesun/qiaomu-ai-prd)
- [Hugging Face Papers: EurekAgent](https://huggingface.co/papers/2606.13662)
- [OpenAI to acquire Ona](https://openai.com/index/openai-to-acquire-ona/)
