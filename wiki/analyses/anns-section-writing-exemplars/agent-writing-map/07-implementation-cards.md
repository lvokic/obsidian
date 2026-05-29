---
id: anns-section-agent-map-implementation
type: analysis
status: active
created: 2026-05-27
updated: 2026-05-29
tags: [anns, paper-writing, implementation, agent-map]
source_count: 5
sources:
  - raw/sources/papers/spfresh-2023.pdf
  - raw/inbox/chameleon-ralm-vector-search-vldb-best-scalable-data-science-2025.pdf
  - raw/sources/papers/odinann-2026.pdf
  - raw/sources/papers/gustann-2025.pdf
  - raw/sources/papers/milvus-2021.pdf
related:
  - anns-section-agent-writing-map
confidence: medium
---

# Implementation Cards

## Current Top 5 Card Index

This index is authoritative for the current implementation ranking. The detailed cards below are retained as expanded style notes; if they conflict with this index or [Implementation Ranking](../implementation.md), follow the ranking.

| Rank | Paper | Use when | Writing move to copy | Do not copy |
|---|---|---|---|---|
| 1 | SPFresh | Storage engines, concurrency, recovery, and background maintenance. | Include implementation details only when they affect performance or correctness. | Do not list low-level APIs without explaining why they exist. |
| 2 | Chameleon | Service implementation across heterogeneous hardware. | Connect implementation choices to request flow and resource isolation. | Do not use if the implementation does not span serving components. |
| 3 | OdinANN | Dynamic graph update implementation. | Explain concurrency and record-level mechanisms as consequences of direct update. | Do not hide correctness details behind performance claims. |
| 4 | GustANN | GPU kernels, host-device transfer, and SSD/GPU pipelines. | Tie every kernel or pipeline detail back to a characterized bottleneck. | Do not add GPU details before proving the GPU/SSD bottleneck. |
| 5 | Milvus | Production vector database implementations. | Use implementation breadth to prove system integration. | Do not copy broad coverage for a one-subsystem contribution. |

## Legacy Detailed Cards

The detailed cards below predate the Top 5 refresh. They are still useful for studying writing moves, but they are not a complete or current ranking.

## SPFresh - Section 4 Design and Implementation

Source pointer: [SPFresh source note](../../../source-notes/spfresh-2023.md); raw PDF Section 4.

Use when writing: implementation for systems with storage engines, concurrency, recovery, or background maintenance.

Section role: prove that LIRE is implementable without damaging online service behavior.

Argument skeleton:

1. Present overall architecture.
2. Explain Local Rebuilder execution and concurrency.
3. Explain Block Controller API and raw block behavior.
4. Explain append, put, copy-on-write, versioning, and snapshots as needed.
5. Tie implementation choices back to latency, IOPS, and correctness.

Reusable writing move: implementation details are only included when they affect performance or correctness.

Do not copy: naming low-level APIs without explaining why they are needed.

## Milvus - Sections 2-5 System Implementation Path

Source pointer: [Milvus source note](../../../source-notes/milvus-2021.md); raw PDF Sections 2-5.

Use when writing: implementation for a production vector database with multiple capabilities.

Section role: demonstrate breadth and integration: APIs, indexing, storage, heterogeneous compute, advanced query processing, and distribution.

Argument skeleton:

1. Present system modules.
2. Explain CPU/GPU optimizations.
3. Explain advanced query processing.
4. Explain distributed execution and storage.
5. Tie the pieces to user-facing functionality.

Reusable writing move: Milvus uses implementation to prove that vector search is a full data management system, not just a library call.

Do not copy: broad implementation coverage if your paper's claim is only one subsystem.

## GustANN - Section 4 Design

Source pointer: [GustANN source note](../../../source-notes/gustann-2025.md); raw PDF Section 4.

Use when writing: implementation for GPU kernels, host-device transfer, and SSD/GPU pipelines.

Section role: show how graph traversal, data transfer, and load balance are implemented under GPU memory limits.

Argument skeleton:

1. Present the overview.
2. Explain memory-efficient graph traversal kernel.
3. Explain CPU-assisted selective transfer.
4. Explain load balancing with pivot search.
5. State memory-budget implications.

Reusable writing move: GustANN connects every implementation technique to a measured bottleneck from motivation.

Do not copy: GPU implementation details without first proving the CPU/GPU/SSD bottleneck.
