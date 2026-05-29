---
id: anns-section-exemplars-implementation
type: analysis
status: active
created: 2026-05-26
updated: 2026-05-29
tags: [anns, paper-writing, implementation]
source_count: 5
sources:
  - raw/sources/papers/spfresh-2023.pdf
  - raw/inbox/chameleon-ralm-vector-search-vldb-best-scalable-data-science-2025.pdf
  - raw/sources/papers/odinann-2026.pdf
  - raw/sources/papers/gustann-2025.pdf
  - raw/sources/papers/milvus-2021.pdf
related:
  - anns-section-writing-exemplars
confidence: medium
---

# Implementation Exemplars

## Top Five

| Rank | Paper | Score | Why it works | Weakness |
|---|---:|---:|---|---|
| 1 | [SPFresh](../../source-notes/spfresh-2023.md) | 9.3 | Best implementation section because it explains SPDK/raw-block access, append/put behavior, concurrency, and recovery in terms of update correctness and performance. | It is detailed enough that poor copying would become implementation clutter. |
| 2 | [Chameleon](../../source-notes/chameleon-ralm-vector-search-2024.md) | 9.2 | Best hardware/software implementation description: LOC, Fairseq extensions, Faiss use, FPGA TCP/IP stack, CPU coordination, and message design are tied to the system boundary. | The FPGA/HLS details are not reusable for most commodity ANNS systems. |
| 3 | [OdinANN](../../source-notes/odinann-2026.md) | 9.1 | Best direct-insert implementation story: fixed-size records, overprovisioned pages, update combining, approximate concurrency control, snapshots, and journaling all support the same claim. | The storage design trades extra SSD space and writes for stability. |
| 4 | [GustANN](../../source-notes/gustann-2025.md) | 8.8 | It gives concrete GPU/SSD engineering: traversal kernels, CPU-assisted selective transfer, pivot search, memory budgeting, and batched execution. | It is too dependent on the throughput-oriented workload model; latency-critical readers need stronger caveats. |
| 5 | [Milvus](../../source-notes/milvus-2021.md) | 8.7 | It is mature about production-system implementation concerns: storage, dynamic data, heterogeneous execution, cache, and system services. | It is broad DBMS implementation prose, not a focused ANNS mechanism implementation section. |

## What To Steal

Implementation details should justify feasibility, not merely report engineering effort.

Expose concurrency, memory management, recovery, batching, and low-level I/O only when they affect correctness or measured performance.

State the hard constants that reviewers care about: memory budget per query, block size, queueing model, device interface, and what resides in CPU memory, GPU memory, SSD, or second-tier memory.

GustANN and Milvus are useful only when their scope matches the target paper. Do not borrow GustANN's GPU/SSD details for a latency-first paper or Milvus's DBMS breadth for a narrow index paper.

## What Not To Copy

Do not write "implemented in C++" as if that is a contribution.

Do not list libraries and APIs without explaining the design constraint that forced them.

Do not hide fallback paths. If the system needs asynchronous rebuild, host-side filtering, spillover, or device-specific tuning, say so.
