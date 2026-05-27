---
id: anns-section-exemplars-implementation
type: analysis
status: active
created: 2026-05-26
updated: 2026-05-26
tags: [anns, paper-writing, implementation]
source_count: 3
sources:
  - raw/sources/papers/spfresh-2023.pdf
  - raw/sources/papers/milvus-2021.pdf
  - raw/sources/papers/gustann-2025.pdf
related:
  - anns-section-writing-exemplars
confidence: medium
---

# Implementation Exemplars

## Top Three

| Rank | Paper | Score | Why it works | Weakness |
|---|---:|---:|---|---|
| 1 | [SPFresh](../../source-notes/spfresh-2023.md) | 9.3 | Best implementation section because it explains SPDK/raw-block access, append/put behavior, concurrency, and recovery in terms of update correctness and performance. | It is detailed enough that poor copying would become implementation clutter. |
| 2 | [Milvus](../../source-notes/milvus-2021.md) | 8.9 | Best production-system implementation breadth: CPU/GPU engine, storage, APIs, multi-GPU execution, and dynamic data management. | Too broad for a focused algorithmic-systems paper. |
| 3 | [GustANN](../../source-notes/gustann-2025.md) | 8.7 | Good concrete GPU/SSD engineering: traversal kernels, CPU-assisted selective transfer, pivot search, and memory budgeting. | Some details are best understood only after accepting the throughput-oriented workload model. |

## What To Steal

Implementation details should justify feasibility, not merely report engineering effort.

Expose concurrency, memory management, recovery, batching, and low-level I/O only when they affect correctness or measured performance.

State the hard constants that reviewers care about: memory budget per query, block size, queueing model, device interface, and what resides in CPU memory, GPU memory, SSD, or second-tier memory.

## What Not To Copy

Do not write "implemented in C++" as if that is a contribution.

Do not list libraries and APIs without explaining the design constraint that forced them.

Do not hide fallback paths. If the system needs asynchronous rebuild, host-side filtering, spillover, or device-specific tuning, say so.
