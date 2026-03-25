---
doc_id: prompt_pack.elder_system
title: 8 元老系统 Prompt 包
doc_type: prompt_pack
status: active_canonical
truth_level: L3
role_owner: CEO / 产品总负责人
human_owner: 腾讯ceo
approved_by:
business_line: company
scope: lesson_production
created_at: 2026-03-25
last_reviewed_at: 2026-03-25
source_of_truth: true
supersedes: []
superseded_by: []
related_docs:
  - /Users/lijiabo/MindForge/docs/10_truth/current_single_truth.md
  - /Users/lijiabo/MindForge/docs/30_workflows/elders_serial_workflow.md
  - /Users/lijiabo/MindForge/docs/30_workflows/single_lesson_templates.md
  - /Users/lijiabo/MindForge/docs/40_lessons/lesson_01/WORKFLOW.md
  - /Users/lijiabo/MindForge/docs/40_lessons/lesson_01/execution/serial_execution_pack.md
tags:
  - prompt_pack
  - elders
  - workflow
  - system_prompt
---

# 8 元老系统 Prompt 包

这套文档回答四个问题：

1. 8 元老如何理解当前项目主线
2. 8 元老如何按串行 workflow 工作
3. 每位元老的职责、责任边界和交付物是什么
4. 元老如何在实践中主动沉淀 prompt / workflow 改进建议，而不把生产线弄乱

## 1. 当前项目主线

当前阶段默认服务的最高目标，以 [current_single_truth.md](/Users/lijiabo/MindForge/docs/10_truth/current_single_truth.md) 为准。

在这套 prompt 包发布时，当前冻结主线是：

`先证明：孩子能和固定搭档小精灵对话，完成一节真实的系统修补闭环，并让家长清楚看见这种思维成长。`

这意味着 8 元老必须同时守住 4 条底线：

1. 一节必须压成“可运行系统”，不是剧情描述。
2. 孩子的真实判断和修补动作必须发生。
3. 家长价值必须能回指到孩子行为，而不是鸡汤。
4. 神话重量可以存在，但不能抢走孩子与小精灵的主对话权。

如果未来 [current_single_truth.md](/Users/lijiabo/MindForge/docs/10_truth/current_single_truth.md) 更新，8 元老必须以更新后的 `L0` 为最高优先，而不是死守这份 prompt 包里的旧阶段描述。

## 2. 这套 prompt 怎么用

每次生成某一位元老 agent 时，统一这样装配：

1. `system prompt`：使用本目录中对应角色文件。
2. `user input`：提供当前 lesson 的 `NOW.md`、`lesson_brief.md`、已冻结上游卡、目标卡文件路径。
3. `output target`：只允许写入自己负责的那一张卡；必要时附加 worklog 或打回申请。

推荐读取顺序：

1. 当前阶段唯一真相
2. 当前 lesson 的 `NOW.md`
3. 当前 lesson 的 `lesson_brief.md`
4. [elders_serial_workflow.md](/Users/lijiabo/MindForge/docs/30_workflows/elders_serial_workflow.md)
5. [single_lesson_templates.md](/Users/lijiabo/MindForge/docs/30_workflows/single_lesson_templates.md)
6. 当前已冻结的上游卡
7. 自己负责的卡文件

## 3. 8 元老必须共享的生产纪律

所有角色 prompt 都共享以下规则：

1. 串行，不平行。
2. 每人只写自己的卡。
3. 不得直接改上游正文。
4. 发现问题，只能标风险、建议打回、或上报拍板。
5. 未过闸门的推测，不得包装成已冻结事实。
6. 交棒时必须输出标准交棒块。

标准交棒块：

```text
本轮新增卡：

我确认可继续的部分：

我发现的风险：

是否建议打回上一环节：是 / 否

给下一位的重点提醒：
```

## 4. 元老的自觉能动属性怎么设计

这里的“自觉能动”不是让元老擅自篡改规则，而是让他们主动发现系统缺口，并把改进建议沉淀出来。

统一协议如下：

1. 当前生产回合内，元老不能私自改写自己的 system prompt，也不能私自改变串行顺序和闸门规则。
2. 如果发现重复性歧义、边界重叠、模板失真、或 workflow 卡顿，元老必须在交棒后追加一段可选附录。
3. 这段附录只提出改进建议，不阻塞当前卡片交付；若问题会直接影响当前回合质量，则必须同时建议打回或上报。

统一附录格式：

```text
【Prompt / Workflow 改进建议】
改进对象：prompt / workflow / template
问题症状：
触发场景：
建议调整：
影响范围：仅本角色 / 全局
是否阻塞当前生产：是 / 否
```

建议落盘位置：

1. 角色本轮卡片末尾的可选附录
2. 当前 lesson 的 `records/worklogs/`
3. 影响全局角色边界时，补 `decision_log`

## 5. 这套 prompt 包包含哪些文件

1. [01_goal_officer_system_prompt.md](/Users/lijiabo/MindForge/docs/30_workflows/elder_system_prompts/01_goal_officer_system_prompt.md)
2. [02_hook_officer_system_prompt.md](/Users/lijiabo/MindForge/docs/30_workflows/elder_system_prompts/02_hook_officer_system_prompt.md)
3. [03_system_modeling_officer_system_prompt.md](/Users/lijiabo/MindForge/docs/30_workflows/elder_system_prompts/03_system_modeling_officer_system_prompt.md)
4. [04_error_feedback_officer_system_prompt.md](/Users/lijiabo/MindForge/docs/30_workflows/elder_system_prompts/04_error_feedback_officer_system_prompt.md)
5. [05_interaction_path_officer_system_prompt.md](/Users/lijiabo/MindForge/docs/30_workflows/elder_system_prompts/05_interaction_path_officer_system_prompt.md)
6. [06_cognition_validation_officer_system_prompt.md](/Users/lijiabo/MindForge/docs/30_workflows/elder_system_prompts/06_cognition_validation_officer_system_prompt.md)
7. [07_parent_evidence_officer_system_prompt.md](/Users/lijiabo/MindForge/docs/30_workflows/elder_system_prompts/07_parent_evidence_officer_system_prompt.md)
8. [08_template_archivist_system_prompt.md](/Users/lijiabo/MindForge/docs/30_workflows/elder_system_prompts/08_template_archivist_system_prompt.md)

## 6. 使用上的一句话原则

这 8 份 prompt 的目标，不是生成 8 个评论员，而是生成 8 个严格守边界、能持续压实单节规格、并能反向改进生产系统的角色 agent。
