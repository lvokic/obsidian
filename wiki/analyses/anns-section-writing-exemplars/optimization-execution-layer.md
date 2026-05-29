---
id: anns-section-exemplars-optimization-execution-layer
type: analysis
status: active
created: 2026-05-29
updated: 2026-05-29
tags: [anns, paper-writing, optimization, simd, vectorization, implementation]
source_count: 8
sources:
  - raw/sources/papers/pq-fast-scan-2015.pdf
  - raw/inbox/warp-multi-vector-retrieval-sigir-best-paper-2025.pdf
  - raw/inbox/chameleon-ralm-vector-search-vldb-best-scalable-data-science-2025.pdf
  - raw/sources/papers/milvus-2021.pdf
  - raw/inbox/flash-graph-indexing-2025.pdf
  - raw/sources/papers/quicker-adc-2019.pdf
  - raw/sources/papers/symphonyqg-2024.pdf
  - raw/sources/papers/gustann-2025.pdf
related:
  - anns-section-writing-exemplars
  - simd-vectorization-anns-implementation-map
confidence: medium
---

# Optimization / Execution-Layer Exemplars

## Top Five

| Rank | Paper | Score | Why it works | Weakness |
|---|---:|---:|---|---|
| 1 | [PQ Fast Scan](../../source-notes/pq-fast-scan-2015.md) | 9.4 | Best pure optimization story: it proves cache locality is not enough, identifies table lookup as the bottleneck, then redesigns layout for SIMD in-register lookup. | Narrowly focused on scan-style PQ/ADC. |
| 2 | [WARP](../../source-notes/warp-multi-vector-retrieval-2025.md) | 9.3 | Best retrieval-engine execution story: missing-similarity imputation, implicit decompression, and two-stage score reduction are tied to measured latency bottlenecks. | Not a SIMD paper yet; SIMD/GPU acceleration is future work. |
| 3 | [Chameleon](../../source-notes/chameleon-ralm-vector-search-2024.md) | 9.1 | Best accelerator execution story: CPU/GPU PQ-scan limits motivate near-memory PQ decoding, pipelined distance evaluation, and approximate hierarchical priority queues. | FPGA/disaggregation assumptions are not portable to ordinary CPU/GPU vector DB deployments. |
| 4 | [Milvus](../../source-notes/milvus-2021.md) | 9.0 | Best vector-DB batching/cache-aware execution section: query blocks reuse database vectors and avoid one-query-per-thread cache waste. | The optimization is embedded in a broad DBMS paper, so the section is less surgical than PQ Fast Scan or WARP. |
| 5 | [Flash Graph Indexing](../../source-notes/flash-graph-indexing-2025.md) | 8.9 | Best graph-construction optimization story: compact codes, table lookup, codeword colocation, and SIMD are tied to HNSW build-time random-access bottlenecks. | It is construction-time optimization and still a less stable template than published systems papers. |

## Strong Honorable Mentions

[Quicker ADC](../../source-notes/quicker-adc-2019.md) is technically deeper than PQ Fast Scan on AVX-512 and irregular product quantizers, but PQ Fast Scan is cleaner as a prose template.

[SymphonyQG](../../source-notes/symphonyqg-2024.md) is the best graph-search-plus-FastScan source, but its optimization story depends on several interacting components: RaBitQ, neighbor-code duplication, implicit reranking, graph degree alignment, and construction-time FastScan.

[GustANN](../../source-notes/gustann-2025.md) is stronger for hardware/system characterization than for a compact optimization-section template.

## What To Steal

Start optimization sections with a bottleneck that survives naive fixes. PQ Fast Scan is strong because it first rejects the easy answer: fitting lookup tables in cache is still insufficient.

Tie each optimization to a data-layout or control-flow change. SIMD and batching are consequences of layout, not just implementation flags.

Separate micro-optimization from end-to-end effect. A reviewer needs to know whether the improvement accelerates candidate scan, graph traversal, graph construction, reranking, filtering, or scheduling.

## What Not To Copy

Do not claim vectorization without naming the stage and ISA-sensitive execution path.

Do not present cache-aware batching as universally better; it can trade latency for throughput or depend on batch size.

Do not use GPU batching papers as CPU SIMD evidence. They can motivate locality and fusion, but they are not the same execution model.
