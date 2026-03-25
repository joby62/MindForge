---
doc_id: execution.codex_spec
title: Codex 执行规范
doc_type: codex_spec
status: active_canonical
truth_level: L5
role_owner: 技术集成 Owner
human_owner: TBD
approved_by:
business_line: company
scope: execution
created_at: 2026-03-25
last_reviewed_at: 2026-03-25
source_of_truth: true
supersedes: []
superseded_by: []
related_docs:
  - /Users/lijiabo/MindForge/docs/30_workflows/single_lesson_templates.md
tags:
  - execution
  - codex
  - canonical
---

# Codex 执行规范

版本：v0.1  
用途：供 Codex / Agent 在实现“任务冒险引擎”相关页面、交互和原型时直接使用

## 1. Mission

Build the smallest shippable version of the Task Adventure Engine as a repeatable single-lesson system, not as a one-off story demo.

中文解释：

- 先做最小单节闭环，不先做大世界
- 先证明孩子端思维循环成立，再补包装
- 先证明家长能看见成长，再谈复杂商业层
- 所有实现都必须服务于复用，而不是只服务当前一节

## 2. 当前阶段定义

当前阶段是：单节灰盒 / 早期正式原型阶段。

这意味着：

- 默认目标是一节可运行的任务闭环
- 默认范围是 20-30 分钟的一节体验
- 默认重点是判断、改规则、看报错、重跑、提炼
- 默认不以世界规模、动画量、内容量作为完成标准

## 3. 产品本体

This product is not a coding lesson, not an online tutoring flow, and not a gamified worksheet.

It is a task-driven adventure system where the child:

1. enters an abnormal situation
2. identifies the real problem
3. understands the system structure
4. edits rules or logic
5. runs the system
6. reads observable errors
7. debugs and reruns
8. leaves with a reusable pattern

If an implementation does not support this loop, it is off-spec.

## 4. Non-Negotiable Design Principles

Every implementation must satisfy all of the following:

1. Task first
   - The child must enter a meaningful situation, not a lesson page
2. Identity before student-feel
   - The child should feel like a participant, fixer, designer, investigator, or engineer
3. Thinking hidden in action
   - The five thinking axes must happen through interaction, not mostly through explanation
4. Failure without shame
   - Failure must be framed as “the system is not fully tuned yet,” not “you are wrong”
5. Observable progress
   - The system must preserve process traces and parent-readable evidence
6. AI supports thinking, never replaces it
   - AI may ask, mirror, hint, and scaffold; it must not skip core judgment steps
7. Reusability over one-off cleverness
   - Prefer generic structures, generic state models, and configurable flows

## 5. 五大主轴

Any lesson spec must explicitly target one primary axis and optionally one secondary axis.

The five axes are:

1. 定义问题
2. 拆解任务
3. 建立规则
4. 调试纠错
5. 抽象迁移

Do not design a lesson that claims to train all five equally.

## 6. 单节最小闭环

Every lesson must include these stages:

1. 异常进入
2. 问题判断
3. 系统排查
4. 法则修改
5. 系统运行
6. 错误反馈
7. 二次修复与重跑
8. 模式提炼

Hard constraints:

- There must be at least one real judgment point
- There must be at least one “modify -> run -> inspect error” cycle
- The child cannot progress only by clicking “next”
- At least one rerun must happen after an imperfect result
- The ending must include a transferable pattern sentence or equivalent abstraction

## 7. Required Child-Facing Screens

At minimum, implement these three screen types:

### 7.1 异常现场界面

Must show:

- scene abnormality
- world reaction
- role dialogue or hook
- initial clues

Primary purpose:

- make the child want to intervene

### 7.2 系统视图界面

Must show:

- modules
- states
- connections
- dependencies
- current abnormal area

Primary purpose:

- convert the situation into an analyzable system

### 7.3 法则台界面

Must show:

- editable rules / conditions / sequence / permissions / paths
- run action
- error feedback
- replay or result trace
- entry to second-round repair

Primary purpose:

- let the child change the system and learn through feedback

## 8. Parent Evidence Output

At least one parent-facing summary or evidence artifact must be generated for each lesson run.

It must contain three categories:

1. 问题定义证据
2. 结构拆解证据
3. 调试证据

It must not be limited to:

- completion status
- duration
- pass / fail
- score-only summaries

## 9. Error System Contract

The error system is mandatory. A lesson without typed, observable errors is invalid.

### 9.1 Required properties of every error

Each error must have:

- `type`
- `worldMessage`
- `observability`
- `revealStage`
- `isFirstRunExpected`
- `isBoundaryCase`
- `affectedModule` or equivalent localization

### 9.2 First-version canonical error taxonomy

Use these categories unless a reviewed spec says otherwise:

- `ConditionMismatch`
- `SequenceMismatch`
- `PermissionMismatch`
- `StateBoundaryMismatch`

### 9.3 Error behavior rules

- Errors must help narrow the problem space
- Errors must be locally visible, not only shown as full failure
- The child must be able to act on the error
- Errors must support hypothesis -> edit -> rerun
- Do not collapse multiple distinct errors into one generic failure state

## 10. State and Runtime Contract

Implementations should converge around one reusable runtime model.

At minimum, a lesson runtime should be able to represent:

- lesson identity
- primary / secondary axis
- current stage
- module states
- editable rules
- last run result
- emitted errors
- repair attempt count
- evidence records
- completion / extraction state

Do not create a brand-new naming scheme for every lesson.

## 11. Config-Driven Lesson Input

Codex should expect a lesson to be described by a structured spec pack, not by loose narrative.

Minimum required cards:

1. system structure card
2. error design card
3. interaction flow card
4. success criteria card

Recommended supporting cards:

5. lesson goal card
6. world language and copy constraints card
7. explicit non-goals list

If the core four cards are missing, stop and report that the spec is incomplete.

## 12. Implementation Priorities

Always build in this order:

1. state runs correctly
2. rules are editable
3. typed errors are emitted
4. rerun loop works
5. parent evidence is generated
6. world copy and visual polish are layered on top

Graybox first, packaging second.

Do not spend the first pass on:

- large maps
- side quests
- cinematic animation
- voice acting
- progression economy
- decorative systems that do not improve the core loop

## 13. Visual and Interaction Constraints

The product should feel premium, editorial, spacious, and world-like, not like enterprise software and not like a low-age toy.

Required direction:

- generous spacing
- soft layering over hard separation
- strong identity framing
- readable information hierarchy
- emotionally serious but still inviting

Forbidden direction:

- dense dashboard UI
- default admin-card aesthetics
- low-age infantilized copy
- pure reward-first interaction
- heavy border-based layout separation

If aesthetic goals conflict with clarity of the lesson loop, clarity wins in graybox stage.

## 14. Copy Constraints

Child-facing copy should be:

- respectful
- world-aware
- challenge-oriented
- non-preachy

System feedback should be:

- diagnostic
- calm
- actionable
- non-shaming

Avoid:

- tutorial over-explaining
- school-like correction tone
- “correct answer” framing as the main interaction language

## 15. AI Constraints

AI may:

- ask clarifying questions inside the experience
- mirror what the child has done
- provide bounded hints
- help compare current run vs expected run
- help surface a transferable pattern

AI may not:

- directly output the full rule solution by default
- auto-fix the system without child involvement
- replace the first judgment step
- trivialize debugging into a magic reveal

## 16. Technical Integration Rules

When implementing multiple lessons, preserve these shared layers:

- unified state system
- unified error taxonomy
- unified rule-console component logic
- unified run / rerun mechanism
- unified evidence output shape
- unified config format

Temporary hardcode is acceptable only when:

- it is explicitly recorded as technical debt
- it does not fragment the shared runtime model
- it does not create a second incompatible version of a core component

## 17. Stop-and-Report Conditions

Codex must stop and report instead of guessing when:

- more than one reasonable product path exists with materially different outcomes
- the lesson spec does not define the system object clearly
- the error model is too vague to implement
- success criteria are abstract and non-testable
- the requested scope would break the single-lesson focus

Suggested report format:

1. path A and its tradeoff
2. path B and its tradeoff
3. recommended default path

## 18. Acceptance Criteria

A lesson implementation is not done until all items below are satisfied:

1. The child can complete at least one real problem-classification judgment
2. The child can perform at least two rule modifications
3. The system can expose at least two distinct error types
4. A second run shows a local repair result, not only binary success / failure
5. Parent evidence generates at least three meaningful records
6. The flow preserves the loop of judgment -> modification -> run -> inspection -> rerun
7. The implementation feels like a task experience, not a lesson page

## 19. Required Codex Return Format

When Codex finishes a task, it should return:

1. implemented pages / screens
2. state flow summary
3. error flow summary
4. unresolved decision points
5. success criteria checklist

It should not only say “implementation complete”.

## 20. Final Principle

Codex does not receive “make a fun myth-based coding experience”.

Codex receives:

- a clear system
- a clear error model
- a clear interaction loop
- a clear success standard
- a clear non-goal boundary

If the input is still a vague vision, the correct action is to ask for a better spec, not to improvise product decisions.
