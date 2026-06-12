# Agent 编程环境：让 CLI Agent 真懂代码，而不是只会 grep

## 审计信息

- 整理时间：2026-06-12。
- 来源：AIHot 最近 7 天精选条目作为发现入口；正文以 GitHub Copilot CLI + Language Server 官方博客、Microsoft Language Server Protocol 文档为主要依据。
- 作者：本地整理；公开版由 Codex 脱敏改写。
- 适合读者：已经开始让 Codex、Copilot CLI、Claude Code 或其他 CLI Agent 改代码，但经常遇到误读 API、乱猜类型、漏掉引用的新手。
- 目标：帮助读者先把代码语义环境、依赖、测试和诊断准备好，再让 Agent 写代码。
- 隐私处理：不包含本地路径、私有仓库、客户代码、账号、密钥、未发布项目或真实业务 diff。

## 先说结论

当代码 Agent 改错文件、猜错函数签名、漏掉引用时，不一定是提示词不够长。很多时候是它只能看到文本，却拿不到代码语义。

更稳的 Agent 编程环境至少要有：

```text
语言服务器 / 依赖安装 / 类型检查 / lint / test / build / git diff
```

其中语言服务器（Language Server）负责给工具提供“跳转定义、查找引用、hover 文档、诊断、签名和类型”等能力。没有这些能力，Agent 就容易退化成全文搜索和猜测。

## 1. 只会 grep 的 Agent 会怎么失败

GitHub 在 Copilot CLI + Language Server 的文章里提到一个典型问题：没有 Language Server 时，CLI Agent 可能会去解压 JAR、grep `.class` 文件，或者在 `node_modules`、`site-packages` 里做文本搜索，试图拼出 API 形状。

这类方法有用，但不够可靠。

| Agent 的做法 | 看起来在努力 | 风险 |
|---|---|---|
| 在依赖目录里全文搜索 | 能找到一些名字相似的代码 | 分不清重载、泛型、类型别名 |
| 猜函数签名 | 速度快 | 容易传错参数或漏掉返回类型 |
| 只看当前文件 | 上下文少 | 漏掉跨文件引用和副作用 |
| 只跑字符串搜索 | 简单直接 | 不知道 symbol 的真实定义 |
| 没有 diagnostics | 生成后才发现编译错 | 返工成本高 |

所以，新手不要只问“提示词怎么写”，还要问：Agent 有没有得到像 IDE 一样的代码智能？

## 2. Language Server 到底给 Agent 什么

Microsoft 的 LSP 文档把 Language Server 的角色讲得很清楚：语言相关的智能能力放在独立 server 里，开发工具通过标准协议和它通信。这样不同编辑器或工具可以复用同一个语言服务。

对新手来说，不需要先读完整协议，先理解这些能力：

| 能力 | 对人的体验 | 对 Agent 的价值 |
|---|---|---|
| Go to definition | 跳到函数或类的定义 | 不用猜 API 来自哪里 |
| Find references | 找到所有引用 | 改名、改接口时少漏文件 |
| Hover documentation | 鼠标悬停看文档和类型 | 写调用代码时少猜参数 |
| Diagnostics | 实时错误和警告 | 改完前就能发现类型或语法问题 |
| Signature help | 函数参数提示 | 少传错参数顺序和类型 |
| Workspace symbols | 全项目 symbol 索引 | 大项目里更快定位模块 |

一句话：Language Server 让 Agent 从“搜文本”升级到“问代码结构”。

## 3. 新手先看 7 个环境信号

把一个项目交给 Agent 写代码前，先检查这 7 个信号：

| # | 信号 | 通过标准 | 不通过时的表现 |
|---:|---|---|---|
| 1 | 依赖安装 | `npm install`、`pip install`、`go mod download` 等已跑通 | Agent 看不到第三方类型 |
| 2 | 语言服务器 | 对应语言 server 可用 | Agent 只能 grep 和猜 |
| 3 | 类型检查 | 有 `typecheck`、`mypy`、`tsc`、`cargo check` 等命令 | 改完才发现类型错 |
| 4 | lint / format | 有明确格式和静态检查命令 | diff 里混入风格噪音 |
| 5 | 测试 | 有最小测试命令 | 只能靠“看起来对”判断 |
| 6 | 构建 / 运行 | 能本地启动或 build | UI / API 行为无法验证 |
| 7 | git 边界 | `git status` 干净或已说明现有改动 | Agent 容易覆盖别人的改动 |

这 7 项不一定都完美，但至少要知道缺哪一项。缺什么，就在任务 spec 里写清楚。

## 4. 常见语言的最低准备

下面不是安装手册，而是给新手的方向判断。具体命令要以项目 README、包管理器和官方文档为准。

| 语言 / 栈 | 常见语义能力 | 常见验证命令 |
|---|---|---|
| TypeScript / JavaScript | `typescript-language-server`、`tsserver`、ESLint | `npm test`、`npm run typecheck`、`npm run lint` |
| Python | Pyright、Pylance、ruff、mypy | `pytest`、`ruff check`、`mypy` |
| Java | JDT Language Server、Maven / Gradle | `mvn test`、`gradle test` |
| Go | `gopls`、`go vet` | `go test ./...`、`go vet ./...` |
| Rust | `rust-analyzer`、Cargo | `cargo check`、`cargo test`、`cargo clippy` |

如果项目 README 里没有这些命令，先让 Agent 帮你做“环境发现”，而不是直接改业务代码。

## 5. 代码 Agent 开工前的环境卡

你可以在每个项目根目录放一张公开、脱敏的环境卡，例如 `AGENT_ENV.md` 或 README 的一节：

```markdown
# Agent coding environment

## Language / stack

- TypeScript + React
- Node.js version:
- Package manager:

## Install

- npm install

## Code intelligence

- Language server:
- Typecheck:
- Lint:

## Verify

- npm run typecheck
- npm run lint
- npm test

## Safe boundaries

- Do not edit `.env`, secrets, deployment credentials, or production config.
- Do not run publish/deploy commands without confirmation.
- Before editing, run `git status --short`.
- Before finishing, summarize changed files and verification results.

## Known gaps

- No full e2e test yet.
- Some legacy files do not pass lint.
```

这张卡比把项目背景塞进聊天记录更稳定。下次换一个 Agent 或新线程，也能继续使用。

## 6. 给 Agent 的环境发现提示词

第一次接手一个代码项目时，不要直接说“帮我实现功能”。先让 Agent 做环境发现：

```text
请先审计这个项目的 Agent 编程环境，不要改业务代码。

目标：
判断这个项目是否已经具备让 CLI Agent 稳定改代码的基础环境。

请检查：
1. 主要语言、框架和包管理器。
2. 依赖安装命令。
3. 是否有 language server / 类型检查能力。
4. lint、format、test、build 命令。
5. 项目 README、package scripts、CI 配置里已声明的验证方式。
6. 当前 git status。
7. 哪些文件或动作必须禁止，例如 `.env`、密钥、生产配置、部署、发布、删除。

输出：
- 环境是否足够支持 Agent 改代码：可以 / 勉强可以 / 不建议。
- 推荐先补的 3 件事。
- 可复制的 AGENT_ENV.md 草稿。

限制：
- 不要安装依赖。
- 不要运行写入型命令。
- 不要读取密钥、cookie、浏览器 profile 或私有账号文件。
- 如果需要安装或修改配置，先列计划，等待确认。
```

这个提示词适合新手在真实开发任务前使用。

## 7. 什么时候不该先上 LSP

Language Server 很有价值，但也不是每个任务都要先折腾环境。

| 场景 | 建议 |
|---|---|
| 改一篇 README、整理文档链接 | 不必先配 LSP |
| 小脚本、一次性数据清洗 | 先用测试样例和 diff 验证 |
| 业务代码、多文件变更、重构 | 优先准备 LSP、类型检查和测试 |
| 大型 Java / TypeScript / Python 项目 | LSP 和依赖索引很重要 |
| 没有权限安装依赖 | 先只做只读分析，不要让 Agent 猜实现 |

关键不是“必须有 LSP 才能写代码”，而是任务越复杂，越不能只靠全文搜索。

## 8. 失败信号：看到这些就先停

如果 Agent 出现下面这些行为，先暂停，让它补环境信息：

- 开始在 `node_modules`、`site-packages`、`.m2` 里大量 grep，却说不清目标 symbol。
- 猜测第三方库函数签名，但没有来源。
- 大范围改接口，却没有查找引用。
- 说“应该能编译”，但没有 typecheck / build 证据。
- 修改很多文件，却没有测试或 diff 摘要。
- 想自动安装全局工具、改 shell profile、改系统路径。
- 想读取 `.env`、token、cookie、生产配置。

这些不是“Agent 很努力”的信号，而是环境不足或权限边界不清的信号。

## 9. 和本仓库其他笔记的关系

- 要先写需求边界：读 [Agent 编程前的 10 行 Spec 模板](agent-coding-10-line-spec-template.md)。
- 要沉淀终端工作流：读 [终端 Agent 可重复工作流](agent-terminal-workflow-card.md)。
- 要审查 diff：读 [Agent 代码审查工作流](agent-code-review-workflow.md)。
- 要判断工具层：读 [Agent 工具调用选型](agent-tooling-mcp-vs-cli.md)。
- 要审计新工具：读 [Agent 新工具 / Skill 安装前审计清单](agent-tool-skill-audit-checklist.md)。

## 10. 一句话结论

代码 Agent 的能力不只来自模型，也来自环境。给它 language server、依赖、类型检查、测试和清晰 git 边界，它才更像一个能查证的工程助手；不给这些，它就只能靠搜索、猜测和运气。

## 参考来源

- [GitHub Blog: Give GitHub Copilot CLI real code intelligence with language servers](https://github.blog/ai-and-ml/github-copilot/give-github-copilot-cli-real-code-intelligence-with-language-servers/)
- [Microsoft: What is the Language Server Protocol?](https://microsoft.github.io/language-server-protocol/overviews/lsp/overview/)
- [Language Server Protocol Specification](https://microsoft.github.io/language-server-protocol/specifications/lsp/3.17/specification/)
- [Awesome GitHub Copilot](https://awesome-copilot.github.com/)
