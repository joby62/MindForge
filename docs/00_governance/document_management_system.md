# 文档治理系统

版本：v0.1  
状态：立即生效  
用途：解决“谁写的、哪个算真相、哪些是总纲、哪些只是记录、打回和复盘放哪里、以后怎么检索”的问题

## 1. 先把问题说清楚

当前文档系统的根问题不是文档数量多，而是五件事同时缺失：

1. 没有统一入口
2. 没有文档层级
3. 没有明确的唯一真相与总纲定义
4. 没有固定的记录落点
5. 没有统一的元数据，导致无法按时间、业务线、lesson、状态检索

所以解决方案不能只是“把文件名起整齐一点”，而是必须建立一套文档操作系统。

## 2. 文档层级

从今天开始，所有业务文档按以下层级管理。

### L0：当前唯一真相

定义：

- 当前阶段只允许有 1 份
- 冲突时优先级最高
- 用来回答“这一轮到底做什么，不做什么”

规则：

- 永远只有一个活跃文档
- 如果要替换，必须显式写明 `supersedes`

目录：

- `docs/10_truth/`

### L1：产品总纲

定义：

- 用来回答“这个产品到底是什么，不是什么”
- 是高于具体 lesson 的长期总纲

规则：

- 同一时期只保留 1 份主总纲
- 其他类似文档只能作为补充参考

目录：

- `docs/10_truth/`

### L2：战略与边界文档

定义：

- 支撑 L0 / L1 的策略、世界观边界、阶段约束

规则：

- 可以多份，但必须标清作用域
- 不能冒充 L0

目录：

- `docs/20_strategy/`

### L3：流程与治理文档

定义：

- workflow
- RACI
- 模板
- SOP
- Codex 执行规则

规则：

- 这些文档定义“怎么生产”
- 不能替代产品真相本身

目录：

- `docs/30_workflows/`
- `docs/50_execution/`
- `docs/60_reference/`

### L4：lesson 规格文档

定义：

- 具体到某一节的 brief、结构卡、技术骨架、卡片集合

规则：

- 必须按 lesson 归档
- 不允许再散落在根目录

目录：

- `docs/40_lessons/<lesson_id>/`

### L5：执行包

定义：

- 给团队和 Codex 的正式执行输入

补充：

- 共享执行规范放全局 `docs/50_execution/`
- 某个 lesson 专属的执行安排和执行包，优先放进该 lesson 工作区自己的 `execution/`

规则：

- 必须引用上游文档版本
- 必须写清“冻结输入”和“不做项”

目录：

- `docs/50_execution/`

### L6：过程记录

定义：

- 闸门审查
- 打回记录
- 工作日志
- 决策记录

规则：

- 一律带日期
- 一律进记录目录
- 不允许散落成“某某补充说明 final v2”

目录：

- `docs/03_records/`

### L9：归档

定义：

- 已被替代、仅保留追溯价值的文档

规则：

- 不再作为当前真相
- 必须保留来源说明

目录：

- `docs/99_archive/`
- 以及现有的 `archive/`

## 3. 新目录怎么用

在全局目录层级之外，再补一条“工作区规则”：

### Active Workspace：当前开发工作区

定义：

- 任何正在集中开发的对象，都应该有一个自己的工作区
- 当前例如：`docs/40_lessons/lesson_01/`

工作区不是新的 truth level，而是某个 scope 的协作壳层。

工作区至少包含四个控制文件：

1. `README.md`
2. `NOW.md`
3. `TIMELINE.md`
4. `DOC_INDEX.md`

这四个文件分别回答：

- 这个工作区是什么
- 现在正在做什么
- 这一路怎么走到今天
- 这里都有哪些文档

对于一个正在开发的 lesson，团队日常应该主要停留在这个工作区里，而不是在全局目录来回跳。

### `docs/10_truth/`

只放：

- 当前唯一真相
- 当前产品总纲

### `docs/20_strategy/`

只放：

- 战略文档
- 世界观边界
- 阶段定义

### `docs/30_workflows/`

只放：

- 串行 workflow
- RACI
- 模板
- SOP

### `docs/40_lessons/<lesson_id>/`

只放该 lesson 的：

- brief
- 卡片
- 结构稿
- 技术骨架
- lesson 专属执行包
- lesson 专属记录

推荐工作区结构：

```text
docs/40_lessons/lesson_01/
  README.md
  NOW.md
  TIMELINE.md
  DOC_INDEX.md
  lesson_01_brief.md
  lesson_01_minimum_unified_skeleton.md
  execution/
  records/
  archive/
```

### `docs/50_execution/`

只放：

- 共享执行规范
- 跨 lesson 通用的执行约束

### `docs/03_records/`

只放：

- 闸门审查记录
- 每日工作日志
- 决策记录

补充规则：

- `docs/03_records/` 更适合放公司级、治理级记录
- lesson 专属记录优先放到该 lesson 工作区自己的 `records/`

### `docs/98_inbox/`

只放：

- 还没定级的临时草稿

规则：

- 进入 inbox 后 48 小时内必须被清理到正式位置或删除

## 4. 命名规则

### 4.1 活文

活文文件名保持稳定，不强制带日期。

例如：

- `current_single_truth.md`
- `task_adventure_master_outline.md`
- `lesson_01_brief.md`

### 4.2 记录文档

记录类文档必须带日期，统一格式：

```text
YYYY-MM-DD__track__scope__topic.md
```

例如：

- `2026-03-25__lesson_01__gate_a__review.md`
- `2026-03-25__lesson_01__worklog__system_modeling.md`
- `2026-03-25__ceo__decision__default_error_chain.md`

## 5. 元数据规则

从现在开始，每份新增文档都必须带头部元数据。

最小字段：

```yaml
---
doc_id:
title:
doc_type:
status:
truth_level:
role_owner:
human_owner:
business_line:
scope:
created_at:
last_reviewed_at:
source_of_truth:
supersedes:
superseded_by:
related_docs:
tags:
---
```

字段解释：

- `doc_id`：唯一标识
- `doc_type`：如 `single_truth` / `master_outline` / `workflow` / `lesson_brief`
- `status`：如 `active_canonical` / `active_reference` / `working` / `archived`
- `truth_level`：`L0-L9`
- `role_owner`：这份文档按职责归谁管
- `human_owner`：当前由谁维护；不知道就先写 `TBD`
- `business_line`：如 `greek_mvp`
- `scope`：如 `company` / `chapter_01` / `lesson_01`
- `source_of_truth`：`true` 或 `false`

## 6. 生命周期规则

每份文档只允许走这条路径：

```text
inbox 草稿
-> 正式活文或正式记录
-> 被替代
-> 归档
```

禁止以下行为：

1. 活文和记录混写在同一份里
2. 被替代后继续装作当前真相
3. 根目录继续新增文档
4. 打回记录只存在聊天里、不落文档
5. 会议只讨论，不留下标准记录

## 7. 工作区状态规则

对于一个正在推进的 lesson 或业务线，建议统一使用以下状态：

1. `active_design_and_spec`
2. `frozen_for_execution`
3. `implemented_graybox`
4. `validated`
5. `archived_or_reused`

这些状态应写在该工作区的 `NOW.md` 和 `README.md` 中。

## 8. 谁写的、谁拍板，今后怎么解决

历史文档的作者信息，目前无法可靠自动回溯。

所以分两步处理：

### 对历史文档

- `human_owner` 先统一标记为 `TBD`
- 由后续人工补齐

### 对新文档

必须明确：

1. `role_owner`
2. `human_owner`
3. `approved_by`
4. `created_at`
5. `last_reviewed_at`

如果缺这些字段，文档不能算正式进入系统。

## 9. 版本控制要求

只靠文件夹管理，无法可靠回答“谁改了什么”。

因此这套文档系统要真正成立，还必须配合版本控制：

1. 文档目录纳入 Git
2. 每次重要改动有 commit
3. commit 信息说明改动范围
4. 关键拍板文档必须在提交前后都能追溯

如果没有 Git，历史追踪只能依赖：

- 文件修改时间
- 文档头部 `human_owner`
- 单独的决策记录

这只能部分止血，不能替代真正版本历史。

## 10. 如何按时间、任务、业务线检索

以后检索统一走三步：

1. 先看 [NOW.md](/Users/lijiabo/MindForge/docs/NOW.md)，确认当前活跃工作区
2. 再进该工作区的 `DOC_INDEX.md` / `NOW.md`
3. 全局真相与优先级问题，再查 [document_registry.md](/Users/lijiabo/MindForge/docs/01_registry/document_registry.md)
4. 过程问题优先去该工作区 `records/`，公司级记录再去 `docs/03_records/`

因此：

- 看当前真相，不靠猜文件名
- 看某次打回，不靠翻聊天
- 看某条业务线，不靠根目录肉眼扫描
- 看当前开发现场，先看工作区，不先扫全仓库

## 11. 立即生效的硬规则

从现在开始：

1. 根目录停止新增 `.md`
2. 当前真相与总纲的判断，以登记册为准
3. 闸门审查必须写进 `docs/03_records/gate_reviews/`
4. 每次关键拍板必须写进 `docs/03_records/decision_logs/`
5. 每条工作流的日常推进必须写进 `docs/03_records/worklogs/`

补充：

6. 当前活跃 lesson 的日常记录优先写进 lesson 工作区自己的 `records/`
7. lesson 专属执行包优先放进该 lesson 工作区的 `execution/`

## 12. 这套系统先怎么落地

本轮不先大搬家，先做三件事：

1. 建立文档登记册
2. 冻结根目录新增
3. 后续新文档只进 `docs/`

等第一轮稳定后，再按迁移清单把现有根目录文档分批迁入新结构。
