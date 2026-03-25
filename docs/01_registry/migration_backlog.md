# 文档迁移清单

目标：分批把根目录里的活文迁入 `docs/`，同时不打断当前使用。

## 迁移原则

1. 先登记，再迁移
2. 先迁活文，再迁参考文
3. 每迁一批，就更新引用
4. 被替代的文档不删除，移入归档并写清 `superseded_by`

## Phase 0：立即止血

- [x] 建立文档治理规则
- [x] 建立文档登记册
- [x] 建立模板目录
- [x] 根目录停止新增新文档
- [ ] 团队开始把新记录统一写进 `docs/03_records/`

## Phase 1：迁移当前真相与总纲

| 优先级 | 当前路径 | 目标路径 | 动作 | 备注 |
|---|---|---|---|---|
| P0 | [current_single_truth.md](/Users/lijiabo/MindForge/docs/10_truth/current_single_truth.md) | `/Users/lijiabo/MindForge/docs/10_truth/current_single_truth.md` | 已迁移 | 唯一真相，已迁入 `docs/10_truth/` |
| P0 | [task_adventure_master_outline.md](/Users/lijiabo/MindForge/docs/10_truth/task_adventure_master_outline.md) | `/Users/lijiabo/MindForge/docs/10_truth/task_adventure_master_outline.md` | 已迁移 | 当前总纲，已迁入 `docs/10_truth/` |

## Phase 2：迁移战略与 lesson 上游

| 优先级 | 当前路径 | 目标路径 | 动作 | 备注 |
|---|---|---|---|---|
| P0 | [vibe_coding_for_kids_strategy.md](/Users/lijiabo/MindForge/docs/20_strategy/vibe_coding_for_kids_strategy.md) | `/Users/lijiabo/MindForge/docs/20_strategy/vibe_coding_for_kids_strategy.md` | 已迁移 | 阶段战略，已迁入 `docs/20_strategy/` |
| P0 | [mvp_world_setup.md](/Users/lijiabo/MindForge/docs/20_strategy/mvp_world_setup.md) | `/Users/lijiabo/MindForge/docs/20_strategy/mvp_world_setup.md` | 已迁移 | 世界观边界，已迁入 `docs/20_strategy/` |
| P0 | [lesson_01_brief.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/lesson_01_brief.md) | `/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/lesson_01_brief.md` | 已迁移 | 第一节上游正文，已迁入 lesson 目录 |

## Phase 3：迁移 workflow 与模板

| 优先级 | 当前路径 | 目标路径 | 动作 | 备注 |
|---|---|---|---|---|
| P1 | [elders_serial_workflow.md](/Users/lijiabo/MindForge/docs/30_workflows/elders_serial_workflow.md) | `/Users/lijiabo/MindForge/docs/30_workflows/elders_serial_workflow.md` | 已迁移 | 当前 workflow 主链，已迁入 `docs/30_workflows/` |
| P1 | [ceo_raci_matrix.md](/Users/lijiabo/MindForge/docs/30_workflows/ceo_raci_matrix.md) | `/Users/lijiabo/MindForge/docs/30_workflows/ceo_raci_matrix.md` | 已迁移 | 当前责任矩阵，已迁入 `docs/30_workflows/` |
| P1 | [single_lesson_templates.md](/Users/lijiabo/MindForge/docs/30_workflows/single_lesson_templates.md) | `/Users/lijiabo/MindForge/docs/30_workflows/single_lesson_templates.md` | 已迁移 | 当前模板，已迁入 `docs/30_workflows/` |
| P2 | [ceo_process_map.md](/Users/lijiabo/MindForge/docs/60_reference/ceo_process_map.md) | `/Users/lijiabo/MindForge/docs/60_reference/ceo_process_map.md` | 已迁移 | 当前仍有冲突，已迁入参考目录待修订 |
| P2 | [weekly_operating_sop.md](/Users/lijiabo/MindForge/docs/60_reference/weekly_operating_sop.md) | `/Users/lijiabo/MindForge/docs/60_reference/weekly_operating_sop.md` | 已迁移 | 已迁入参考目录，待按新串行链修订 |
| P2 | [ceo_flow_org_system.md](/Users/lijiabo/MindForge/docs/60_reference/ceo_flow_org_system.md) | `/Users/lijiabo/MindForge/docs/60_reference/ceo_flow_org_system.md` | 已迁移 | 组织参考文，已迁入 `docs/60_reference/` |
| P2 | [eight_roles_working_guide.md](/Users/lijiabo/MindForge/docs/60_reference/eight_roles_working_guide.md) | `/Users/lijiabo/MindForge/docs/60_reference/eight_roles_working_guide.md` | 已迁移 | 角色参考文，已迁入 `docs/60_reference/` |

## Phase 4：迁移技术骨架与执行包

| 优先级 | 当前路径 | 目标路径 | 动作 | 备注 |
|---|---|---|---|---|
| P1 | [lesson_01_minimum_unified_skeleton.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/lesson_01_minimum_unified_skeleton.md) | `/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/lesson_01_minimum_unified_skeleton.md` | 已迁移 | working 文档，已归入 lesson 目录 |
| P1 | [codex_execution_spec.md](/Users/lijiabo/MindForge/docs/50_execution/codex_execution_spec.md) | `/Users/lijiabo/MindForge/docs/50_execution/codex_execution_spec.md` | 已迁移 | 执行规范，已迁入 `docs/50_execution/` |
| P1 | [next_execution_arrangement.md](/Users/lijiabo/MindForge/docs/50_execution/next_execution_arrangement.md) | `/Users/lijiabo/MindForge/docs/50_execution/next_execution_arrangement.md` | 已迁移 | 当前安排，已迁入 `docs/50_execution/` |
| P1 | [serial_execution_pack.md](/Users/lijiabo/MindForge/docs/50_execution/serial_execution_pack.md) | `/Users/lijiabo/MindForge/docs/50_execution/serial_execution_pack.md` | 已迁移 | 当前执行包，已迁入 `docs/50_execution/` |

## Phase 5：记录系统启用

必须新增而不是继续散写：

1. `docs/03_records/gate_reviews/`
2. `docs/03_records/worklogs/`
3. `docs/03_records/decision_logs/`

第一批应补的记录：

1. 第一节闸门 A 审查记录
2. 第一节闸门 B 审查记录
3. 第一节闸门 C 审查记录
4. 第一节关键分歧拍板记录

## 历史作者信息回填

当前阻塞：

- 无法自动可靠识别每份文档由谁编写

解决方式：

1. 先在登记册里把 `human_owner` 统一标记 `TBD`
2. 后续由团队人工补齐
3. 从现在开始，所有新文档强制写 `human_owner`
