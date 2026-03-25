# 文档头模板

所有新文档都先复制这一段。

```yaml
---
doc_id: 
title: 
doc_type: 
status: active_canonical
truth_level: L3
role_owner: 
human_owner: TBD
approved_by: 
business_line: 
scope: 
created_at: YYYY-MM-DD
last_reviewed_at: YYYY-MM-DD
source_of_truth: false
supersedes: []
superseded_by: []
related_docs: []
tags: []
---
```

## 常用取值

### `doc_type`

- `single_truth`
- `master_outline`
- `strategy`
- `world_setup`
- `workflow`
- `raci`
- `template`
- `lesson_brief`
- `lesson_skeleton`
- `execution_plan`
- `execution_packet`
- `gate_review`
- `worklog`
- `decision_log`
- `archive_note`

### `status`

- `active_canonical`
- `active_reference`
- `active_reference_pending_rewrite`
- `working`
- `working_pending_approval`
- `archived`

### `truth_level`

- `L0`
- `L1`
- `L2`
- `L3`
- `L4`
- `L5`
- `L6`
- `L9`
