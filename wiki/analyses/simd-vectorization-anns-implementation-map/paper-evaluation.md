---
id: simd-vectorization-anns-paper-evaluation
type: analysis
status: active
created: 2026-05-27
updated: 2026-05-27
tags: [anns, simd, vectorization, paper-evaluation]
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
  - simd-vectorization-anns-implementation-map
confidence: medium
---

# Paper Evaluation: SIMD / Vectorization / Batch For ANNS

## Rating Legend

| Rating | Meaning |
|---|---|
| A | Central. Use directly in the vectorization/batch chapter. |
| B | Strong support. Use for one subsection or mechanism. |
| C | Context only. Mention if needed, but do not center the chapter on it. |
| D | Do not use as evidence for SIMD/vectorization unless the claim is very narrow. |

## Evaluation Matrix

| Paper | Rating | Best use in chapter | Main lesson | Caveat |
|---|---|---|---|---|
| [PQ Fast Scan](../../source-notes/pq-fast-scan-2015.md) | A+ | Explain SIMD ADC and in-register lookup. | Cache locality is not enough; the lookup table must fit the SIMD register model. | Specialized to scan-style PQ/ADC. |
| [Quicker ADC](../../source-notes/quicker-adc-2019.md) | A | Explain modern SIMD ADC and FAISS integration. | Subquantizer bit width, split tables, AVX-512 capability, and index structure must be co-designed. | Mostly distance evaluation, not a full vector DB. |
| [Milvus](../../source-notes/milvus-2021.md) | A | Explain query batching, cache reuse, and runtime SIMD dispatch in a production vector DB. | Batch queries can improve cache locality by comparing cached database blocks against multiple queries. | Broad system paper; SIMD section is concise. |
| [SymphonyQG](../../source-notes/symphonyqg-2024.md) | A- | Explain graph ANN plus SIMD batch search. | Graph search benefits from FastScan only when neighbor codes, graph degree, reranking, and layout are co-designed. | Medium confidence source; duplicated neighbor codes increase index size. |
| [Flash Graph Indexing](../../source-notes/flash-graph-indexing-2025.md) | A- | Explain construction-time SIMD and compact codes for HNSW-like graph building. | Build-time distance comparisons need their own compact-code layout, not just query-time quantization. | Inbox/preprint metadata; focus is construction, not serving. |
| [FastLanes](../../source-notes/fastlanes-2023.md) | B+ | Explain SIMD-friendly layout and auto-vectorization. | Layout can expose SIMD parallelism without hand-written ISA-specific code. | Database compression source, not ANN-specific. |
| [SIMD Investments](../../source-notes/simd-investments-2020.md) | B+ | Explain divergence and lane refill in irregular pipelines. | SIMD lanes go idle under control-flow divergence; refill and buffering may help. | Database pipelines, not ANN; use as conceptual warning. |
| [Compiled and Vectorized Queries](../../source-notes/compiled-vectorized-queries-2018.md) | B+ | Explain vectorized execution and batch primitives. | Vectorized execution hides cache misses and makes SIMD easier, but end-to-end bottlenecks matter. | Not ANN-specific. |
| [Rethinking SIMD Vectorization](../../source-notes/rethinking-simd-vectorization-2015.md) | B | Explain gather/scatter, buffering, partitioning, and operator-level SIMD design. | Irregular memory access needs buffering and layout changes, not just SIMD intrinsics. | Some hardware details are historical. |
| [Low-Precision Quantization for KNN](../../source-notes/low-precision-quantization-knn-2021.md) | B | Explain int8/SQ-style implementation path. | Quantization can make distance computation cheaper if distance ordering is preserved. | Not primarily a SIMD paper; evidence is narrower. |
| [FAISS GPU](../../source-notes/faiss-gpu-2017.md) | B | Explain GPU batch and register-resident selection as analogy. | Keep hot selection state local and fuse distance plus selection to avoid memory traffic. | GPU SIMT is not CPU SIMD. |
| [RUMMY](../../source-notes/rummy-2024.md) | B | Explain batch scheduling beyond GPU memory. | Reordering and grouping query-cluster work can overlap transfer and computation. | Batch pipeline paper, not SIMD. |
| [FusionANNS](../../source-notes/fusionanns-2025.md) | B- | Explain mini-batch reranking and I/O-aware refinement. | Accurate reranking can be staged and stopped early to reduce raw-vector I/O. | GPU/SSD system; not a SIMD source. |
| [Panorama](../../source-notes/panorama-2025.md) | B- | Explain batch exact refinement and partial-distance pruning. | Exact reranking can be accelerated by level-wise partial distances and bounds. | Preprint; strongest gains are not graph traversal. |
| [Stream VByte](../../source-notes/stream-vbyte-2017.md) | B- | Explain compressed ID/list path. | Separate control/data streams make integer decoding SIMD-friendly. | Useful only if IDs, posting lists, or filters are critical. |
| [SIMD Compression and Intersection](../../source-notes/simd-compression-intersection-2014.md) | B- | Explain filters, list intersection, and hybrid vector/text retrieval. | Decompression and downstream list intersection must both be vectorized. | Search-engine source, not ANN. |
| [SIMD-Based Posting List Decoding](../../source-notes/simd-based-decoding-posting-lists-2011.md) | C+ | Explain historical SIMD variable-byte decoding. | Encoding format determines whether SIMD decoding helps. | Supporting evidence only. |
| [FAISS Library](../../source-notes/faiss-library-2025.md) | C+ | Cite index taxonomy, SQ/PQ, CPU/GPU support, IndexRefine. | FAISS provides canonical index and quantizer vocabulary. | Not focused on vectorization mechanisms. |
| [ScaNN](../../source-notes/scann-2020.md) | C | Explain quantized scoring quality, not vectorization. | Score-aware quantization preserves retrieval ranking better than plain reconstruction loss. | Do not use as SIMD/batch evidence. |
| [GustANN](../../source-notes/gustann-2025.md) | C | Mention high-concurrency GPU/SSD throughput as adjacent systems context. | Batch/concurrency can make irregular search hardware-efficient. | Main contribution is SSD/GPU system scheduling, not SIMD. |

## Brutal Takeaways

The chapter should not treat all SIMD-related papers equally. PQ Fast Scan and Quicker ADC are the true SIMD core for compressed ANN distance evaluation.

Milvus is the best ANNS paper for explaining batching as cache reuse. If the chapter has a "batch" subsection and does not discuss Milvus Section 3.2, it is missing the most direct system source.

SymphonyQG and Flash are the most useful graph-ANN papers, but they teach different stages. SymphonyQG is query-time graph traversal plus SIMD estimation. Flash is construction-time graph building plus compact SIMD codes.

FastLanes, SIMD Investments, Compiled/Vectorized Queries, and Rethinking SIMD are not ANNS papers, but they explain the execution model better than most ANNS papers do. Use them to define principles, then ground those principles in ANNS papers.

Posting-list SIMD papers are supporting material. They matter if your system has metadata filters, IVF list IDs, graph adjacency lists, or vector-text hybrid retrieval. They should not dominate the chapter.

ScaNN and low-precision quantization papers are easy to misuse. They are about quantization quality and cheaper arithmetic; they do not automatically prove that the system is vectorized.
