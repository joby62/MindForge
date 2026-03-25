---
doc_id: decision.docs_governance_baseline.2026-03-25
title: 文档治理基线决定
doc_type: decision_log
status: active_canonical
truth_level: L6
role_owner: CEO / 产品总负责人
human_owner: Codex
approved_by: CEO / 产品总负责人
business_line: company
scope: document_system
created_at: 2026-03-25
last_reviewed_at: 2026-03-25
source_of_truth: false
supersedes: []
superseded_by: []
related_docs:
  - /Users/lijiabo/MindForge/docs/00_governance/document_management_system.md
  - /Users/lijiabo/MindForge/docs/01_registry/document_registry.md
  - /Users/lijiabo/MindForge/docs/01_registry/migration_backlog.md
tags:
  - decision
  - docs
  - governance
---

决策主题：
建立文档治理基线，并停止根目录继续新增业务文档。

决策时间：
2026-03-25

提案人：
Codex

拍板人：
CEO / 产品总负责人

Path A：
继续沿用根目录散落文档，只靠人工约定“哪个更重要”。

Path B：
建立 `docs/` 文档中枢，定义文档层级、登记册、模板、记录目录和迁移清单。

最终决定：
采用 Path B。

决策原因：

1. 当前问题不是文档少，而是没有层级、没有入口、没有记录落点、没有可检索元数据。
2. 如果不先建立治理层，继续写新文档只会把混乱继续叠加。
3. 先止血、再迁移，比直接全量搬家更稳。

影响文档：

1. /Users/lijiabo/MindForge/docs/README.md
2. /Users/lijiabo/MindForge/docs/00_governance/document_management_system.md
3. /Users/lijiabo/MindForge/docs/01_registry/document_registry.md
4. /Users/lijiabo/MindForge/docs/01_registry/migration_backlog.md

后续动作：

1. 新业务文档统一进入 `docs/`
2. 根目录停止新增新的 `.md`
3. 活跃文档分批迁移到对应目录
4. 过程记录统一进入 `docs/03_records/`
