---
id: simd-vectorization-anns-implementation-map
type: analysis
status: active
created: 2026-05-27
updated: 2026-05-27
tags: [anns, simd, vectorization, batch-execution, implementation, agent-map]
source_count: 20
sources:
  - raw/sources/papers/pq-fast-scan-2015.pdf
  - raw/sources/papers/quicker-adc-2019.pdf
  - raw/sources/papers/symphonyqg-2024.pdf
  - raw/inbox/flash-graph-indexing-2025.pdf
  - raw/inbox/panorama-2025.pdf
  - raw/sources/papers/low-precision-quantization-knn-2021.pdf
  - raw/sources/papers/fastlanes-2023.pdf
  - raw/sources/papers/simd-investments-2020.pdf
  - raw/sources/papers/compiled-vectorized-queries-2018.pdf
  - raw/sources/papers/rethinking-simd-vectorization-2015.pdf
  - raw/sources/papers/simd-posting-list-decoding-2011.pdf
  - raw/sources/papers/simd-compression-intersection-2014.pdf
  - raw/sources/papers/stream-vbyte-2017.pdf
  - raw/sources/papers/milvus-2021.pdf
  - raw/sources/papers/faiss-gpu-2017.pdf
  - raw/sources/papers/faiss-library-2025.pdf
  - raw/sources/papers/rummy-2024.pdf
  - raw/sources/papers/gustann-2025.pdf
  - raw/sources/papers/fusionanns-2025.pdf
  - raw/sources/papers/scann-2020.pdf
related:
  - simd-and-vectorization-for-ann-systems
  - scalar-and-binary-quantization-for-ann
  - anns-section-writing-exemplars
confidence: medium
---

# Agent Map: SIMD, Vectorization, and Batch Execution for ANNS Implementation

This is the specialized entry point for writing a technical chapter on SIMD/vectorization and batch execution in ANNS systems.

The core message for the chapter should be blunt: vectorization is not a compiler flag. In ANNS, vectorization only works when the data layout, candidate batch shape, quantized representation, and search control flow are co-designed.

## How Future Agents Should Use This Map

1. Read this map first.
2. Decide which technical path the user's chapter needs: PQ/ADC scan, scalar/int8 distance, graph traversal, graph construction, exact reranking, filters/list processing, or batch query scheduling.
3. Read the original paper sections listed below before reading summaries. The point is to learn how the papers explain low-level implementation mechanisms.
4. Read [Paper Evaluation](paper-evaluation.md) to choose which papers deserve central treatment.
5. Read [Chapter Blueprint](chapter-blueprint.md) to build the user's section.
6. Keep terminology strict: do not conflate SIMD, vectorized execution, query batching, GPU SIMT, and multi-threading.

## Original Reading Targets

| Technical need | Read first | Why |
|---|---|---|
| Explain SIMD for PQ/ADC | `raw/sources/papers/pq-fast-scan-2015.pdf`, Sections 1-3 | Best explanation of why cache locality is insufficient and why in-register lookup matters. |
| Explain modern SIMD ADC implementation | `raw/sources/papers/quicker-adc-2019.pdf`, Introduction and Background | Best bridge from FastScan to AVX-512, irregular subquantizer widths, split tables, and FAISS integration. |
| Explain batch/cache-aware vector search | `raw/sources/papers/milvus-2021.pdf`, Section 3.2 | Best ANNS system section for query batching as cache reuse and SIMD-aware runtime dispatch. |
| Explain graph search plus SIMD | `raw/sources/papers/symphonyqg-2024.pdf`, Sections 2.2 and 3 | Best current graph-ANN example of FastScan/RaBitQ, neighbor-code colocation, and batch-aligned graph degree. |
| Explain graph construction vectorization | `raw/inbox/flash-graph-indexing-2025.pdf`, profiling and design sections | Best source for build-time compact codes, SIMD table lookup, and random-access reduction in HNSW construction. |
| Explain vectorized execution vs batching | `raw/sources/papers/compiled-vectorized-queries-2018.pdf`, SIMD and execution-model sections | Best conceptual source for vector-at-a-time execution and why batch primitives make SIMD easier. |
| Explain divergence in irregular search | `raw/sources/papers/simd-investments-2020.pdf`, Sections 3-5 | Best warning source for control-flow divergence and lane refill under irregular branches. |
| Explain SIMD-friendly compressed layout | `raw/sources/papers/fastlanes-2023.pdf`, Sections 1-2 | Best source for the idea that layout, not only instructions, exposes SIMD parallelism. |
| Explain filter/list paths | `raw/sources/papers/stream-vbyte-2017.pdf` and `raw/sources/papers/simd-compression-intersection-2014.pdf` | Useful when the chapter discusses metadata filters, posting lists, IDs, or graph adjacency lists. |
| Explain batch GPU analogy | `raw/sources/papers/faiss-gpu-2017.pdf`, Sections 3-5; `raw/sources/papers/rummy-2024.pdf`, Design | Use only as GPU/SIMT and batching analogies, not CPU SIMD evidence. |

## Technical Taxonomy

| Term | Meaning in this chapter | Do not confuse with |
|---|---|---|
| SIMD | One CPU instruction operates over multiple lanes in a vector register. | Multi-threading or GPU kernels. |
| Vectorization | Restructuring computation and layout so SIMD instructions are actually useful. | Automatic compiler optimization alone. |
| Vectorized execution | Processing a batch/vector of tuples, candidates, or queries at a time. | ANN vectors as data objects. |
| Query batching | Serving multiple queries together to reuse data, amortize transfers, or fill hardware. | SIMD lanes inside one CPU instruction. |
| SIMT/GPU warp execution | GPU threads execute in warp-style lockstep with different memory and synchronization constraints. | CPU SIMD, even though the performance logic is related. |
| FastScan-style batch | A fixed batch of quantized codes is processed through in-register lookup tables. | Arbitrary batching at the request scheduler. |

## Mechanism Map

| ANNS stage | Vectorization opportunity | Core papers | Main risk |
|---|---|---|---|
| Dense exact distance | SIMD L2/IP kernels, cache-aware query blocks, int8 arithmetic | Milvus, Low-Precision KNN, FAISS library | Memory bandwidth can dominate arithmetic speedup. |
| PQ/ADC scan | In-register lookup, transposed code layout, small LUTs, saturated arithmetic | PQ Fast Scan, Quicker ADC | Works best for scan-like compressed codes, not arbitrary graph traversal. |
| Graph traversal | Batch neighbor distance estimation, neighbor-code colocation, graph degree aligned to batch size | SymphonyQG | Graph search is irregular; random access and branch divergence can erase SIMD gains. |
| Graph construction | Compact construction-time codes, asymmetric/symmetric tables, codeword colocation | Flash Graph Indexing | Construction codes must preserve graph quality, not just speed distance estimates. |
| Exact reranking | Partial-distance pruning, contiguous batch layout, mini-batch reranking | Panorama, FusionANNS | Benefits depend on whether reranking dominates end-to-end latency. |
| Filters and IDs | SIMD integer decoding, list intersection, selection vectors, compressed adjacency lists | Stream VByte, SIMD Posting Lists, SIMD Compression/Intersection | Useful only if list/filter processing is on the critical path. |
| Batch scheduling | Query blocking, cluster grouping, transfer/compute overlap, GPU memory management | Milvus, RUMMY, FAISS GPU | Improves throughput but can hurt tail latency or fairness. |
| Irregular control flow | Lane refill, buffering, gather/scatter, divergence-aware pipelines | SIMD Investments, Rethinking SIMD | Overhead can exceed gains for short or highly variable candidate paths. |

## Recommended Central Narrative

Start the chapter by separating three layers:

1. Hardware lane parallelism: SIMD and SIMT.
2. Execution batching: processing candidates, codes, or queries in groups.
3. ANNS algorithm structure: IVF scans are regular, graph traversal is irregular, reranking is often contiguous but expensive.

Then argue that good ANNS vectorization requires all three layers to agree. PQ Fast Scan and Quicker ADC succeed because the code layout and LUTs match SIMD registers. Milvus succeeds because query batching reuses cached database vectors. SymphonyQG and Flash show that graph ANN needs layout and graph-degree co-design before SIMD helps. SIMD Investments explains why irregular graph/control-flow paths cannot be vectorized naively.

## What This Map Adds To The General Section Map

The general ANNS writing map tells an agent how to write paper sections. This map tells an agent what technical material to learn before writing a vectorization-and-batch chapter.

Use this map when the target section needs to explain implementation mechanisms, batch layout, hardware utilization, compressed-code scanning, graph-code colocation, or why a system's query path is vectorization-friendly.

Do not use this map as a generic related-work section. It is a technical writing and implementation guide.
