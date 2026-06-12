# 提示词模板目录（审计版）

这一页只保留和 Codex OpenSchool 强相关、能直接帮助用户完成任务的提示词。上一版 20 个模板里有不少泛用内容，例如 PRD、Gibbs 复盘、Cornell 笔记、普通 issue 模板，虽然不一定错，但不够有辨识度，已从主目录下架。

## 收录标准

一个提示词必须同时满足：

1. 有明确使用场景，不是“万能助手”式套话。
2. 输出能直接进入下一步工作，例如代码审查、PPT 大纲、视频分镜、研究简报、skill 复盘。
3. 有约束和验收标准，能降低幻觉、隐私泄露或低质量输出。
4. 和本仓库主题相关：Codex、Agent、AI 教学、PPT、技术视频、视觉内容、工程质量。

## 主推模板

| # | 模板 | 用途 | 审计结论 |
|---:|---|---|---|
| 1 | [Codex 自我进化提示词](codex-self-evolution.md) | 复盘近期工作，把重复任务沉淀成 skill、subagent、automation 或 checklist | 通过 |
| 2 | [AI 教程视觉提示词方法：参考宝玉 skills](visual-prompts-baoyu-skills.md) | 为 AI 教程、知识卡片、封面和概念图设计视觉方向 | 通过 |
| 3 | [高价值提示词模板精选](high-value-prompts.md) | 8 个可直接使用的 Codex / Agent / PPT / 视频 / 研究模板 | 通过 |
| 4 | [Agent 新手任务提示词包：7 天完成第一个可验证闭环](agent-beginner-task-prompts.md) | 按 7 天入门路线提供可复制的任务判断、网页整理、工具选择、护栏和验收提示词 | 通过 |
| 5 | [Codex Goal 指令生成提示词](codex-goal-command-template.md) | 把一句模糊任务改写成可执行、可验证、有边界的 `/goal` 指令 | 通过 |

## 已下架模板

| 旧模板 | 下架原因 |
|---|---|
| PRD 一页纸、Bug / Feature Issue | 有用但过于通用，不是 OpenSchool 第一批重点 |
| Gibbs 六步复盘、Cornell 笔记 | 学习方法通用模板，不够贴近 Codex / Agent 实战 |
| 普通苏格拉底辅导、教师备课 | 教学方向可保留为未来专题，但当前版本缺少本地实践案例 |
| 公开 Prompt 库二次改写 | 可作为方法，但本身不是高价值可复用任务模板 |

后续新增提示词时，先写完整模板和使用边界，再进入主目录；不再为了数量放泛化模板。
