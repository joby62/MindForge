---
doc_id: execution.next_arrangement
title: 接下来执行安排
doc_type: execution_plan
status: active_working
truth_level: L5
role_owner: CEO / 产品总负责人
human_owner: Codex
approved_by:
business_line: greek_mvp
scope: lesson_01
created_at: 2026-03-25
last_reviewed_at: 2026-03-25
source_of_truth: true
supersedes: []
superseded_by: []
related_docs:
  - /Users/lijiabo/MindForge/docs/10_truth/current_single_truth.md
  - /Users/lijiabo/MindForge/docs/40_lessons/lesson_01/lesson_01_brief.md
  - /Users/lijiabo/MindForge/docs/40_lessons/lesson_01/execution/serial_execution_pack.md
tags:
  - execution
  - lesson_01
  - working
---

# 接下来执行安排

版本：v0.1  
日期：2026-03-25  
定位：根据 CEO 最新“8 元老串行 + 3 个闸门”口径，为当前项目给出下一步统一执行安排

## 1. 先确认当前项目处在哪

根目录文档显示，当前项目已经有三层材料：

1. 顶层事实源已经锁定
2. 8 元老串行 workflow 已经成文
3. Lesson 01 技术骨架已经提前推进到“供拍板”状态

当前真正应该做的，不是继续扩世界，也不是直接进入自由实现，而是：

`把第一节按 8 元老串行链正式跑完，过完 3 个闸门，再由技术 Owner 整包交给 Codex。`

## 2. 本轮执行时的文档优先级

本轮先按以下顺序认定单一事实源：

1. `current_single_truth.md`
2. `vibe_coding_for_kids_strategy.md`
3. `mvp_world_setup.md`
4. `lesson_01_brief.md`
5. `elders_serial_workflow.md`
6. `single_lesson_templates.md`
7. `lesson_01_minimum_unified_skeleton.md`

说明：

- 前 4 份文档定义“这轮到底做什么”
- 第 5、6 份文档定义“怎么串行生产”
- 第 7 份文档只视为技术候选骨架，不视为最终已冻结方案

在相关文档完成修订前，本安排优先于旧版 `weekly_operating_sop.md` 与 `ceo_process_map.md` 中较早形成的周会顺序与技术闸门位置。

## 3. 本轮冻结项

从现在开始，以下内容直接冻结，不再重新发散：

1. 当前只做希腊神话 MVP / 第一章 / 第一节
2. 第一节类型固定为“修补裂缝节”
3. 第一节系统对象固定为“初火祭坛稳焰系统”
4. 主交互关系固定为“孩子 <-> 小精灵”
5. 世界观大使本轮已交付的 4 件套，统一以 `lesson_01_brief.md` 为准

这意味着：

- 不再开新的世界观脑暴
- 不再补大反派长线
- 不再先做大地图或多地点切换
- 不再让技术 Owner 从第 1 棒开始主导内容

## 4. 第一节的正式跑法

### 0. 世界观大使输入冻结

直接采用 `lesson_01_brief.md` 作为世界观大使的上游输入包，内容包括：

1. 小精灵设定卡
2. 灰烬拨针者设定卡
3. 第一节开场钩子草案
4. 世界语言与禁用表达

不要求世界观大使继续扩写，只允许在元老 1-3 期间被咨询。

### 1. 元老 1-3 串行

顺序固定：

1. 节目标官
2. 戏剧钩子官
3. 系统建模官

本阶段目标：

- 把第一节从“世界设定”压成“目标 + 开场 + 系统对象”

本阶段必须产出：

1. 节目标卡
2. 进入钩子卡
3. 系统结构卡

### 2. 闸门 A

审查人：

- CEO / 产品总负责人
- 技术集成 Owner

只审三件事：

1. 这节目标是否清楚
2. 开场是否能在 2 分钟内抓住孩子
3. 系统是否已经是可运行对象

不过则打回 1-3 棒，不进入错误和交互设计。

### 3. 元老 4-5 串行

顺序固定：

4. 错误反馈官
5. 交互路径官

本阶段目标：

- 把系统变成真实可调试体验

本阶段必须产出：

4. 错误设计卡
5. 交互流程卡

补充原则：

- 错误官不能替孩子写答案
- 交互官不能把整节做成一路点完
- `lesson_01_minimum_unified_skeleton.md` 里的 runtime / action / error / evidence 结构，只能作为候选支撑，不自动视为已拍板正文

### 4. 闸门 B

审查人：

- 技术集成 Owner

只审三件事：

1. 错误是否可观测、可分类、可缩小范围
2. 交互是否支持“对话 -> 修改 -> 运行 -> 重跑”
3. 是否出现状态爆炸、命名漂移或实现失控风险

本关通过后，再允许把技术骨架和卡片内容合并成 Codex 规格包。

### 5. 元老 6-7 串行

顺序固定：

6. 认知校验官
7. 家长证据官

本阶段目标：

- 确认这节练的真是思维，不是剧情体验
- 确认家长端价值能被一句话讲清

本阶段必须产出：

6. 主轴校验卡
7. 家长证据卡

### 6. 闸门 C

审查人：

- CEO / 产品总负责人

只审两件事：

1. 这节是否真的在练目标能力
2. 家长是否能一句话看懂价值

不过则不进入模板沉淀，也不进入实现。

### 7. 元老 8 收束

第 8 棒只做：

1. 模板归档卡
2. 复用项提炼
3. 坑位记录
4. 下一节可继承资产记录

第 8 棒不继续发明剧情，不重写前 7 张卡。

### 8. 技术 Owner 整包

只有在闸门 C 通过之后，技术集成 Owner 才开始：

1. 合并 8 张卡中的执行必需信息
2. 把 `lesson_01_minimum_unified_skeleton.md` 转成正式执行包
3. 明确统一 runtime、error taxonomy、evidence schema
4. 补齐 Codex 输入封面
5. 标注本轮允许 hardcode 与禁止 hardcode 的边界

### 9. 交 Codex / 工程

交付给 Codex 的最小执行包至少包含：

1. 节目标卡
2. 系统结构卡
3. 错误设计卡
4. 交互流程卡
5. 成功标准卡
6. 主轴校验卡
7. 家长证据卡
8. 技术红线说明

## 5. 每一棒统一交接格式

从本轮开始，8 元老统一按以下格式交棒：

```text
本轮新增卡：

我确认可继续的部分：

我发现的风险：

是否建议打回上一环节：是 / 否

给下一位的重点提醒：
```

硬规则：

1. 下一位不能直接改上一位正文
2. 只能继续写自己的卡
3. 只能标风险或申请打回
4. 两条以上合理路径并且会影响产品方向时，必须上报，不自行拍板

## 6. 这一周的实际安排

建议按下面的工作块推进，而不是先开旧式大周会。

### 工作块 A：今天

完成事项：

1. 冻结本安排
2. 指定本轮 8 个功能位负责人
3. 明确谁担任 CEO 审查、谁担任技术 Owner 审查
4. 以 `lesson_01_brief.md` 作为唯一上游输入包开跑

### 工作块 B：接下来 0.5-1 天

完成元老 1-3 串行，立即过闸门 A。

### 工作块 C：闸门 A 通过后 0.5-1 天

完成元老 4-5 串行，立即过闸门 B。

### 工作块 D：闸门 B 通过后 0.5 天

完成元老 6-7 串行，立即过闸门 C。

### 工作块 E：闸门 C 通过后 0.5 天

元老 8 做模板沉淀，技术 Owner 生成 Codex 执行包。

### 工作块 F：最后 1-2 天

Codex / 工程只做灰盒闭环：

1. 对话驱动第一次判断
2. 至少两类错误暴露
3. 至少一次修改后运行
4. 至少一次重跑
5. 家长证据自动生成

## 7. 当前必须先拍板的三件技术分歧

`lesson_01_minimum_unified_skeleton.md` 已经提前提出 3 个分歧点。为了避免技术层提前替产品拍板，本轮建议这样处理：

1. 对话翻译链默认采用“受控槽位翻译”
2. 第一节默认错误链先走 `seal_condition_unmet -> oxygen_boundary_unstable`
3. 家长证据默认采用“过程流式沉淀”

这三项都先作为闸门 B 前的推荐默认值；如果 CEO 有异议，再在对应闸门拍板，不让工程侧自行改道。

## 8. 本安排执行后的下一个文档动作

在第一节串行链正式跑完后，再做以下文档修订：

1. 更新 `weekly_operating_sop.md`
2. 更新 `ceo_process_map.md`
3. 视需要补一版带闸门的模板包

顺序上先跑通第一节，再统一修订旧文档，避免再次陷入“先写流程图、后跑生产”的空转。

本安排对应的可执行发令材料，见 [serial_execution_pack.md](/Users/lijiabo/MindForge/docs/40_lessons/lesson_01/execution/serial_execution_pack.md)。
