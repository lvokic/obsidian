---
id: anns-section-exemplars-motivation-characterization
type: analysis
status: active
created: 2026-05-26
updated: 2026-05-29
tags: [anns, paper-writing, motivation, characterization]
source_count: 5
sources:
  - raw/sources/papers/gustann-2025.pdf
  - raw/inbox/chameleon-ralm-vector-search-vldb-best-scalable-data-science-2025.pdf
  - raw/inbox/warp-multi-vector-retrieval-sigir-best-paper-2025.pdf
  - raw/sources/papers/odinann-2026.pdf
  - raw/sources/papers/starling-2024.pdf
related:
  - anns-section-writing-exemplars
confidence: medium
---

# Motivation / Characterization Exemplars

## Top Five

| Rank | Paper | Score | Why it works | Weakness |
|---|---:|---:|---|---|
| 1 | [GustANN](../../source-notes/gustann-2025.md) | 9.5 | Best hardware-to-system motivation. It makes CPU bottlenecks, SSD bandwidth, GPU parallelism, and transfer selectivity part of one argument. | The latency-throughput tradeoff needs to be stated early because the design is not for every workload. |
| 2 | [Chameleon](../../source-notes/chameleon-ralm-vector-search-2024.md) | 9.4 | Best service-level hardware motivation. It separates LLM inference from vector retrieval, quantifies CPU/GPU PQ-scan limits, and uses shifting RALM bottlenecks to justify disaggregation. | The argument depends on IVF-PQ and RALM retrieval frequency, so it should not be generalized to all ANN workloads. |
| 3 | [WARP](../../source-notes/warp-multi-vector-retrieval-2025.md) | 9.3 | Best pipeline-latency characterization. It profiles PLAID and XTR, isolates token retrieval/decompression/scoring bottlenecks, and makes the later engine design feel forced. | It targets multi-vector retrieval and CPU serving, not single-vector ANN indexes. |
| 4 | [OdinANN](../../source-notes/odinann-2026.md) | 9.2 | It characterizes buffered-insert interference, memory pressure, latency fluctuation, and weak batching benefit before proposing direct insert. | The characterization is compelling but locked to SSD-resident dynamic graph indexes. |
| 5 | [Starling](../../source-notes/starling-2024.md) | 9.1 | It reduces disk graph inefficiency to poor locality and long search paths, then maps that to block shuffling and in-memory routing. | It is I/O-locality motivation, not a general systems characterization. |

## What To Steal

Make the bottleneck measurable before proposing the design. GustANN and Starling are persuasive because the reader can see exactly why the later mechanism exists.

Separate resource limits. Memory capacity, I/O bandwidth, random access, GPU occupancy, host-device transfer, and update freshness are not the same problem.

Use characterization figures to eliminate alternatives, not just to decorate the paper.

The lower two slots are still strong but narrower: OdinANN is the dynamic-update motivation model, while Starling is the disk-I/O-locality motivation model.

## What Not To Copy

Do not claim that a new hardware tier is automatically useful. Show which access pattern makes it useful.

Do not motivate a throughput system using only latency-critical examples. GustANN is honest later about the throughput-latency tradeoff; a new paper should expose that scope earlier.

Do not use microbenchmarks unless they predict a design decision.
