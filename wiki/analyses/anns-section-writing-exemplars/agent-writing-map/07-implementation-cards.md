---
id: anns-section-agent-map-implementation
type: analysis
status: active
created: 2026-05-27
updated: 2026-05-27
tags: [anns, paper-writing, implementation, agent-map]
source_count: 3
sources:
  - raw/sources/papers/spfresh-2023.pdf
  - raw/sources/papers/milvus-2021.pdf
  - raw/sources/papers/gustann-2025.pdf
related:
  - anns-section-agent-writing-map
confidence: medium
---

# Implementation Cards

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
