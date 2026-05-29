---
id: anns-section-agent-map-architecture
type: analysis
status: active
created: 2026-05-27
updated: 2026-05-29
tags: [anns, paper-writing, architecture, system-overview, agent-map]
source_count: 5
sources:
  - raw/sources/papers/milvus-2021.pdf
  - raw/inbox/chameleon-ralm-vector-search-vldb-best-scalable-data-science-2025.pdf
  - raw/sources/papers/spfresh-2023.pdf
  - raw/sources/papers/fusionanns-2025.pdf
  - raw/sources/papers/starling-2024.pdf
related:
  - anns-section-agent-writing-map
confidence: medium
---

# System Overview / Architecture Cards

## Current Top 5 Card Index

This index is authoritative for the current architecture ranking. The detailed cards below are retained as expanded style notes; if they conflict with this index or [Architecture Ranking](../system-overview-architecture.md), follow the ranking.

| Rank | Paper | Use when | Writing move to copy | Do not copy |
|---|---|---|---|---|
| 1 | Milvus | Full vector database or broad end-to-end system architecture. | Anchor modules in user-facing requirements before showing internals. | Do not copy the breadth for a narrow index paper. |
| 2 | Chameleon | Heterogeneous or disaggregated retrieval-serving architecture. | Show how request flow, compute placement, and memory placement interact. | Do not use if hardware placement is not central to the contribution. |
| 3 | SPFresh | Systems with foreground serving and background maintenance. | Make every component exist because of freshness, latency, or correctness. | Do not copy the split without a real asynchronous maintenance path. |
| 4 | FusionANNS | Multi-tier CPU/GPU/SSD search systems. | Explain architecture as data placement plus computation placement. | Do not draw tiers without reasoning about tier-crossing costs. |
| 5 | Starling | Segment-level disk index systems. | Keep the architecture constrained to the unit where the design operates. | Do not inflate a segment-level mechanism into a full database architecture. |

## Legacy Detailed Cards

The detailed cards below predate the Top 5 refresh. They are still useful for studying writing moves, but they are not a complete or current ranking.

## Milvus - Section 2 System Design

Source pointer: [Milvus source note](../../../source-notes/milvus-2021.md); raw PDF Section 2, "SYSTEM DESIGN".

Use when writing: architecture for a full vector database or broad end-to-end system.

Section role: show the reader how query processing, storage, dynamic data, heterogeneous computing, and distribution fit into one system.

Argument skeleton:

1. Start from user-facing capabilities and system requirements.
2. Decompose the system into query processing, index management, storage, compute, and distribution.
3. Explain dynamic data and consistency at the architecture level.
4. Defer detailed optimizations to later sections.

Reusable writing move: Milvus anchors architecture in product requirements instead of only showing internal modules.

Do not copy: the broad module list for a narrow index paper. Reviewers will see it as scope inflation.

## SPFresh - Section 4.1 Overall Architecture

Source pointer: [SPFresh source note](../../../source-notes/spfresh-2023.md); raw PDF Section 4.1, "Overall Architecture".

Use when writing: architecture for a system with foreground serving and background maintenance.

Section role: show how the update protocol becomes a running system with an updater, rebuilder, and storage controller.

Argument skeleton:

1. Introduce the foreground update/search path.
2. Introduce the background local rebuilder.
3. Introduce the block controller as the storage abstraction.
4. Explain how the components avoid putting heavy rebuild work on the critical path.

Reusable writing move: each component exists because of a specific freshness or performance requirement.

Do not copy: the foreground/background split unless your system has a real asynchronous maintenance path.

## FusionANNS - Section 3 FusionANNS Design

Source pointer: [FusionANNS source note](../../../source-notes/fusionanns-2025.md); raw PDF Section 3, "FusionANNS Design".

Use when writing: architecture for multi-tier CPU/GPU/SSD vector search.

Section role: map data placement and computation placement across SSD, CPU memory, and GPU HBM.

Argument skeleton:

1. State which data lives on SSD, CPU memory, and GPU memory.
2. Explain the coarse filtering path.
3. Explain the reranking/refinement path.
4. Explain how deduplication reduces redundant I/O.
5. Tie the placement decisions to memory capacity and throughput constraints.

Reusable writing move: FusionANNS makes architecture about tier placement, not just boxes.

Do not copy: the multi-tier diagram style unless the paper can quantify or reason about tier-crossing costs.
