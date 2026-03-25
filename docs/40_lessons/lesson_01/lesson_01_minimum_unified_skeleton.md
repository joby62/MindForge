---
doc_id: lesson01.skeleton
title: 第一节最小统一骨架
doc_type: lesson_skeleton
status: working_pending_approval
truth_level: L4
role_owner: 技术集成 Owner
human_owner: TBD
approved_by:
business_line: greek_mvp
scope: lesson_01
created_at: 2026-03-25
last_reviewed_at: 2026-03-25
source_of_truth: false
supersedes: []
superseded_by: []
related_docs:
  - /Users/lijiabo/MindForge/docs/40_lessons/lesson_01/lesson_01_brief.md
  - /Users/lijiabo/MindForge/docs/50_execution/codex_execution_spec.md
tags:
  - lesson
  - skeleton
  - working
---

# 第一节最小统一骨架

版本：v0.1  
状态：供拍板  
范围：只覆盖希腊神话 MVP / 第一章 / 第一节  
对象：修补裂缝节 / 初火祭坛稳焰系统

## 0. 本轮边界

这份文档只交 5 个产物：

1. lesson 01 runtime 最小状态结构
2. dialogue -> structured action 的翻译链路
3. lesson 01 的错误模型和字段定义
4. parent evidence 输出 schema
5. 技术红线说明

本轮明确不做：

- 多章节通用框架
- 开放式自由对话方案
- 大而全平台层
- AI 代做答案层

---

## 1. Lesson 01 Runtime 最小状态结构

设计原则只有三条：

1. 对话、系统、运行、错误、证据必须挂在同一条 runtime 上
2. 关键推进动作必须通过 `structured action` 落成状态变化
3. 灰盒允许 hardcode，但不能长出第二套状态结构

### 1.1 最小 runtime shape

```ts
type Lesson01Runtime = {
  schemaVersion: "lesson01.runtime.v0";

  lesson: {
    lessonId: "greek_mvp_ch1_l01";
    lessonType: "repair_gap";
    primaryAxis: "debugging";
    secondaryAxis: "problem_definition";
    systemId: "first_fire_altar_stabilizer";
  };

  progression: {
    currentStage:
      | "scene_entry"
      | "anomaly_description"
      | "first_judgment"
      | "system_inspection"
      | "patch_declaration"
      | "running"
      | "feedback_review"
      | "pattern_extraction"
      | "completed";
    repairAttemptCount: number;
    gates: {
      anomalyDescribed: boolean;
      firstJudgmentMade: boolean;
      firstPatchDeclared: boolean;
      hasRerunAfterFailure: boolean;
      parentEvidenceReady: boolean;
    };
  };

  dialogue: {
    primaryNpcId: "sprite";
    turns: DialogueTurn[];
    pendingTranslation: StructuredActionDraft | null;
  };

  diagnosis: {
    observedProblemClass: "unknown" | "fire_missing" | "fire_unstable";
    childHypothesis: {
      problemClass: "unknown" | "fire_missing" | "fire_unstable";
      suspectedModules: ModuleId[];
      rationaleText: string | null;
      sourceTurnId: string | null;
    };
    currentFocusModules: ModuleId[];
  };

  system: {
    disturbanceSource: "ash_needle_maker";
    modules: Record<ModuleId, ModuleRuntime>;
    editableRules: Record<RuleId, EditableRule>;
    activeFaultPresetId: string;
  };

  actionLedger: {
    drafts: StructuredActionDraft[];
    applied: StructuredAction[];
  };

  runs: {
    history: RunRecord[];
    lastRunId: string | null;
  };

  errors: {
    active: Lesson01Error[];
    resolvedErrorIds: string[];
  };

  evidence: {
    records: ParentEvidenceRecord[];
    artifact: ParentEvidenceArtifact | null;
  };

  tech: {
    hardcodeFlags: string[];
  };
};
```

### 1.2 Lesson 01 的最小模块集合

```ts
type ModuleId =
  | "spark"
  | "altar_vessel"
  | "oxygen"
  | "seal"
  | "ignite_sequence";
```

```ts
type ModuleRuntime = {
  moduleId: ModuleId;
  displayName: string;
  visibleState: string;
  expectedState: string;
  isSuspected: boolean;
  observables: string[];
  relatedRuleIds: RuleId[];
};
```

### 1.3 Lesson 01 的最小可改规则集合

```ts
type RuleId =
  | "seal_threshold"
  | "oxygen_gate_condition"
  | "ignite_order";

type EditableRule = {
  ruleId: RuleId;
  ruleType: "condition" | "boundary" | "sequence";
  currentValue: string | string[];
  expectedValue: string | string[];
  lastPatchedByActionId: string | null;
};
```

### 1.4 最小辅助记录结构

```ts
type DialogueTurn = {
  turnId: string;
  speaker: "child" | "sprite" | "system";
  text: string;
  linkedActionId: string | null;
};

type RunRecord = {
  runId: string;
  attemptIndex: number;
  patchedRuleIds: RuleId[];
  emittedErrorIds: string[];
  outcome: "failed" | "partial_repair" | "stable_repair";
  worldFeedback: string[];
  systemFeedback: string[];
};
```

### 1.5 为什么这一版状态结构够用

它已经能承载本节必须发生的闭环：

1. `dialogue.turns` 记录孩子如何描述异常
2. `diagnosis.childHypothesis` 记录第一次判断
3. `actionLedger.applied` 记录“声明修改”被翻译成什么动作
4. `system.editableRules` 真正保存修改后的规则
5. `runs.history` 记录运行和重跑
6. `errors.active` 暴露局部错误
7. `evidence.records` 在过程中沉淀家长证据

---

## 2. Dialogue -> Structured Action 翻译链路

### 2.1 最小链路

第一节只需要一条受控链路，不需要开放式 agent。

```text
孩子发言
-> 回合识别
-> 槽位抽取
-> 动作草稿
-> 合法性校验
-> 状态提交
-> 运行/报错
-> 证据沉淀
```

### 2.2 回合识别层

第一节最小支持 7 类对话动作：

1. `DescribeAnomaly`
2. `ClassifyProblem`
3. `InspectModule`
4. `DeclarePatch`
5. `RunSystem`
6. `InterpretFeedback`
7. `RefinePatch`

### 2.3 统一动作草稿结构

```ts
type StructuredActionDraft = {
  draftId: string;
  turnId: string;
  kind:
    | "DescribeAnomaly"
    | "ClassifyProblem"
    | "InspectModule"
    | "DeclarePatch"
    | "RunSystem"
    | "InterpretFeedback"
    | "RefinePatch";
  sourceText: string;
  extractedSlots: Record<string, unknown>;
  missingSlots: string[];
  needsClarification: boolean;
};

type StructuredAction = StructuredActionDraft & {
  actionId: string;
  commitStatus: "applied" | "rejected";
  stateEffects: string[];
};
```

### 2.4 每类动作的最小必填槽位

| 动作 | 最小必填槽位 | 状态变化 |
| --- | --- | --- |
| `DescribeAnomaly` | `observedPhenomenon` | 写入 `dialogue.turns`，打开 `anomalyDescribed` |
| `ClassifyProblem` | `problemClass` | 写入 `diagnosis.childHypothesis.problemClass` |
| `InspectModule` | `moduleIds[]` | 写入 `diagnosis.currentFocusModules` |
| `DeclarePatch` | `ruleId`, `operator`, `proposedValue`, `reason` | 生成待应用规则变更 |
| `RunSystem` | `basedOnRuleIds[]` | 生成一次 `RunRecord` |
| `InterpretFeedback` | `runId`, `noticedErrorIds[]`, `newSuspicion[]` | 缩小模块范围 |
| `RefinePatch` | `ruleId`, `operator`, `proposedValue`, `reason`, `basedOnRunId` | 形成第二次修改 |

### 2.5 第一节的关键推进约束

以下阶段不能只停留在聊天文本，必须产生结构动作：

1. 描述异常
2. 第一次判断
3. 第一次声明修改
4. 第一次运行
5. 第一次看反馈
6. 第二次声明修改
7. 第二次运行

### 2.6 槽位不全时怎么处理

槽位不全时，不推进状态，不偷偷猜完整动作。

只允许两种结果：

1. 小精灵追问补槽位
2. 灰盒阶段用受控选项补槽位

例如：

- 孩子说“它不太对劲”
- 系统只能落成 `DescribeAnomaly` 草稿
- 小精灵追问：“你觉得是没点着，还是点着了但立不住？”
- 孩子补全后，才允许提交 `ClassifyProblem`

### 2.7 运行入口必须绑定声明修改

第一节不允许“随手点运行”。

`RunSystem` 之前必须存在：

1. 至少一个已提交的 `DeclarePatch` 或 `RefinePatch`
2. 该 patch 对应到真实 `RuleId`
3. 该 patch 写入 `system.editableRules`

否则就不是“对话驱动改系统”，而是“聊天后点按钮”。

---

## 3. Lesson 01 错误模型和字段定义

### 3.1 统一错误对象

```ts
type Lesson01Error = {
  errorId: string;
  lessonErrorKey:
    | "seal_condition_unmet"
    | "oxygen_boundary_unstable"
    | "ignite_sequence_shifted";
  canonicalType:
    | "ConditionMismatch"
    | "StateBoundaryMismatch"
    | "SequenceMismatch";
  affectedModule: ModuleId;
  affectedRuleIds: RuleId[];
  worldMessage: string;
  systemMessage: string;
  observability: {
    worldSignal: string[];
    systemSignal: string[];
    localMarker: string;
  };
  revealStage: "system_inspection" | "run_result" | "rerun_result";
  isFirstRunExpected: boolean;
  isBoundaryCase: boolean;
  narrowingHints: string[];
  childActionableNextSteps: Array<
    "InspectModule" | "DeclarePatch" | "RefinePatch"
  >;
};
```

### 3.2 第一节最小错误清单

#### 错误 A：封护条件未站稳

```text
lessonErrorKey: seal_condition_unmet
canonicalType: ConditionMismatch
affectedModule: seal
affectedRuleIds: [seal_threshold]
worldMessage: 火焰立起来了一瞬，但边缘一直在漏散
systemMessage: 封护条件未满足，火焰无法持续收束
worldSignal:
- 火圈边缘断开
- 火苗向外散
systemSignal:
- seal.visibleState = partial
- expectedState = closed
localMarker: seal_ring
revealStage: run_result
isFirstRunExpected: 预置链路可配置
isBoundaryCase: false
narrowingHints:
- 问题不在火种是否到达
- 优先检查封护是否闭合
childActionableNextSteps:
- InspectModule
- DeclarePatch
```

#### 错误 B：供氧处于临界态

```text
lessonErrorKey: oxygen_boundary_unstable
canonicalType: StateBoundaryMismatch
affectedModule: oxygen
affectedRuleIds: [oxygen_gate_condition]
worldMessage: 火焰能亮起来，但亮度一阵强一阵弱
systemMessage: 供氧落在临界区，足以引燃，不足以稳焰
worldSignal:
- 火光脉冲式忽明忽暗
- 热量传不远
systemSignal:
- oxygen.visibleState = borderline
- expectedState = stable_flow
localMarker: oxygen_channel
revealStage: run_result
isFirstRunExpected: 预置链路可配置
isBoundaryCase: true
narrowingHints:
- 火已经到达
- 问题不是完全缺氧，而是供氧站不稳
childActionableNextSteps:
- InspectModule
- RefinePatch
```

#### 错误 C：引燃顺序被拨偏

```text
lessonErrorKey: ignite_sequence_shifted
canonicalType: SequenceMismatch
affectedModule: ignite_sequence
affectedRuleIds: [ignite_order]
worldMessage: 火先窜起又失去依附，像点得太早
systemMessage: 引燃顺序错误，稳定条件尚未就位就触发了点燃
worldSignal:
- 火花先跳
- 火焰没有挂住火坛
systemSignal:
- ignite_sequence.visibleState = misordered
- expectedState = anchored_order
localMarker: ignition_path
revealStage: run_result
isFirstRunExpected: false
isBoundaryCase: false
narrowingHints:
- 先后次序有问题
- 即使每个模块单看都存在，顺序错了仍会失败
childActionableNextSteps:
- InspectModule
- DeclarePatch
```

### 3.3 第一节错误模型的三个硬要求

1. 错误必须能指到模块，不允许只有整坛失败
2. 错误必须能指到下一步动作，不允许只有诊断句
3. 错误必须区分“没发生”和“发生了但不稳”

### 3.4 推荐的最小激活方式

第一节最稳的做法是：

1. 预置一个主错误
2. 第一轮修补后暴露第二个更窄的错误
3. 保留一个分支错误给误修路径

这样才能自然支持：

`第一次判断 -> 第一次修 -> 跑 -> 看反馈 -> 再修一次`

---

## 4. Parent Evidence 输出 Schema

原则：家长证据不是结尾 copy，而是 runtime 里持续沉淀的结构记录。

### 4.1 顶层输出结构

```ts
type ParentEvidenceArtifact = {
  schemaVersion: "parent_evidence.v0";
  artifactId: string;
  lessonId: "greek_mvp_ch1_l01";
  systemId: "first_fire_altar_stabilizer";
  sessionStatus: "partial_repair" | "stable_repair" | "incomplete";
  summary: {
    firstProblemClass: "unknown" | "fire_missing" | "fire_unstable";
    finalProblemClass: "unknown" | "fire_missing" | "fire_unstable";
    repairAttemptCount: number;
    distinctErrorTypesSeen: string[];
    rerunCompleted: boolean;
  };
  records: ParentEvidenceRecord[];
};
```

### 4.2 单条证据记录结构

```ts
type ParentEvidenceRecord = {
  recordId: string;
  category:
    | "problem_definition"
    | "structure_decomposition"
    | "debugging"
    | "pattern_extraction";
  axis:
    | "problem_definition"
    | "structure_decomposition"
    | "debugging"
    | "pattern_extraction";
  claimKey: string;
  status: "demonstrated" | "attempted" | "not_yet";
  structuredFacts: Record<string, unknown>;
  sourceRefs: {
    turnIds: string[];
    actionIds: string[];
    runIds: string[];
    errorIds: string[];
  };
  confidence: number;
  renderKey: string;
};
```

### 4.3 第一节至少要稳定产出的三条证据

#### 证据 1：问题定义证据

```text
category: problem_definition
claimKey: distinguish_fire_missing_vs_fire_unstable
status: demonstrated
structuredFacts:
- chosenProblemClass = fire_unstable
- rejectedProblemClass = fire_missing
- sourceRationale = 孩子提到“火已经亮了，但立不住”
sourceRefs:
- 至少 1 个孩子回合
- 1 个 ClassifyProblem action
renderKey: parent.problem_definition.distinguish_unstable
```

#### 证据 2：结构拆解证据

```text
category: structure_decomposition
claimKey: inspect_modules_instead_of_random_try
status: demonstrated
structuredFacts:
- inspectedModules = [seal, oxygen]
- moduleCount = 2
- firstFocusedModule = seal
sourceRefs:
- 1 个或多个 InspectModule action
- 对应模块的局部错误
renderKey: parent.structure.inspect_modules
```

#### 证据 3：调试证据

```text
category: debugging
claimKey: use_feedback_to_refine_patch
status: demonstrated
structuredFacts:
- firstRunErrorType = ConditionMismatch
- secondRunErrorType = StateBoundaryMismatch
- rerunCount = 1
- refinedRuleId = oxygen_gate_condition
sourceRefs:
- 2 次 patch action
- 2 次 run
- 至少 1 次 InterpretFeedback
renderKey: parent.debugging.refine_after_feedback
```

### 4.4 证据生成规则

每条家长证据都必须同时满足：

1. 有孩子侧表达来源
2. 有系统侧状态或运行来源
3. 有可复述的 `claimKey`

如果只有一句结论文案，没有 `sourceRefs`，则视为无效证据。

---

## 5. 技术红线说明

### 红线 1：关键回合不能只留下聊天文本

以下动作如果没有落成 `StructuredAction`，本节就偏了：

1. 第一次问题判断
2. 第一次声明修改
3. 第一次运行
4. 看反馈后的第二次修改

### 红线 2：运行不能脱离规则状态

`RunSystem` 必须读取当前 `editableRules`，不能用剧情脚本直接播成功或失败。

否则：

- 对话不会真的改系统
- 错误不会真的反映修改结果
- 家长证据会失真

### 红线 3：错误不能只做统一失败条

每次失败至少要带出：

1. `canonicalType`
2. `affectedModule`
3. `localMarker`
4. `childActionableNextSteps`

缺一项，错误就不能承担调试入口。

### 红线 4：AI / NPC 不能绕过孩子的第一判断

NPC 可以：

- 追问
- 镜像
- 帮孩子缩范围

NPC 不能：

- 直接给正确问题分类
- 自动替孩子提交 patch
- 在没有孩子声明的情况下自动运行修复

### 红线 5：家长证据不能在结束页临时拼

证据必须在以下节点实时沉淀：

1. `ClassifyProblem`
2. `InspectModule`
3. `RunSystem`
4. `InterpretFeedback`
5. `RefinePatch`

否则最终只能写出“完成了一节”，写不出“孩子到底怎么想的”。

### 红线 6：灰盒 hardcode 只能放在内容，不许放在 contract

允许 hardcode 的位置：

- 预置错误链
- 世界语言文案
- 小精灵追问文案
- lesson 01 的 rule preset

不允许 hardcode 的位置：

- 第二套 runtime 命名
- 第二套错误字段
- 第二套 evidence schema
- 绕开 actionLedger 的直接状态改写

### 红线 7：不能靠一路 next 过关

阶段推进至少受以下 gate 控制：

1. 没有第一次判断，不能进 patch
2. 没有 patch，不能进 run
3. 没有反馈阅读，不能进第二次 patch
4. 没有 rerun，不能直接给“本节完成”

---

## 6. 当前需要你拍板的分歧点

以下三处都有两条以上合理路径，而且会影响系统结构、错误模型、家长证据或长期复用，所以这里不替你拍板。

### 分歧点 A：对话翻译引擎走“受控槽位”还是“自由语义 patch”

路径 A：受控槽位翻译

- 做法：先识别动作类型，再补齐少量固定槽位
- 好处：闭环稳定、trace 清楚、证据好沉淀
- 代价：自由感弱一些

路径 B：自由语义直接产出 patch

- 做法：让 parser 直接从自然语言生成规则改动
- 好处：更像自然对话
- 代价：错误归因和证据追踪会明显变差

建议默认：路径 A

### 分歧点 B：第一节默认预置错误链怎么排

路径 A：`seal_condition_unmet -> oxygen_boundary_unstable`

- 好处：最容易支撑“火到了但不稳”的第一判断
- 好处：局部修复感最强，家长证据最好讲

路径 B：`ignite_sequence_shifted -> seal_condition_unmet`

- 好处：更早训练顺序意识
- 代价：第一眼异常与第一判断的对应关系更绕

建议默认：路径 A

### 分歧点 C：家长证据是“过程流式沉淀”还是“结束时回放总结”

路径 A：过程流式沉淀

- 做法：每个关键 action/run 立即生成 evidence record
- 好处：trace 真、技术债低、长期复用强

路径 B：结束时回放总结

- 做法：会话结束后再从日志反推证据
- 好处：短期实现快
- 代价：容易漏证据，最终变成文案猜测

建议默认：路径 A
