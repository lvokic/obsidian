---
id: anns-section-agent-map-design
type: analysis
status: active
created: 2026-05-27
updated: 2026-05-29
tags: [anns, paper-writing, design, algorithms, agent-map]
source_count: 6
sources:
  - raw/sources/papers/starling-2024.pdf
  - raw/inbox/warp-multi-vector-retrieval-sigir-best-paper-2025.pdf
  - raw/sources/papers/spfresh-2023.pdf
  - raw/sources/papers/odinann-2026.pdf
  - raw/inbox/integrating-vector-databases-across-embedding-models-sigmod-hm-2026.pdf
  - raw/sources/papers/vbase-2023.pdf
related:
  - anns-section-agent-writing-map
confidence: medium
---

# Core Design / Algorithms Cards

## Current Top 5 Card Index

This index is authoritative for the current method/core-design ranking. The detailed cards below are retained as expanded style notes; if they conflict with this index or [Method Ranking](../core-design-algorithms.md), follow the ranking.

| Rank | Paper | Use when | Writing move to copy | Do not copy |
|---|---|---|---|---|
| 1 | Starling | Layout-plus-search designs for disk-resident ANNS. | Preserve a one-to-one mapping from diagnosed problem factors to mechanisms. | Do not add mechanisms without making their target bottleneck explicit. |
| 2 | WARP | Compressed scoring, implicit decompression, and multi-vector execution. | Explain the execution trick at the same granularity as the bottleneck it removes. | Do not use if the method is not primarily an execution-layer redesign. |
| 3 | SPFresh | Incremental maintenance, local repair, and mutable index protocols. | Present update cases as protocol invariants rather than ad hoc engineering. | Do not copy the multi-operation structure without simple invariants. |
| 4 | OdinANN | Direct-update graph ANNS. | Make the algorithm answer a specific dynamic-index failure mode. | Do not use for static graph construction. |
| 5 | Integrating Vector Databases | Data-management abstractions across embedding models. | Organize design around a reusable abstraction rather than an isolated implementation. | Do not use if the contribution is only faster search. |

## Legacy Detailed Cards

The detailed cards below predate the Top 5 refresh. They are still useful for studying writing moves, but they are not a complete or current ranking.

## Starling - Sections 3-5 Design Philosophy, Data Layout, Search Strategy

Source pointer: [Starling source note](../../../source-notes/starling-2024.md); raw PDF Sections 3-5.

Use when writing: core design for a layout-plus-search paper.

Section role: show how two diagnosed I/O problems become concrete design mechanisms.

Argument skeleton:

1. State the design philosophy through measurable I/O inefficiency.
2. Present data layout as the answer to locality waste.
3. Present an in-memory navigation graph as the answer to route-length waste.
4. Present block search as the query-time algorithm that exploits the layout.
5. Cover ANN search and range search as two uses of the same framework.

Reusable writing move: the design sections preserve a one-to-one mapping from problem factors to mechanisms.

Do not copy: adding multiple mechanisms without this one-to-one mapping.

## SPFresh - Sections 3-4 LIRE Protocol and Design/Implementation

Source pointer: [SPFresh source note](../../../source-notes/spfresh-2023.md); raw PDF Sections 3-4.

Use when writing: core design for incremental maintenance, local repair, or mutable indexes.

Section role: define the update protocol and then explain how it runs without hurting foreground search.

Argument skeleton:

1. Define the local rebalancing goal.
2. Explain split, merge, and reassignment operations.
3. State the conditions that decide whether reassignment is necessary.
4. Explain convergence or stability of the protocol.
5. Map protocol operations to the system architecture.

Reusable writing move: SPFresh treats update cases as protocol invariants rather than ad hoc engineering.

Do not copy: the many-operation structure unless the invariants are easy to state.

## VBASE - Sections 3-4 Design and Implementation

Source pointer: [VBASE source note](../../../source-notes/vbase-2023.md); raw PDF Sections 3-4.

Use when writing: core design for semantic abstraction, query execution, or database-index integration.

Section role: introduce relaxed monotonicity and show how a vector index can expose incremental results safely to query execution.

Argument skeleton:

1. Define the relaxed monotonicity property.
2. Explain how common vector indexes can satisfy or approximate it.
3. Show result equivalence relative to TopK-style execution.
4. Explain implementation hooks such as checking, execution state, and planning.

Reusable writing move: the design is organized around a property that unlocks the whole system.

Do not copy: formal property-first writing if the paper cannot later evaluate or use the property.
