# lesson_01 / ROLE_ASSIGNMENT

## 当前状态

这份文件回答：

1. `lesson_01` 当前有哪些功能位
2. 每个功能位现在默认由谁兼任
3. 每个功能位应该主要改哪些文件
4. 哪些位置已经冻结为当前称谓

当前规则：

- 当前 lesson_01 采用“角色称谓即责任标识”的运行方式
- 腾讯 CEO、米哈游世界师、天美 Owner 作为固定外部角色称谓写入
- 8 位元老直接以职责名作为当前真人显示名
- 后续如果需要替换为真实姓名，再在本文件里覆盖更新

## 默认兼任方案

| 人员类型 | 当前默认兼任功能位 | 主要文件落点 | 当前真人 |
|---|---|---|---|
| CEO / 产品负责人 | CEO / 产品总负责人 + 节目标官 | `cards/01_goal_card.md`, `records/gate_reviews/`, `records/decision_logs/` | 腾讯ceo |
| 世界观架构师 / 内容负责人 | 世界观大使 + 戏剧钩子官 + 家长证据官 | `lesson_01_brief.md`, `cards/02_hook_card.md`, `cards/07_parent_evidence_card.md`, `records/decision_logs/` | 米哈游世界师 |
| 系统策划负责人 | 系统建模官 + 错误反馈官 + 认知校验官 | `cards/03_system_card.md`, `cards/04_error_card.md`, `cards/06_cognition_card.md`, `records/worklogs/` | 系统建模官 / 错误反馈官 / 认知校验官 |
| 交互负责人 | 交互路径官 | `cards/05_interaction_card.md`, `records/worklogs/` | 交互路径官 |
| 技术负责人 | 技术集成 Owner + 模板沉淀官 | `lesson_01_minimum_unified_skeleton.md`, `execution/`, `cards/08_template_archive_card.md`, `records/gate_reviews/`, `records/decision_logs/` | 天美owner |
| 工程实现 | Codex / 工程实现 | `execution/` 对应执行包落地后的实现任务 | Codex |

## 8 元老分配位

| 棒次 | 角色 | 当前责任文件 | 当前状态 | 当前真人 |
|---|---|---|---|---|
| 1 | 节目标官 | [01_goal_card.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/cards/01_goal_card.md) | not_started | 节目标官 |
| 2 | 戏剧钩子官 | [02_hook_card.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/cards/02_hook_card.md) | not_started | 戏剧钩子官 |
| 3 | 系统建模官 | [03_system_card.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/cards/03_system_card.md) | not_started | 系统建模官 |
| 4 | 错误反馈官 | [04_error_card.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/cards/04_error_card.md) | not_started | 错误反馈官 |
| 5 | 交互路径官 | [05_interaction_card.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/cards/05_interaction_card.md) | not_started | 交互路径官 |
| 6 | 认知校验官 | [06_cognition_card.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/cards/06_cognition_card.md) | not_started | 认知校验官 |
| 7 | 家长证据官 | [07_parent_evidence_card.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/cards/07_parent_evidence_card.md) | not_started | 家长证据官 |
| 8 | 模板沉淀官 | [08_template_archive_card.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/cards/08_template_archive_card.md) | not_started | 模板沉淀官 |

## 闸门负责人

| 闸门 | 审查人 | 必交记录 | 当前真人 |
|---|---|---|---|
| Gate A | CEO / 产品总负责人 + 技术集成 Owner | `records/gate_reviews/YYYY-MM-DD__lesson_01__gate_a__review.md` | 腾讯ceo / 天美owner |
| Gate B | 技术集成 Owner | `records/gate_reviews/YYYY-MM-DD__lesson_01__gate_b__review.md` | 天美owner |
| Gate C | CEO / 产品总负责人 | `records/gate_reviews/YYYY-MM-DD__lesson_01__gate_c__review.md` | 腾讯ceo |

## 关键说明

1. 这份文件只负责“谁管什么”
2. 真正的协作顺序看 [WORKFLOW.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/WORKFLOW.md)
3. 真正的发令和闸门 prompt 看 [serial_execution_pack.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/execution/serial_execution_pack.md)
4. 真正的当前状态看 [NOW.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/NOW.md)
