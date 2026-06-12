# 500 Stars 增长维护手册

## 当前状态

- 目标：GitHub Star / 收藏达到 500。
- 基线：2026-06-12，公开 GitHub API 显示 2 Stars。
- 当前阶段：0-50 Stars，重点不是追曝光，而是把仓库做得可信、清晰、可转发。

## 推荐仓库元数据

GitHub 仓库设置里建议使用：

```text
Description:
中文 AI Agent 新手入门频道：Codex、skills、提示词、自动化浏览、PPT 工作流与学习笔记

Topics:
ai-agent, agentic-ai, codex, skills, prompt-engineering, automation, mcp, knowledge-base, ai-tutorial, chinese
```

元数据验收标准：

- Description 直接说明“给谁、解决什么问题”。
- Topics 覆盖读者会搜索的词，而不是只写项目内部名称。
- 不放个人隐私、账号、组织内部项目或未公开品牌词。

## 内容飞轮

每次新增内容都要经过四步：

1. 从本地真实经验、公开一手资料或优秀外部项目中找选题。
2. 脱敏重写成新手能读懂的教程、清单或模板。
3. 进入 README、目录页和相关专题页，避免孤立文件。
4. 输出一段可传播摘要，方便发到小红书、公众号、X 或朋友圈。

仓库增长不靠“资料多”，靠这三个信号：

- 新手打开后知道先读哪一篇。
- 每篇内容都能解决一个具体问题。
- 有经验的读者能看出审计、取舍和边界。

## AIHot 新内容处理规则

AIHot 可以作为新选题雷达，但不能直接当成正文来源。每次看到很新的 Agent、skill、提示词或工具条目时，先按这个流程处理：

1. 判断它是否解决新手真实问题，而不是只有产品更新或标题新鲜。
2. 补官方博客、GitHub、论文、文档或作者主页等稳定公开入口。
3. 提炼成一个方法主题，例如权限分级、skill 触发边界、spec、PRD、环境规格或内容生产流程。
4. 只在能写出操作步骤、边界和验收标准时进入主推。
5. 进入仓库后优先沉淀成常青笔记、提示词或 skills 导览，再放传播素材。

不通过时只进入观察池，不写进 README 主入口。

## 每周维护节奏

### 周一：选题审计

- 从本地 notebook、skills 使用记录、AIHot 最近精选、公开一手资料里选 3 个候选。
- 只保留能写成正文的选题。
- 排除只有标题、没有方法、需要隐私材料支撑的内容。

### 周三：写作与脱敏

- 写 1 篇公开笔记或 1 组提示词模板。
- 删除本地路径、账号、聊天、后台截图、客户材料、密钥、未发布项目。
- 所有外部资料保留链接，不复制长篇原文。

### 周五：发布与传播

- 更新 README 和对应目录。
- 跑敏感扫描、链接检查、远程验证。
- 生成一段传播摘要和 3 个标题备选。

### 月末：清理与复盘

- 检查所有链接是否可打开。
- 下架占位内容、重复内容和低质量条目。
- 记录当前 Stars、增长来源和下月重点。

## 传播摘要模板

```text
这周更新了 Codex OpenSchool 的一篇新手教程：

主题：[一句话主题]

适合谁：
- [读者 1]
- [读者 2]

能解决什么：
- [具体问题 1]
- [具体问题 2]
- [具体问题 3]

我没有把它写成工具清单，而是补了：
- 判断标准
- 操作流程
- 常见坑
- 隐私和安全边界

仓库：[GitHub 链接]
```

## 标题候选模板

用于社交平台时，不要夸大承诺，标题要强调“新手能拿走什么”：

- AI Agent 新手最该先搞懂的一个问题：什么时候该用工具？
- 别一上来就追 MCP：Agent 工具调用的真实选型表
- 从会问 AI 到会让 Agent 做事：我整理了一条入门路线
- 给新手的 Codex + Skills 入门资料库，持续更新中
- 我把本地 Agent 工作流脱敏整理成了公开笔记

## 内容质量门禁

一篇内容发布前必须回答：

| 问题 | 不通过时怎么处理 |
|---|---|
| 读者是谁？ | 重新定义受众，不要写成泛泛教程 |
| 解决什么具体问题？ | 降低范围，只讲一个问题 |
| 是否有操作步骤或判断表？ | 补流程、表格或 checklist |
| 是否有边界和风险？ | 补隐私、安全、权限、版权说明 |
| 是否和已有内容重复？ | 合并或改成补充章节 |
| 是否能转发给新手？ | 改标题、摘要和开头 |

## 0-50 Stars 的重点任务

- 首页继续压缩，让读者 30 秒内知道仓库价值。
- 已补齐 16 篇高质量入门笔记；新增内容必须先判断是否能解决一个具体问题，避免为了数量扩张。
- 已新增“第一个 Agent 任务”实战案例：[整理一篇公开网页并写成 Markdown 笔记](notes/first-agent-web-research-task.md)。
- 为每篇笔记补一段“适合谁 / 读完能做什么”。
- 已建立基础 FAQ：[AI Agent 新手概念 FAQ](notes/agent-concepts-faq.md)。
- 已建立术语表专题页：[AI Agent 新手术语表](notes/agent-glossary.md)。
- 已补第一组配套提示词任务清单：[Agent 新手任务提示词包](prompts/agent-beginner-task-prompts.md)。
- 已新增 AIHot 新鲜拆解栏目：[AIHot Agent 新鲜内容拆解](digests/2026-06-12-aihot-agent-trends.md)。
- 已把 AIHot 里的 Cursor Auto-review 方向沉淀成常青教程：[Agent 自主权限分级清单](notes/agent-autonomy-permission-ladder.md)。
- 已把 AIHot 里的 Skills 趋势沉淀成常青教程：[Skill 描述怎么写才不误触发](notes/skill-description-trigger-boundaries.md)。
- 已把 AIHot 里的 Spec 驱动开发趋势沉淀成常青教程：[Agent 编程前的 10 行 Spec 模板](notes/agent-coding-10-line-spec-template.md)。
- 已把 AIHot 里的 `qiaomu-ai-prd` 拆成常青教程：[AI 可执行 PRD](notes/agent-executable-prd.md)。
- 已把 AIHot 里的 EurekAgent 环境工程视角补进：[Enterprise Agent Harness 学习笔记](notes/enterprise-agent-harness.md)。
- 已把 EurekAgent / Ona 相关的长任务环境工程视角拆成可复制模板：[Agent 长任务环境规格模板](notes/agent-long-task-environment-spec.md)。
- 已把 AIHot 里的 Cursor Auto-review / Bugbot 方向沉淀成常青教程：[Agent 代码审查工作流](notes/agent-code-review-workflow.md)。
- 已新增第一组传播素材：[Codex OpenSchool 传播素材包](share/README.md)，覆盖入门路线、第一个实战任务、长任务环境规格和代码审查工作流。

## 50-150 Stars 的重点任务

- 把最受欢迎的 3 篇内容扩展成系列。
- 每篇教程配一张可复制的任务清单或提示词。
- 开始接收 issue 反馈，但不接受未脱敏材料。
- 做一次外部优秀资源中文导读专题。

## 150-500 Stars 的重点任务

- 做完整学习地图。
- 增加贡献规范和选题提案模板。
- 每月发布更新日志。
- 对高频问题做专题页，而不是让 README 膨胀。

## 维护者原则

- 宁可少发，也不发空泛内容。
- 宁可写清楚“不适合什么”，也不做万能承诺。
- 宁可重写成本地公开方法，也不搬运私有材料。
- 宁可保守处理，也不冒隐私、版权和账号风险。
