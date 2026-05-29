---
id: anns-section-agent-map-motivation
type: analysis
status: active
created: 2026-05-27
updated: 2026-05-29
tags: [anns, paper-writing, motivation, characterization, agent-map]
source_count: 6
sources:
  - raw/sources/papers/gustann-2025.pdf
  - raw/inbox/chameleon-ralm-vector-search-vldb-best-scalable-data-science-2025.pdf
  - raw/inbox/warp-multi-vector-retrieval-sigir-best-paper-2025.pdf
  - raw/sources/papers/odinann-2026.pdf
  - raw/sources/papers/starling-2024.pdf
  - raw/sources/papers/rummy-2024.pdf
related:
  - anns-section-agent-writing-map
confidence: medium
---

# Motivation / Characterization Cards

## Current Top 5 Card Index

This index is authoritative for the current motivation/characterization ranking. The detailed cards below are retained as expanded style notes; if they conflict with this index or [Motivation Ranking](../motivation-characterization.md), follow the ranking.

| Rank | Paper | Use when | Writing move to copy | Do not copy |
|---|---|---|---|---|
| 1 | GustANN | Hardware-assisted ANNS with GPU/SSD or throughput bottlenecks. | Separate opportunity from challenge before introducing the design. | Do not claim "GPU is faster" without showing the transfer or memory bottleneck. |
| 2 | Chameleon | RALM/vector retrieval serving systems. | Characterize service pressure across request rate, retrieval cost, and hardware placement. | Do not use if the paper lacks an end-to-end serving workload. |
| 3 | WARP | Multi-vector retrieval and compressed execution. | Turn scoring cost into a measurable execution-layer bottleneck. | Do not use multi-vector motivation for ordinary top-k vector search. |
| 4 | OdinANN | Dynamic ANNS under insert/delete workloads. | Make direct updates necessary by showing why buffering/rebuild is structurally weak. | Do not use for append-only or offline construction papers. |
| 5 | Starling | Disk graph search and I/O locality papers. | Reduce the motivation to two measurable factors: locality waste and path length. | Do not borrow disk-block logic for memory-resident designs. |

## Legacy Detailed Cards

The detailed cards below predate the Top 5 refresh. They are still useful for studying writing moves, but they are not a complete or current ranking.

## GustANN - Section 3 Motivation

Source pointer: [GustANN source note](../../../source-notes/gustann-2025.md); raw PDF Section 3, "Motivation".

Use when writing: motivation for GPU/SSD cooperation, high-throughput search, or hardware bottleneck papers.

Section role: prove that CPU-only SSD-resident ANNS leaves performance and cost efficiency on the table, while GPU acceleration creates new data-movement challenges.

Argument skeleton:

1. Show CPU limits cost-effectiveness.
2. Show GPU is attractive for ANNS parallelism.
3. Explain why naive GPU use is blocked by memory capacity and transfer behavior.
4. Convert these observations into concrete design challenges.
5. Use the motivation to justify GPU-centric, CPU-assisted execution.

Reusable writing move: GustANN separates opportunity from challenge. It does not say "GPU is faster"; it says the GPU helps only if traversal, transfer, and load balance are redesigned.

Do not copy: the throughput-first framing if your system targets strict low-latency search.

## Starling - Section 3 Design Philosophy

Source pointer: [Starling source note](../../../source-notes/starling-2024.md); raw PDF Section 3, "DESIGN PHILOSOPHY".

Use when writing: motivation for layout, locality, search-path shortening, or disk I/O reduction.

Section role: turn the problem into two measurable factors: poor data locality and long search path.

Argument skeleton:

1. Analyze I/O inefficiency of disk graph search.
2. Identify the locality waste inside loaded blocks.
3. Identify the route-length problem that causes repeated disk accesses.
4. Present the framework overview as a direct response to those factors.

Reusable writing move: the section introduces design principles before mechanisms, which makes later block shuffling and navigation graph design feel forced.

Do not copy: the disk-block framing for a memory-only or GPU-only paper.

## RUMMY - Sections 2-3 Motivation Setup

Source pointer: [RUMMY source note](../../../source-notes/rummy-2024.md); raw PDF Sections 2-3 setup around GPU acceleration and beyond-GPU-memory constraints.

Use when writing: motivation for batch query processing, host-GPU memory expansion, or pipeline scheduling.

Section role: show that large datasets exceed GPU memory and that naive transfer/computation overlap is not enough.

Argument skeleton:

1. Establish GPU acceleration as attractive for vector query processing.
2. Show that billion-scale datasets exceed GPU memory.
3. Explain why host memory expansion creates transfer bottlenecks.
4. Identify query ordering and batching as system-level optimization opportunities.
5. Prepare the reader for reordered pipelining.

Reusable writing move: RUMMY motivates the scheduler, not just the accelerator.

Do not copy: the IVF-specific assumptions unless your system also works through independent clusters/lists or batchable query units.
