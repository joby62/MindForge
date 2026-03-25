# 文档登记册

用途：回答三个问题

1. 现在哪个文档算当前唯一真相
2. 哪个文档是总纲，哪个只是参考
3. 某份文档现在是活文、工作稿、参考文还是归档文

检索规则：

- 冲突时先看 `truth_level`
- 同层冲突时先看 `status`
- `source_of_truth = true` 的优先于 `false`

## A. 当前活跃文档

| truth_level | doc_id | 标题 | 当前路径 | doc_type | status | source_of_truth | role_owner | human_owner | business_line | scope | 最后修改时间 | 说明 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L0 | truth.current | 当前阶段唯一真相 | [current_single_truth.md](/Users/lijiabo/MindForge/docs/10_truth/current_single_truth.md) | single_truth | active_canonical | true | CEO / 产品总负责人 | TBD | greek_mvp | current_phase | 2026-03-25 13:23:21 | 当前阶段唯一真相，冲突时最高优先 |
| L1 | outline.master | 任务冒险引擎总纲 | [task_adventure_master_outline.md](/Users/lijiabo/MindForge/docs/10_truth/task_adventure_master_outline.md) | master_outline | active_canonical | true | CEO / 产品总负责人 | TBD | company | product | 2026-03-25 11:46:40 | 当前总纲 |
| L2 | strategy.vibe_kids | Vibe Coding for Kids 战略定义 | [vibe_coding_for_kids_strategy.md](/Users/lijiabo/MindForge/docs/20_strategy/vibe_coding_for_kids_strategy.md) | strategy | active_canonical | true | CEO / 产品总负责人 | TBD | greek_mvp | current_phase | 2026-03-25 13:23:21 | 当前阶段战略补充 |
| L2 | strategy.world.mvp | MVP 世界观主设定 | [mvp_world_setup.md](/Users/lijiabo/MindForge/docs/20_strategy/mvp_world_setup.md) | world_setup | active_canonical | true | 世界观 / 内容总负责人 | TBD | greek_mvp | chapter_01 | 2026-03-25 13:23:21 | 世界观边界与角色职责 |
| L3 | workflow.elders_serial | 8 元老串行 Workflow | [elders_serial_workflow.md](/Users/lijiabo/MindForge/docs/30_workflows/elders_serial_workflow.md) | workflow | active_canonical | true | CEO / 产品总负责人 | TBD | company | lesson_production | 2026-03-25 13:29:01 | 当前单节生产主链 |
| L3 | workflow.raci | CEO RACI 责任矩阵 | [ceo_raci_matrix.md](/Users/lijiabo/MindForge/docs/30_workflows/ceo_raci_matrix.md) | raci | active_reference | false | CEO / 产品总负责人 | TBD | company | lesson_production | 2026-03-25 09:48:57 | 当前责任分工参考 |
| L3 | template.single_lesson | 单节模板包 | [single_lesson_templates.md](/Users/lijiabo/MindForge/docs/30_workflows/single_lesson_templates.md) | template | active_canonical | true | 技术集成 Owner | TBD | company | lesson_production | 2026-03-25 09:59:55 | 当前模板入口 |
| L3 | reference.eight_roles | 八角色分工说明 | [eight_roles_working_guide.md](/Users/lijiabo/MindForge/docs/60_reference/eight_roles_working_guide.md) | role_guide | active_reference | false | CEO / 产品总负责人 | TBD | company | lesson_production | 2026-03-25 09:17:35 | 八角色总览参考 |
| L3 | workflow.org.system | CEO 视角流程分工设计 | [ceo_flow_org_system.md](/Users/lijiabo/MindForge/docs/60_reference/ceo_flow_org_system.md) | org_workflow | active_reference | false | CEO / 产品总负责人 | TBD | company | org_design | 2026-03-25 11:46:15 | 组织设计参考，不是当前唯一真相 |
| L3 | workflow.process.map | CEO 流程分工图 | [ceo_process_map.md](/Users/lijiabo/MindForge/docs/60_reference/ceo_process_map.md) | process_map | active_reference_pending_rewrite | false | CEO / 产品总负责人 | TBD | company | lesson_production | 2026-03-25 09:48:57 | 仍有参考价值，但部分节奏已被新安排覆盖 |
| L3 | workflow.weekly.sop | 周运营 SOP | [weekly_operating_sop.md](/Users/lijiabo/MindForge/docs/60_reference/weekly_operating_sop.md) | sop | active_reference_pending_rewrite | false | CEO / 产品总负责人 | TBD | company | weekly_ops | 2026-03-25 09:59:55 | 仍有参考价值，但需按新串行链修订 |
| L4 | lesson01.brief | 第一节正式 Brief | [lesson_01_brief.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/lesson_01_brief.md) | lesson_brief | active_canonical | true | 世界观 / 内容总负责人 | TBD | greek_mvp | lesson_01 | 2026-03-25 13:23:21 | 第一节上游 4 件套唯一正文 |
| L4 | lesson01.skeleton | 第一节最小统一骨架 | [lesson_01_minimum_unified_skeleton.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/lesson_01_minimum_unified_skeleton.md) | lesson_skeleton | working_pending_approval | false | 技术集成 Owner | TBD | greek_mvp | lesson_01 | 2026-03-25 13:24:15 | 技术候选骨架，不能直接当成已冻结真相 |
| L5 | execution.codex_spec | Codex 执行规范 | [codex_execution_spec.md](/Users/lijiabo/MindForge/docs/50_execution/codex_execution_spec.md) | codex_spec | active_canonical | true | 技术集成 Owner | TBD | company | execution | 2026-03-25 02:48:14 | 通用工程执行规范 |
| L5 | execution.next_arrangement | 接下来执行安排 | [next_execution_arrangement.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/execution/next_execution_arrangement.md) | execution_plan | active_working | true | CEO / 产品总负责人 | Codex | greek_mvp | lesson_01 | 2026-03-25 16:01:07 | 当前第一节推进安排，属于 lesson_01 工作区 |
| L5 | execution.serial_pack | 串行执行包 | [serial_execution_pack.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/execution/serial_execution_pack.md) | execution_packet | active_working | true | CEO / 产品总负责人 | Codex | greek_mvp | lesson_01 | 2026-03-25 16:00:59 | 当前发令包、闸门包、交接包，属于 lesson_01 工作区 |

## B. 归档源文档

以下内容统一视为历史源材料，不作为当前唯一真相：

| doc_id | 标题 / 文件 | 当前路径 | status | 说明 |
|---|---|---|---|---|
| archive.v0_1.eight_roles | eight_roles_responsibilities_v0_1 | [archive/source_docs_v0_1/eight_roles_responsibilities_v0_1.md](/Users/lijiabo/MindForge/archive/source_docs_v0_1/eight_roles_responsibilities_v0_1.md) | archived_source | 早期角色职责源稿 |
| archive.v0_1.parent_guide | parent_guide_task_adventure_engine_v0_1 | [archive/source_docs_v0_1/parent_guide_task_adventure_engine_v0_1.md](/Users/lijiabo/MindForge/archive/source_docs_v0_1/parent_guide_task_adventure_engine_v0_1.md) | archived_source | 早期家长端材料 |
| archive.v0_1.parent_child | parent_with_child_disney_task_adventure_engine_v0_1 | [archive/source_docs_v0_1/parent_with_child_disney_task_adventure_engine_v0_1.md](/Users/lijiabo/MindForge/archive/source_docs_v0_1/parent_with_child_disney_task_adventure_engine_v0_1.md) | archived_source | 早期概念材料 |
| archive.v0_1.single_lesson_workflow | single_lesson_workflow_v0_1 | [archive/source_docs_v0_1/single_lesson_workflow_v0_1.pdf](/Users/lijiabo/MindForge/archive/source_docs_v0_1/single_lesson_workflow_v0_1.pdf) | archived_source | 早期 workflow 材料 |
| archive.v0_1.codex_spec_pack | codex_spec_pack_template_v0_1 | [archive/source_docs_v0_1/codex_spec_pack_template_v0_1.md](/Users/lijiabo/MindForge/archive/source_docs_v0_1/codex_spec_pack_template_v0_1.md) | archived_source | 早期 Codex 规格模板 |
| archive.v0_1.tech_owner | technical_integration_owner_checklist_v0_1 | [archive/source_docs_v0_1/technical_integration_owner_checklist_v0_1.md](/Users/lijiabo/MindForge/archive/source_docs_v0_1/technical_integration_owner_checklist_v0_1.md) | archived_source | 早期技术 Owner 清单 |

## C. 当前阅读顺序

如果你是第一次进项目，统一按下面顺序看：

1. [current_single_truth.md](/Users/lijiabo/MindForge/docs/10_truth/current_single_truth.md)
2. [task_adventure_master_outline.md](/Users/lijiabo/MindForge/docs/10_truth/task_adventure_master_outline.md)
3. [vibe_coding_for_kids_strategy.md](/Users/lijiabo/MindForge/docs/20_strategy/vibe_coding_for_kids_strategy.md)
4. [mvp_world_setup.md](/Users/lijiabo/MindForge/docs/20_strategy/mvp_world_setup.md)
5. [lesson_01_brief.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/lesson_01_brief.md)
6. [elders_serial_workflow.md](/Users/lijiabo/MindForge/docs/30_workflows/elders_serial_workflow.md)
7. [single_lesson_templates.md](/Users/lijiabo/MindForge/docs/30_workflows/single_lesson_templates.md)
8. [next_execution_arrangement.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/execution/next_execution_arrangement.md)
9. [serial_execution_pack.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/execution/serial_execution_pack.md)

## D. 当前明确不该拿来当唯一真相的文档

以下文档仍可参考，但当前不应被当成“最高优先”：

1. [ceo_process_map.md](/Users/lijiabo/MindForge/docs/60_reference/ceo_process_map.md)
2. [weekly_operating_sop.md](/Users/lijiabo/MindForge/docs/60_reference/weekly_operating_sop.md)
3. [ceo_flow_org_system.md](/Users/lijiabo/MindForge/docs/60_reference/ceo_flow_org_system.md)
4. [eight_roles_working_guide.md](/Users/lijiabo/MindForge/docs/60_reference/eight_roles_working_guide.md)

原因：

- 这些文档更多是流程说明、组织说明或较早口径的展开
- 当前实际推进以 L0-L5 活跃文档组合为准
