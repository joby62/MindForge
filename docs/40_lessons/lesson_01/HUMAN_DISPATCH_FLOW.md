---
doc_id: lesson01.human_dispatch_flow
title: lesson_01 人类调度看板
doc_type: orchestration_map
status: active_canonical
truth_level: L4
role_owner: CEO / 产品总负责人
human_owner: 腾讯ceo
approved_by:
business_line: greek_mvp
scope: lesson_01
created_at: 2026-03-25
last_reviewed_at: 2026-03-25
source_of_truth: true
supersedes: []
superseded_by: []
related_docs:
  - /Users/lijiabo/MindForge/docs/40_lessons/lesson_01/ORCHESTRATION_MAP.md
  - /Users/lijiabo/MindForge/docs/40_lessons/lesson_01/ROLE_ASSIGNMENT.md
  - /Users/lijiabo/MindForge/docs/40_lessons/lesson_01/NOW.md
tags:
  - lesson_01
  - dispatch
  - visual
  - board
---

# lesson_01 / 人类调度看板

这页只服务一个目的：
让你一眼看清“现在该叫谁，产物落哪，下一步去哪”。

## 1. 调度主图

```mermaid
flowchart LR
    A["米哈游世界师<br/>冻结上游 brief"] --> B["1 节目标官<br/>01_goal_card"]
    B --> C["2 戏剧钩子官<br/>02_hook_card"]
    C --> D["3 系统建模官<br/>03_system_card"]
    D --> GA{"Gate A<br/>腾讯ceo + 天美owner"}
    GA -- 过 --> E["4 错误反馈官<br/>04_error_card"]
    GA -- 打回 --> RB1["退回 2 或 3"]
    RB1 --> C
    E --> F["5 交互路径官<br/>05_interaction_card"]
    F --> GB{"Gate B<br/>天美owner"}
    GB -- 过 --> G["6 认知校验官<br/>06_cognition_card"]
    GB -- 打回 --> RB2["退回 4 或 5"]
    RB2 --> E
    G --> H["7 家长证据官<br/>07_parent_evidence_card"]
    H --> GC{"Gate C<br/>腾讯ceo"}
    GC -- 过 --> I["8 模板沉淀官<br/>08_template_archive_card"]
    GC -- 打回 --> RB3["退回 6 或 7"]
    RB3 --> G
    I --> J["天美owner 整包<br/>skeleton + execution"]
    J --> K["Codex / 工程实现"]
```

## 2. 你只要记住的调度口令

```mermaid
flowchart TD
    A["看 NOW.md<br/>判断当前阶段"] --> B["看 ROLE_ASSIGNMENT.md<br/>确认现在该叫谁"]
    B --> C["发对应 prompt<br/>serial_execution_pack.md"]
    C --> D["对方只改自己的文件"]
    D --> E{"是否完成本棒产物?"}
    E -- 否 --> D
    E -- 是 --> F{"进下一棒<br/>还是进闸门?"}
    F -- 下一棒 --> G["继续调度下一位"]
    F -- 闸门 --> H["叫拍板人写 gate review"]
    H --> I{"通过?"}
    I -- 是 --> G
    I -- 否 --> J["打回指定棒次"]
    J --> D
```

## 3. 人类调度员速查表

| 你看到的状态 | 你该叫的人 | 他只该改的地方 | 你拿到什么才算结束 |
|---|---|---|---|
| 上游未冻住 | 米哈游世界师 | [lesson_01_brief.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/lesson_01_brief.md) | brief 冻结 |
| 轮到第 1 棒 | 节目标官 | [01_goal_card.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/cards/01_goal_card.md) | 目标卡 |
| 轮到第 2 棒 | 戏剧钩子官 | [02_hook_card.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/cards/02_hook_card.md) | 钩子卡 |
| 轮到第 3 棒 | 系统建模官 | [03_system_card.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/cards/03_system_card.md) | 系统卡 |
| 轮到 Gate A | 腾讯ceo + 天美owner | [gate_a_review](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/records/gate_reviews/2026-03-25__lesson_01__gate_a__review.md) | Gate A 结论 |
| 轮到第 4 棒 | 错误反馈官 | [04_error_card.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/cards/04_error_card.md) | 错误卡 |
| 轮到第 5 棒 | 交互路径官 | [05_interaction_card.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/cards/05_interaction_card.md) | 交互卡 |
| 轮到 Gate B | 天美owner | [gate_b_review](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/records/gate_reviews/2026-03-25__lesson_01__gate_b__review.md) | Gate B 结论 |
| 轮到第 6 棒 | 认知校验官 | [06_cognition_card.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/cards/06_cognition_card.md) | 认知卡 |
| 轮到第 7 棒 | 家长证据官 | [07_parent_evidence_card.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/cards/07_parent_evidence_card.md) | 家长证据卡 |
| 轮到 Gate C | 腾讯ceo | [gate_c_review](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/records/gate_reviews/2026-03-25__lesson_01__gate_c__review.md) | Gate C 结论 |
| 轮到第 8 棒 | 模板沉淀官 | [08_template_archive_card.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/cards/08_template_archive_card.md) | 模板卡 |
| 准备交工程 | 天美owner | [lesson_01_minimum_unified_skeleton.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/lesson_01_minimum_unified_skeleton.md), [execution](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/execution) | 冻结执行包 |

## 4. 一条底线

如果有人想直接改上一棒正文，你就不放行。
