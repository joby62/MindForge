# lesson_01 / WORKFLOW

## 1. 这份文档回答什么

回答四个实际问题：

1. 技术 Owner、世界观架构师、CEO、8 元老在这一节里到底怎么协作
2. 每个人分别改什么文件
3. 每个人的“提交”是什么，记录落在哪里
4. 当前系统里这些职责是否已经有文档支撑

## 2. 结论先说

对于 `lesson_01`，正确的组织方式不是大家都在全仓库里改文档，而是：

1. 全局稳定文档提供上层约束
2. `lesson_01` 工作区承接这节的所有日常协作
3. 每个角色只在自己的落盘区域里提交
4. 每过一个闸门，就冻结通过内容

## 3. 参与角色与位置

### CEO / 实际拍板人

位置：

- 不在 8 元老正文创作链内部
- 在闸门 A 和闸门 C 进行拍板
- 在出现多条产品路径时进行最终默认路径选择

本节主要提交：

1. 闸门 A 审查结论
2. 闸门 C 审查结论
3. 关键分歧的决策记录

主要落盘位置：

- `records/gate_reviews/`
- `records/decision_logs/`

### 世界观架构师 / 世界观大使

位置：

- 在串行链启动前给出上游输入
- 在 1-3 棒期间可被咨询
- 不一路主导后续所有棒次

本节主要提交：

1. 上游 4 件套冻结版
2. 必要时补充世界语言和角色边界
3. 如果上游设定被打回，负责修订上游正文

主要落盘位置：

- `lesson_01_brief.md`
- `records/decision_logs/`（若涉及世界设定拍板）
- `records/worklogs/`

### 技术集成 Owner

位置：

- 不从第 1 棒开始重写内容
- 在闸门 A / B 作为技术审查者
- 在闸门 C 后把 lesson 文档整理成 Codex 输入包

本节主要提交：

1. 闸门 A 技术审查意见
2. 闸门 B 技术审查意见
3. 技术候选骨架修订
4. Codex 输入包 / 执行整包
5. 技术分歧上报与统一骨架约束

主要落盘位置：

- `lesson_01_minimum_unified_skeleton.md`
- `execution/`
- `records/gate_reviews/`
- `records/decision_logs/`
- `records/worklogs/`

### 八元老

位置：

- 在串行链内部按顺序工作
- 每人只负责自己的卡
- 不得直接改上游正文

本节主要提交：

1. 自己负责的卡
2. 交棒块
3. 必要时的打回申请

主要落盘位置：

- `cards/`
- `records/worklogs/`

## 4. lesson_01 的具体工作流

### Phase 0：启动与冻结输入

负责人：

- 世界观架构师
- CEO

动作：

1. 冻结 `lesson_01_brief.md`
2. 在 `NOW.md` 标记当前状态
3. 如有关键设定分歧，写决策记录

输出：

1. 上游正文可用
2. 允许进入第 1 棒

### Phase 1：元老 1-3 串行

顺序：

1. 节目标官
2. 戏剧钩子官
3. 系统建模官

每人动作：

1. 只编辑自己负责的 card 文件
2. 在 card 末尾写交棒块
3. 如需要，补一条 worklog

输出：

1. `01_goal_card.md`
2. `02_hook_card.md`
3. `03_system_card.md`

### Phase 2：闸门 A

负责人：

- CEO
- 技术集成 Owner

动作：

1. 审查 1-3 棒卡片
2. 输出一份正式 gate review
3. 如有分歧，补决策记录

输出：

- `records/gate_reviews/YYYY-MM-DD__lesson_01__gate_a__review.md`

### Phase 3：元老 4-5 串行

顺序：

4. 错误反馈官
5. 交互路径官

输出：

1. `04_error_card.md`
2. `05_interaction_card.md`

### Phase 4：闸门 B

负责人：

- 技术集成 Owner

动作：

1. 审查错误与交互
2. 判断是否具备可实现性
3. 必要时要求打回第 4 棒或第 5 棒

输出：

- `records/gate_reviews/YYYY-MM-DD__lesson_01__gate_b__review.md`

### Phase 5：元老 6-7 串行

顺序：

6. 认知校验官
7. 家长证据官

输出：

1. `06_cognition_card.md`
2. `07_parent_evidence_card.md`

### Phase 6：闸门 C

负责人：

- CEO

动作：

1. 判断这节是否真的练思维
2. 判断家长价值是否能一句话讲清

输出：

- `records/gate_reviews/YYYY-MM-DD__lesson_01__gate_c__review.md`

### Phase 7：元老 8 收束

负责人：

- 模板沉淀官

动作：

1. 提炼复用项
2. 记录踩坑
3. 形成模板归档卡

输出：

- `08_template_archive_card.md`

### Phase 8：技术 Owner 整包

负责人：

- 技术集成 Owner

动作：

1. 读取冻结后的 cards
2. 对齐 skeleton
3. 生成正式 Codex 输入包
4. 标注允许 hardcode / 禁止 hardcode

输出：

- `execution/` 下的执行包
- 必要时补充技术决策记录

## 5. 每个角色具体改什么

| 角色 | 主要编辑文件 | 允许补充文件 | 不该改的内容 |
|---|---|---|---|
| 世界观架构师 | `lesson_01_brief.md` | `records/decision_logs/`, `records/worklogs/` | 8 张卡正文 |
| CEO | `records/gate_reviews/`, `records/decision_logs/` | `NOW.md` | 他人卡正文 |
| 节目标官 | `cards/01_goal_card.md` | `records/worklogs/` | 2-8 棒卡 |
| 戏剧钩子官 | `cards/02_hook_card.md` | `records/worklogs/` | 1 棒与 3-8 棒正文 |
| 系统建模官 | `cards/03_system_card.md` | `records/worklogs/` | 1-2 棒与 4-8 棒正文 |
| 错误反馈官 | `cards/04_error_card.md` | `records/worklogs/` | 1-3 棒与 5-8 棒正文 |
| 交互路径官 | `cards/05_interaction_card.md` | `records/worklogs/` | 1-4 棒与 6-8 棒正文 |
| 认知校验官 | `cards/06_cognition_card.md` | `records/worklogs/` | 1-5 棒与 7-8 棒正文 |
| 家长证据官 | `cards/07_parent_evidence_card.md` | `records/worklogs/` | 1-6 棒与 8 棒正文 |
| 模板沉淀官 | `cards/08_template_archive_card.md` | `records/worklogs/` | 前 7 张卡正文 |
| 技术集成 Owner | `lesson_01_minimum_unified_skeleton.md`, `execution/` | `records/gate_reviews/`, `records/decision_logs/`, `records/worklogs/` | 未过闸门前重写卡正文 |

## 6. 每个人的“提交”到底是什么

这里有两种提交，不要混。

### A. 文档提交

指的是把本轮结果正式落到文件里。

最小要求：

1. 角色正文写进指定文件
2. 补交棒块或审查结论
3. 如有关键分歧，补决策记录

### B. Git 提交

指的是把这一批文档改动作为一次版本历史提交。

建议规则：

1. 一个角色完成自己一棒后，形成一次小提交
2. 一个闸门完成后，形成一次 gate 提交
3. 一个关键拍板完成后，形成一次 decision 提交
4. 技术 Owner 整包给 Codex 时，形成一次 execution 提交

## 7. 推荐 commit 颗粒度

建议使用下面格式：

```text
role(scope): action
```

例如：

- `world(lesson_01): freeze upstream 4-pack`
- `goal(lesson_01): complete goal card`
- `hook(lesson_01): complete hook card`
- `system(lesson_01): complete system card`
- `gate(lesson_01): record gate A review`
- `decision(lesson_01): freeze default error chain`
- `tech(lesson_01): assemble codex input pack`
- `archive(lesson_01): complete template archive card`

原则：

1. 不要把多棒内容揉成一个大提交
2. 不要把正文改动和 gate review 混成一个提交
3. 不要把 lesson_01 的改动和公司级治理改动混在一起

## 8. 当前系统里，这些职责是否已经有文档支撑

### 已经有

1. 8 元老顺序、闸门、交棒规则  
   见 [elders_serial_workflow.md](/Users/lijiabo/MindForge/docs/30_workflows/elders_serial_workflow.md)
2. 角色拍板边界与 RACI  
   见 [ceo_raci_matrix.md](/Users/lijiabo/MindForge/docs/30_workflows/ceo_raci_matrix.md)
3. lesson_01 执行包与闸门 prompt  
   见 [serial_execution_pack.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/execution/serial_execution_pack.md)
4. 当前 lesson 工作区结构  
   见 [README.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/README.md)

### 之前缺的

之前缺的是这三件事：

1. 没有把角色职责映射到 lesson 工作区的具体文件
2. 没有把“文档提交”和“Git 提交”区分开
3. 没有把 lesson 专属记录固定落在 lesson 工作区

这份文档就是在补这个缺口。

## 9. 他们现在知道自己职责么

从系统角度看：

- 抽象职责是有文档支撑的
- 具体到 `lesson_01` 的文件落点、提交流程、记录路径，之前并不够清楚

所以答案是：

`职责边界原来部分清楚，但操作层还不够清楚；现在需要以本工作区的文件结构和本文件为准执行。`
