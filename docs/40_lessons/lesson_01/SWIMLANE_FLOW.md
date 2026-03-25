---
doc_id: lesson01.swimlane_flow
title: lesson_01 泳道调度图
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
  - /Users/lijiabo/MindForge/docs/40_lessons/lesson_01/HUMAN_DISPATCH_FLOW.md
  - /Users/lijiabo/MindForge/docs/40_lessons/lesson_01/ORCHESTRATION_MAP.md
  - /Users/lijiabo/MindForge/docs/40_lessons/lesson_01/ROLE_ASSIGNMENT.md
  - /Users/lijiabo/MindForge/docs/40_lessons/lesson_01/NOW.md
tags:
  - lesson_01
  - dispatch
  - visual
  - swimlane
---

# lesson_01 / 泳道调度图

这页只回答一件事：
从调度员视角看，`lesson_01` 这条链到底怎么发令、收件、放行、打回。

## 1. 泳道时序图

```mermaid
sequenceDiagram
    autonumber
    actor Coord as 你 / 调度员
    participant World as 米哈游世界师
    participant Elders as 8元老串行链
    participant CEO as 腾讯ceo
    participant Owner as 天美owner
    participant Codex as Codex / 工程实现

    Coord->>World: 冻结上游输入
    World-->>Coord: lesson_01_brief.md

    Coord->>Elders: 发第 1-3 棒
    Note over Elders: 1 节目标官 -> 2 戏剧钩子官 -> 3 系统建模官
    Elders-->>Coord: 01 / 02 / 03 cards

    Coord->>CEO: 进入 Gate A
    Coord->>Owner: 进入 Gate A
    CEO-->>Coord: 产品结论
    Owner-->>Coord: 技术结论

    alt Gate A 通过
        Coord->>Elders: 发第 4-5 棒
        Note over Elders: 4 错误反馈官 -> 5 交互路径官
        Elders-->>Coord: 04 / 05 cards
    else Gate A 打回
        Coord->>Elders: 打回第 2 棒或第 3 棒
        Elders-->>Coord: 修订后的 02 / 03 cards
    end

    Coord->>Owner: 进入 Gate B
    Owner-->>Coord: 可实现性结论

    alt Gate B 通过
        Coord->>Elders: 发第 6-7 棒
        Note over Elders: 6 认知校验官 -> 7 家长证据官
        Elders-->>Coord: 06 / 07 cards
    else Gate B 打回
        Coord->>Elders: 打回第 4 棒或第 5 棒
        Elders-->>Coord: 修订后的 04 / 05 cards
    end

    Coord->>CEO: 进入 Gate C
    CEO-->>Coord: 思维价值结论

    alt Gate C 通过
        Coord->>Elders: 发第 8 棒
        Note over Elders: 8 模板沉淀官
        Elders-->>Coord: 08 template card
    else Gate C 打回
        Coord->>Elders: 打回第 6 棒或第 7 棒
        Elders-->>Coord: 修订后的 06 / 07 cards
    end

    Coord->>Owner: 发起技术整包
    Owner-->>Coord: skeleton + execution 冻结包

    Coord->>Codex: 交付冻结执行包
    Codex-->>Coord: 工程实现开始
```

## 2. 调度员只需要记住的动作

```mermaid
flowchart TD
    A["看 NOW.md"] --> B["确认现在轮到谁"]
    B --> C["从 serial_execution_pack.md 取对应 prompt"]
    C --> D["只发给当前泳道负责人"]
    D --> E["等他把产物落盘"]
    E --> F{"这是闸门吗?"}
    F -- 否 --> G["继续下一棒"]
    F -- 是 --> H["拿 gate review 结论"]
    H --> I{"通过?"}
    I -- 是 --> G
    I -- 否 --> J["打回指定棒次"]
    J --> D
```

## 3. 泳道职责一句话版

| 泳道 | 你怎么理解它 |
|---|---|
| 你 / 调度员 | 发令、催收、放行、打回，不亲自写正文 |
| 米哈游世界师 | 先把世界和上游 brief 冻住，只在前段被咨询 |
| 8 元老串行链 | 一棒接一棒写卡，每人只写自己的卡 |
| 腾讯ceo | Gate A 和 Gate C 拍板，决定这节值不值得继续 |
| 天美owner | Gate A / B 审技术可实现性，最后整包交工程 |
| Codex | 只接冻结后的执行包，不接半成品讨论 |

## 4. 你最容易犯的错

- 一次放出两棒以上并行写。
- 让下一棒直接改上一棒正文。
- Gate 没落盘，只在聊天里说“过了”。
- 还没过 Gate C 就让天美owner把工程包做实。
