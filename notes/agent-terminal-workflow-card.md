# 终端 Agent 可重复工作流：从一次性提示到可审计任务卡

## 审计信息

- 整理时间：2026-06-12。
- 来源：GitHub Copilot CLI 自定义 Agent 官方博客和文档；本地 Git / Claude Code 工作流笔记已脱敏改写。
- 作者：本地整理；公开版由 Codex 改写。
- 适合读者：已经会在终端里让 Agent 跑命令、改文件或整理资料，但经常反复解释同一类任务的新手。
- 目标：把“一次性长提示词”沉淀成可复用、可审查、可交给团队共享的工作流卡片。
- 隐私处理：不包含本地路径、账号、客户材料、聊天记录、仓库私密配置、密钥或未脱敏截图。

## 先说结论

终端 Agent 最值得沉淀的不是一句“帮我处理这个项目”，而是一张任务卡：

```text
角色 -> 触发场景 -> 输入 -> 允许工具 -> 禁止动作 -> 执行步骤 -> 输出格式 -> 验收证据 -> 停止条件
```

如果一个任务每周都做、输入输出稳定、能用命令验证结果，就不要每次重新写一大段提示词。把它整理成工作流卡片或 Agent profile，让 Agent 按同一套步骤执行，也让人能按同一套证据审查。

## 1. 为什么终端 Agent 容易跑乱

终端 Agent 能力很强，但新手常见问题也很固定：

| 问题 | 表现 | 后果 |
|---|---|---|
| 上下文每次重讲 | 每次都解释项目结构、命令、输出格式 | 结果不稳定，容易漏掉团队约定 |
| 工具边界太宽 | Agent 可以读写、运行、提交、推送一把梭 | 高风险动作不容易被提前拦住 |
| 输出没有合同 | 只说“完成了”，没有 diff、命令、文件列表 | 人很难审查真假 |
| 任务没有停止线 | 失败后继续尝试更多命令 | 时间和风险一起失控 |
| 经验没有沉淀 | 做完一次就留在聊天记录里 | 下次还要从零开始 |

可重复工作流的价值，就是把这些隐性约定写成显性规则。

## 2. 什么任务值得做成工作流

优先沉淀这类任务：

| 值得沉淀 | 原因 | 例子 |
|---|---|---|
| 每周或每个项目都会重复 | 重复成本高 | 发布前检查、文档链接检查、变更摘要 |
| 输入输出清楚 | 容易写验收标准 | PR 标题和 diff -> changelog 草稿 |
| 有稳定命令可验证 | 结果可复查 | `git diff`、测试命令、lint、链接检查 |
| 风险可以分层 | 能写清哪些动作必须确认 | 本地修改可以自动，远端 push 要确认 |
| 适合团队共享 | 规则比口头解释更可靠 | 代码审查、发布说明、事故复盘模板 |

暂时不要沉淀这类任务：

| 不适合 | 原因 |
|---|---|
| 一次性探索 | 写卡片成本高于收益 |
| 目标还很模糊 | Agent 只能猜，不如先写 spec |
| 需要真实账号、付款、发布、删除远端内容 | 必须单独做权限设计和人工确认 |
| 输入包含未脱敏隐私或客户材料 | 先脱敏，再决定是否公开或自动化 |
| 没有验收证据 | 做完也无法判断是否真的完成 |

## 3. 任务卡模板

可以先用这张 Markdown 模板，不必一上来就接复杂框架：

```markdown
# workflow-card

## name

一句话说明这张卡解决什么重复任务。

## use when

- 什么时候应该使用。
- 什么时候不应该使用。

## input

- 必填输入：
- 可选输入：
- 输入必须脱敏：

## allowed tools

- 可以读取：
- 可以运行：
- 可以写入：

## forbidden actions

- 不允许读取：
- 不允许修改：
- 不允许发布、推送、删除、付款或登录：

## steps

1. 先确认当前状态。
2. 再执行低风险读取和分析。
3. 只在需要时修改文件。
4. 修改后跑验证。
5. 输出证据和待人工确认项。

## output contract

- 修改了哪些文件：
- 运行了哪些命令：
- 关键结果：
- 风险和未完成项：

## evidence

- `git status`
- `git diff --check`
- 测试或检查命令输出摘要
- 关键来源链接

## stop conditions

- 需要账号、密钥、cookie、付款或发布。
- 需要删除远端内容、强推、重置历史。
- 测试连续失败且原因不明。
- 输入材料包含未脱敏隐私。

## review checklist

- 是否只做了卡片允许的动作？
- 是否留下可复查证据？
- 是否有未确认的高风险动作？
- 是否应该把本次经验回写到卡片？
```

这张卡的重点不是“写得像文档”，而是让 Agent 和人都知道边界在哪里。

## 4. GitHub 自定义 Agent 给我们的启发

GitHub 在 Copilot CLI 自定义 Agent 的介绍里，把一次性终端提示转成了可复用 workflow：用 Markdown 定义 Agent 的角色、工具、护栏和输出行为，再把 profile 放进仓库，让团队可以 review、version、share。

GitHub 文档里也给出了一种具体组织方式：仓库级 custom agent profile 可以放在 `.github/agents` 下，文件以 `.agent.md` 结尾；profile 由 Markdown 和 YAML frontmatter 组成，用来定义名称、描述、工具、可选 MCP server、模型和行为提示。文档还提醒，如果不声明 `tools`，Agent 可能获得所有可用工具，所以公开教程里更推荐最小工具集。

这对新手有两个启发：

1. 工作流应该进仓库，而不是只留在聊天记录里。
2. 工具权限要显式声明，而不是默认全给。

## 5. 一个最小示例：文档变更摘要 Agent

下面是一个可迁移结构，不是某个平台可直接复制运行的配置。不同平台字段可能不完全一样，具体工具名以平台文档为准；这里用语义化名称表达权限意图。

```markdown
---
name: docs-change-summarizer
description: Summarize documentation changes into a concise review note.
tools:
  - read
  - search
  - shell
---

You are a documentation change summarizer.

Use this when a user asks for a reviewable summary of Markdown or docs changes.

Allowed actions:
- Read repository files.
- Run read-only Git commands such as `git status`, `git diff --stat`, and `git diff`.
- Search text with `rg`.

Forbidden actions:
- Do not commit, push, delete files, rewrite history, publish content, or access secrets.
- Do not read `.env`, cookies, tokens, browser profiles, or private customer material.

Steps:
1. Run `git status --short` and identify changed docs.
2. Read the relevant diff.
3. Summarize user-facing changes, risk, and missing verification.
4. If the diff touches links, recommend a link check.

Output:
- Changed files.
- Reader-facing summary.
- Review risks.
- Commands reviewed.
- Follow-up checks.

Stop if:
- The task requires publishing, pushing, deleting, or reading secrets.
- The changed files include private data or unredacted personal information.
```

注意：这不是让 Agent 自动提交代码，而是让它稳定地生成一份可审查摘要。

## 6. 四个适合新手练习的工作流

### 6.1 Markdown 链接检查

输入：一个公开仓库或一个 Markdown 文件夹。

允许：

- 读取 `.md` 文件。
- 搜索相对链接。
- 检查内部链接是否存在。

禁止：

- 自动删除内容。
- 访问需要登录的后台。
- 把本地绝对路径公开到输出里。

验收证据：

- 检查命令。
- 找到的坏链接列表。
- 修复文件列表。

### 6.2 PR 变更摘要

输入：当前分支 diff。

允许：

- `git status`
- `git diff --stat`
- `git diff`

禁止：

- 自动 merge。
- 自动 push。
- 修改 review 之外的文件。

验收证据：

- 变更摘要。
- 风险点。
- 需要人工确认的测试缺口。

### 6.3 Changelog 草稿

输入：PR 标题、标签、diff 摘要。

允许：

- 读取提交和 diff。
- 生成 changelog 草稿。

禁止：

- 发布 release。
- 改版本号。
- 创建 tag。

验收证据：

- 面向用户的变更说明。
- breaking change 判断。
- 缺失信息清单。

### 6.4 公开资料整理

输入：公开网页链接或公开文档。

允许：

- 读取公开来源。
- 写 Markdown 摘要。
- 标注来源。

禁止：

- 绕过登录。
- 抓取私密页面。
- 大段复制原文。

验收证据：

- 来源链接。
- 摘要和行动建议。
- 隐私与版权检查。

## 7. Git 安全线：让 Agent 写文件前先过四步

本地 Git 工作流笔记里最值得公开分享的是这条线：

```text
看状态 -> 小范围修改 -> 看 diff -> 再提交
```

具体到 Agent 任务：

| 阶段 | 推荐动作 | 不要做 |
|---|---|---|
| 开工前 | 先看 `git status`，确认有哪些现有改动 | 不看状态就直接改 |
| 修改中 | 保持范围小，说明会改哪些文件 | 顺手重构无关内容 |
| 提交前 | 看 `git diff`，跑必要检查 | 只听 Agent 说“完成了” |
| 发布前 | 明确 commit、push、PR 的意图 | 静默推送、强推、重置历史 |

只要任务涉及删除、重置、强推、发布、付款、登录、读取密钥，就应该停下来让人确认。

## 8. 如何把一次任务回写成工作流

每次做完一个重复任务，问 6 个问题：

1. 这次真正的输入是什么？
2. 哪些命令或工具是必要的？
3. 哪些动作必须禁止？
4. 输出里哪些信息最方便人审查？
5. 哪个环节最容易失败？
6. 下次能不能用同一张卡完成 80%？

如果第 6 条答案是“能”，就把本次经验回写到 workflow card。这样仓库里的工作流会越来越像团队经验库，而不是提示词收藏夹。

## 9. 和本仓库其他笔记的关系

- 想先理解工具层：读 [Agent 工具调用选型：什么时候用 MCP，什么时候用 CLI](agent-tooling-mcp-vs-cli.md)。
- 想写长任务目标：读 [Codex Goal 指令怎么写](codex-goal-writing-template.md)。
- 想把长期协作沉淀成文件：读 [Agent 共享上下文与知识编译](agent-shared-context-knowledge-compile.md)。
- 想让 Agent 改代码后可审查：读 [Agent 代码审查工作流](agent-code-review-workflow.md)。

## 10. 一句话结论

终端 Agent 的成熟用法不是每次写更长提示词，而是把重复任务沉淀成可审计工作流：输入清楚、工具最小、禁止动作明确、输出有合同、验证有证据、风险会停下。

## 参考来源

- [GitHub Blog: From one-off prompts to workflows: How to use custom agents in GitHub Copilot CLI](https://github.blog/ai-and-ml/github-copilot/from-one-off-prompts-to-workflows-how-to-use-custom-agents-in-github-copilot-cli/)
- [GitHub Docs: Creating custom agents for Copilot coding agent](https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/create-custom-agents)
