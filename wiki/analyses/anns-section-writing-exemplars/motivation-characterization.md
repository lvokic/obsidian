---
id: anns-section-exemplars-motivation-characterization
type: analysis
status: active
created: 2026-05-26
updated: 2026-05-26
tags: [anns, paper-writing, motivation, characterization]
source_count: 3
sources:
  - raw/sources/papers/gustann-2025.pdf
  - raw/sources/papers/starling-2024.pdf
  - raw/sources/papers/rummy-2024.pdf
related:
  - anns-section-writing-exemplars
confidence: medium
---

# Motivation / Characterization Exemplars

## Top Three

| Rank | Paper | Score | Why it works | Weakness |
|---|---:|---:|---|---|
| 1 | [GustANN](../../source-notes/gustann-2025.md) | 9.5 | Best hardware-to-system motivation. It makes CPU bottlenecks, SSD bandwidth, GPU parallelism, and transfer selectivity part of one argument. | The latency-throughput tradeoff needs to be stated early because the design is not for every workload. |
| 2 | [Starling](../../source-notes/starling-2024.md) | 9.3 | Best I/O characterization. It reduces disk graph inefficiency to poor locality and long search paths, then maps those directly to block shuffling and in-memory routing. | The argument is strongest for disk-resident graph search, not all ANNS. |
| 3 | [RUMMY](../../source-notes/rummy-2024.md) | 8.8 | Best beyond-GPU-memory motivation. It turns host-device transfer, GPU utilization, and query ordering into a coherent pipeline problem. | It depends heavily on IVF and batch/pipeline assumptions. |

## What To Steal

Make the bottleneck measurable before proposing the design. GustANN and Starling are persuasive because the reader can see exactly why the later mechanism exists.

Separate resource limits. Memory capacity, I/O bandwidth, random access, GPU occupancy, host-device transfer, and update freshness are not the same problem.

Use characterization figures to eliminate alternatives, not just to decorate the paper.

## What Not To Copy

Do not claim that a new hardware tier is automatically useful. Show which access pattern makes it useful.

Do not motivate a throughput system using only latency-critical examples. GustANN is honest later about the throughput-latency tradeoff; a new paper should expose that scope earlier.

Do not use microbenchmarks unless they predict a design decision.
