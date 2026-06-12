# Enterprise Agent Harness 学习笔记

主题：如何把一个会调用工具、会多步执行、会产生业务副作用的 Agent，变成可测试、可回放、可审计、可上线、可交付的系统。

适合对象：已经会写 Agent、Skill、CLI 或自动化脚本，但想理解企业端 Agent 工程化的人。

## 一句话总览

Agent 负责做事，Harness 负责让 Agent 做得可控、可测、可复盘、可上线、可交付。

企业端不只是关心 Agent 会不会回答问题，而是更关心：

- 它有没有做对？
- 出错能不能复现？
- 它调用了哪些工具？
- 有没有越权？
- 有没有泄露敏感数据或密钥？
- 高风险动作有没有人工审批？
- 改模型、改 prompt、改工具后有没有退化？
- 能不能给业务、合规、安全和交付团队看报告？

可以把 Enterprise Agent Harness 理解成：

```text
Enterprise Agent Harness =
  Runtime Control
  + Tool Governance
  + State / Memory / Event Log
  + Eval / Golden Cases
  + Trace / Replay
  + Guardrails / Human Approval
  + Sandbox / Permission
  + CI / Release Gates
  + Observability / Reports
  + Compliance / Audit
```

## 最小 Harness 是什么

不要一开始把 Harness 做得很重。最小版本只需要做到 6 件事：

1. 有一批固定业务样例。
2. 能自动运行 Agent / Skill / CLI。
3. 能记录输入、输出、工具调用和文件变化。
4. 能判断 PASS / FAIL。
5. 能保存失败样例，用于回放。
6. 能在上线前阻止明显退化。

没有 Harness 的说法：

```text
我试了一下，好像能跑。
```

有 Harness 的说法：

```text
我有 30 个 golden cases，每次修改后自动跑。
这次通过 29 个，失败 1 个。
失败原因已经沉淀成 regression case。
```

## Agent 生命周期

企业 Agent 的完整生命周期不是“用户问一句，模型答一句”，而是：

```text
1. 收到任务
2. 判断任务类型
3. 制定步骤
4. 调用工具
5. 读取 / 写入状态
6. 生成结果
7. 检查结果
8. 高风险动作等待审批
9. 记录全过程
10. 生成报告
11. 出错后回放
12. 下次上线前用样例重新测试
```

Harness 就是在这 12 步外面加控制系统。

## 环境工程：长任务 Agent 先设计环境，再设计聪明程度

AIHot 里提到的 EurekAgent 给这篇笔记补了一个重要视角：长任务 Agent 的瓶颈不只是 prompt、模型或 agent loop，而是环境。

这里的环境不是“部署在哪台机器”，而是 Agent 能看到什么、能改什么、必须留下什么、花费多少、什么时候让人介入。对新手来说，可以把环境工程理解成：

```text
Environment Engineering =
  Permission Engineering
  + Artifact Engineering
  + Budget Engineering
  + Human-in-the-Loop Engineering
```

这四件事应该在 Agent 开始长期任务前写清楚，而不是等它跑偏以后再补救。

### 1. Permission Engineering：权限工程

权限工程回答：

- Agent 能读哪些目录、网页、数据库或 API？
- Agent 能写哪些文件？
- 哪些工具只能 dry-run？
- 哪些动作必须人工确认？
- 评测环境是否和真实环境隔离？

新手最小写法：

```text
只读范围：
可写范围：
禁止动作：
必须确认：
隔离方式：
```

如果这几行写不出来，就不要让 Agent 做长时间自主执行。

### 2. Artifact Engineering：产物工程

产物工程回答：

- Agent 每一步留下什么文件或记录？
- 最终结果是不是可复查，而不是只存在聊天窗口里？
- 中间方案、失败原因、验证结果有没有保存？
- 能不能用 Git、diff、日志或报告还原过程？

一个能交付的 Agent 任务至少应该留下：

| 产物 | 作用 |
|---|---|
| `PLAN.md` 或任务计划 | 说明准备怎么做 |
| `TRACE.md` 或运行摘要 | 说明实际做了什么 |
| 输出文件 | 给用户真正使用的结果 |
| 验收记录 | 证明结果符合要求 |
| 失败样例 | 下次回归测试用 |

不要把“Agent 说它做完了”当成产物。文件、链接、截图、命令输出和可复查 diff 才是产物。

### 3. Budget Engineering：预算工程

预算工程回答：

- 这次最多跑多久？
- 最多调用多少次工具？
- 最多花多少 token 或 API 成本？
- 找不到结果时什么时候停止？
- 探索失败后是否允许换路径？

预算不是只为了省钱，更是为了防止 Agent 在错误方向上无限探索。

新手可以给每个长任务加一个预算块：

```text
最长时间：
最多工具调用：
最多网页/文件读取：
最大费用：
停止条件：
升级给人的条件：
```

### 4. Human-in-the-Loop Engineering：人在回路工程

人在回路不是“每一步都问我”，而是把人工介入点设计得低摩擦、可审计、能真正降低风险。

应该人工介入的情况：

- 要发布、提交、删除、付款、发消息。
- 要读取或处理未脱敏数据。
- 发现任务目标和现有事实冲突。
- 预算快耗尽但还没有证据。
- Agent 想扩大范围。
- 失败样例影响后续判断。

好的人工介入请求应该包含：

```text
当前进展：
遇到的问题：
可选方案：
每个方案的风险：
我建议的下一步：
需要你确认的动作：
```

这比一句“要继续吗？”更有价值。

## 环境规格模板

在让 Agent 跑一个超过 30 分钟、会改文件、会调用工具或会产生业务副作用的任务前，可以先写这张环境规格：

```text
任务目标：
只读范围：
可写范围：
禁止动作：
必须人工确认：
每步必须留下的产物：
最终交付物：
预算上限：
停止条件：
失败后如何回放：
```

这张表和前面的 Harness 模块是对应的：

| 环境规格 | 对应 Harness 模块 |
|---|---|
| 只读范围 / 可写范围 / 禁止动作 | Sandbox / Permission, Tool Governance |
| 必须人工确认 | Guardrails / Human Approval |
| 每步必须留下的产物 | State / Memory / Event Log, Trace / Replay |
| 最终交付物 | Observability / Reports |
| 预算上限 / 停止条件 | Runtime Control, Release Gates |
| 失败后如何回放 | Eval / Golden Cases, Trace / Replay |

如果你只记住一句话，就是：

> 长任务 Agent 不要先问“模型够不够聪明”，先问“环境有没有把正确行为变容易，把危险行为变困难”。

## 十大模块

### 1. Runtime Control：运行控制

Runtime Control 管 Agent 这次任务到底怎么跑。

它要回答：

- 这次运行的 `run_id` 是什么？
- 最多允许执行几步？
- 超时怎么办？
- 失败能不能重试？
- 重试会不会重复创建数据？
- 中断后能不能恢复？
- 能不能取消？
- 不同任务用哪个模型？

一句话记忆：

> Runtime Control 管“Agent 怎么跑”。

### 2. Tool Governance：工具治理

Tool Governance 管 Agent 可以调用哪些工具、怎么调用、调用前要不要审批。

Agent 真正危险的地方不是会说话，而是会调用工具。一个好的工具设计至少应该有：

- `input_schema`：防止模型乱传参数。
- `output_schema`：让工具返回结构化结果。
- `risk_level`：区分低风险、中风险、高风险动作。
- `requires_approval`：是否必须人工确认。
- `permissions`：权限边界。
- `idempotency_key`：防止重复创建。

一句话记忆：

> Tool Governance 管“Agent 能动哪些按钮”。

### 3. State / Memory / Event Log：状态、记忆、事件日志

很多 Agent 项目失败，是因为把业务状态只放在上下文窗口里。

企业业务状态应该放在数据库、文件、事件日志或状态表里，而不是只靠模型记忆。

- State：当前业务事实。
- Memory：长期可复用信息。
- Event Log：发生过什么。

一句话记忆：

> State / Memory / Event Log 管“Agent 依据什么事实做事，以及做过什么”。

### 4. Eval / Golden Cases：评测和黄金样例

Eval 是 Agent 的考试系统。Golden Case 是固定输入 + 期望结果。

Eval 不应该只看“回复好不好听”，而要检查业务结果：

- 分类是否正确？
- 字段是否抽取正确？
- 是否去重？
- 是否创建了正确状态？
- 是否拦截高风险动作？
- 是否更新报告？

一句话记忆：

> Eval / Golden Cases 管“怎么证明 Agent 真的做对了”。

### 5. Trace / Replay：轨迹和回放

Trace 是 Agent 的黑匣子。一次 trace 应该记录：

- 输入是什么
- 调用了哪个 agent / skill
- 调用了哪些工具
- 每个工具参数是什么
- 每个工具返回什么
- 状态怎么变化
- 有没有错误
- 有没有审批
- 最终输出是什么
- 生成了哪些 artifacts

Replay 是用同样输入、同样 fixture、同样工具返回、同样状态快照重新跑一遍。

一句话记忆：

> Trace / Replay 管“出错以后能不能查清楚、重现、修好”。

### 6. Guardrails / Human Approval：护栏和人工审批

不要把 Guardrail 理解成 prompt 里写一句“请不要做坏事”。这不够。

真正的 Guardrail 应该能：

- 拦截
- 拒绝
- 暂停
- 要求审批
- 记录原因

高风险动作示例：

- 真实发布内容
- 自动回复用户
- 删除数据
- 发送正式报价或合同
- 修改预算
- 修改主数据

一句话记忆：

> Guardrails / Human Approval 管“哪些事不能做，哪些事必须人批”。

### 7. Sandbox / Permission：沙箱和权限

测试和运行要尽量隔离。

常见做法：

- 测试时只用临时目录。
- 测试时只用 fake database。
- 测试时不碰真实账号。
- 工具分只读 / 写入 / 高风险写入。
- 真实发布必须审批。
- shell 命令白名单。
- 环境变量和密钥不进 prompt。
- trace 里自动脱敏。

一句话记忆：

> Sandbox / Permission 管“Agent 被关在哪个安全范围内”。

### 8. CI / Release Gates：自动测试和上线门禁

CI 是每次改动自动测试。Release Gate 是不通过就不许上线。

上线前应该自动跑：

- 单元测试
- integration test
- golden cases
- smoke test
- schema check
- secrets scan
- report 生成
- release gate 判断

一句话记忆：

> CI / Release Gates 管“这次改动能不能放出去”。

### 9. Observability / Reports：可观测性和报告

企业不会满足于“Agent 今天跑了”。企业要看：

- 今天跑了多少任务？
- 成功多少？
- 失败多少？
- 失败集中在哪？
- 平均耗时多少？
- 调用了哪些工具？
- 有没有高风险动作？
- 有没有未审批动作？
- 有没有敏感信息泄露？

Observability 通常包括：

- Logs
- Metrics
- Traces
- Artifacts
- Reports

一句话记忆：

> Observability / Reports 管“系统跑得怎么样，别人能不能看懂”。

### 10. Compliance / Audit：合规和审计

Compliance / Audit 是责任系统。

企业最终会问：

- 谁让 Agent 做的？
- Agent 做了什么？
- 什么时候做的？
- 用的哪个版本？
- 依据是什么？
- 有没有审批记录？
- 有没有违反权限？
- 有没有泄露密钥？

一句话记忆：

> Compliance / Audit 管“出了事以后能不能追责，平时能不能证明你合规”。

## 常见边界

### Provider 不是 Harness

Provider 是模型从哪里来，比如 OpenAI、Anthropic、Google、本地模型。

Harness 是怎么测试、控制、回放、上线、审计。

### Runtime 不是 Harness

Runtime 是 Agent 怎么执行。Harness 是对运行结果做测试、追踪、回放、门禁和报告。

### MCP 不是 Harness

MCP 解决“怎么标准化接工具”。Harness 解决：

- 这个工具该不该被调用？
- 调用前要不要审批？
- 工具返回怎么打分？
- 失败怎么回放？
- 上线前怎么测？
- 日志怎么审计？

### RAG 不是 Harness

RAG 解决“知道什么”。Agent 解决“做什么”。Harness 解决“做得对不对、可不可控”。

## 关键词速览

| 关键词 | 含义 |
|---|---|
| Golden Case | 固定输入 + 期望输出 |
| Regression Test | 修过的问题变成永久测试 |
| Trace | 一次 Agent run 的完整轨迹 |
| Replay | 用同样输入和 fixture 重跑失败任务 |
| Guardrail | 能拦截、拒绝、暂停或要求审批的控制机制 |
| Human-in-the-Loop | 高风险动作由人类 approve / edit / reject |
| Tool Schema | 工具参数和返回值的数据合同 |
| Idempotency | 同一操作重复执行不会产生重复或错误结果 |
| State Machine | 业务状态只能按合法路径变化 |
| Fixture | 测试固定数据 |
| Artifact | Agent 运行生成的文件或结果 |
| Readiness Gate | 上线前检查依赖、配置、权限、dry-run、审批策略 |
| Release Gate | 不满足质量门槛就不允许上线 |
| Sandbox | 隔离环境，防止误操作真实系统 |
| Permission | 最小权限原则 |
| Prompt Injection | 外部内容试图操控 Agent |
| Observability | 通过 logs、metrics、traces、artifacts 理解运行情况 |
| Audit | 记录谁在什么时候做了什么、依据是什么、谁审批了 |
| Canary | 小流量试运行 |
| Rollback | 出问题后恢复到旧版本 |

## 学习顺序

建议按这个顺序学，不要一开始就追多 Agent：

1. Agent Loop：理解 Agent 为什么不是聊天机器人。
2. Tools / Function Calling：理解 Agent 怎么真正做事。
3. State / Memory：理解长期任务为什么不能只靠上下文。
4. Eval / Golden Case：理解怎么证明 Agent 可靠。
5. Trace / Replay：理解怎么调试失败。
6. Guardrails / Approval：理解怎么控制风险。
7. CI / Readiness：理解怎么上线。
8. Observability / Reports：理解怎么给企业交付。
9. Compliance / Audit：理解怎么做责任闭环。
10. Multi-Agent / Handoff：最后再学，不要一开始就堆多个 Agent。

## 自测题

### 为什么企业 Agent 不能只靠 prompt 里的“不要乱操作”？

因为 prompt 只是软约束，不能真正阻止工具调用。企业需要代码层的 tool permission、guardrail、approval gate、sandbox 和 audit log。

### 为什么 Golden Cases 是 Agent 项目的护城河？

因为它沉淀了真实业务判断标准。模型、prompt、工具都可以换，但业务样例库能持续验证系统有没有退化。

### Trace 和 Log 的区别是什么？

Log 通常记录一条条事件。Trace 记录一次完整运行链路，包含多个 span，能看到输入、工具调用、状态变化、输出、错误和审批。

### Replay 为什么重要？

因为 Agent 有非确定性。线上出错后，只有保存输入、fixture、工具返回和状态快照，才能复现问题、比较修复前后差异，并把失败变成 regression case。

### MCP 和 Harness 的区别是什么？

MCP 解决 Agent 怎么标准化连接工具和数据。Harness 解决连接工具以后如何测试、监控、审批、回放、上线和审计。

## 最终记忆卡片

```text
Agent = 会做事的智能体。
Runtime = Agent 怎么跑。
Tool Governance = Agent 能动哪些按钮。
State = 当前业务事实。
Memory = 长期可复用信息。
Event Log = 发生过什么。
Golden Case = 固定输入和期望结果。
Eval = 判断做得对不对。
Trace = 运行黑匣子。
Replay = 失败重跑。
Guardrail = 刹车。
Approval = 高风险动作人类确认。
Sandbox = 安全隔离。
Permission = 最小权限。
CI = 自动测试。
Release Gate = 上线闸门。
Observability = 运行仪表盘。
Report = 给人看的结果。
Audit = 责任记录。
Harness = 让 Agent 可控、可测、可回放、可上线、可交付的工程系统。
```

## 结论

Enterprise Agent Harness 的本质不是某个框架，也不是某个模型 API。

它是一套工程闭环：

```text
让 Agent 在企业环境里：
  做事有边界，
  结果可验证，
  过程可追踪，
  失败可回放，
  风险可审批，
  权限可限制，
  上线有门禁，
  运行有报告，
  出事可审计。
```

真正要学会的不是“会不会写 Agent”，而是如何把 Agent 从 Demo 变成可交付系统。

## 参考来源

- [AIHot Agent 新鲜内容拆解：Auto-review、Skills、Spec 与环境工程](../digests/2026-06-12-aihot-agent-trends.md)
- [EurekAgent: Agent Environment Engineering is All You Need For Autonomous Scientific Discovery](https://arxiv.org/abs/2606.13662)
- [Hugging Face Papers: EurekAgent](https://huggingface.co/papers/2606.13662)
