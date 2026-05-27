---
id: simd-vectorization-anns-chapter-blueprint
type: analysis
status: active
created: 2026-05-27
updated: 2026-05-27
tags: [anns, simd, vectorization, batch-execution, writing-blueprint]
source_count: 12
sources:
  - raw/sources/papers/pq-fast-scan-2015.pdf
  - raw/sources/papers/quicker-adc-2019.pdf
  - raw/sources/papers/symphonyqg-2024.pdf
  - raw/inbox/flash-graph-indexing-2025.pdf
  - raw/sources/papers/milvus-2021.pdf
  - raw/sources/papers/fastlanes-2023.pdf
  - raw/sources/papers/simd-investments-2020.pdf
  - raw/sources/papers/compiled-vectorized-queries-2018.pdf
  - raw/sources/papers/rethinking-simd-vectorization-2015.pdf
  - raw/sources/papers/stream-vbyte-2017.pdf
  - raw/sources/papers/rummy-2024.pdf
  - raw/sources/papers/faiss-gpu-2017.pdf
related:
  - simd-vectorization-anns-implementation-map
confidence: medium
---

# Chapter Blueprint: Vectorization and Batch Execution in ANNS Systems

## Recommended Thesis

Vectorization in ANNS is a co-design problem across representation, layout, batch shape, and search control flow. Regular scan-like stages such as PQ/ADC and dense distance computation are naturally vectorization-friendly. Graph traversal, filtering, and reranking need additional layout and scheduling work because they introduce random access, divergence, and variable candidate counts.

## Suggested Section Structure

### 1. Open With The Misconception

Claim to make: SIMD does not automatically speed up ANNS. The hot loop must be reshaped so the CPU can keep vector lanes full and avoid random memory traffic.

Use [PQ Fast Scan](../../source-notes/pq-fast-scan-2015.md) as the opening source: even cache-resident lookup tables are not enough if lookup operations do not map to SIMD registers.

### 2. Define The Execution Terms

Explain these terms early:

| Term | Explanation |
|---|---|
| SIMD | A CPU instruction applies the same operation to multiple lanes. |
| Vectorized execution | The system processes batches of tuples, candidates, or queries at once. |
| Query batching | Multiple user queries are grouped to reuse data or fill hardware. |
| FastScan batch | A fixed group of quantized codes is processed with register-resident lookup tables. |
| GPU SIMT | GPU warp execution is related but has different memory and synchronization constraints. |

This prevents a common writing bug: using "vectorization" to mean five different things.

### 3. Explain Where ANNS Spends Work

Break the ANNS pipeline into stages:

| Stage | Typical work | Vectorization status |
|---|---|---|
| Coarse routing | centroid distances, partition selection, graph entry search | Often batchable. |
| Candidate scan | PQ/SQ distance estimates, list scan, dense distance | Most SIMD-friendly. |
| Graph expansion | neighbor fetch, candidate queue, visited checks | Hard due to irregular access and divergence. |
| Reranking/refinement | exact L2/IP over candidates, raw-vector fetch | Batchable if candidates are contiguous or staged. |
| Filters/metadata | ID decode, posting-list intersection, attribute predicates | SIMD-friendly only if lists are encoded/layouted for it. |

### 4. Mechanism A: In-Register Lookup For PQ/ADC

Use [PQ Fast Scan](../../source-notes/pq-fast-scan-2015.md) and [Quicker ADC](../../source-notes/quicker-adc-2019.md).

Core explanation:

1. Product quantization stores each vector as subquantizer code indexes.
2. ADC uses query-specific lookup tables to sum partial distances.
3. Naive ADC repeatedly loads table entries from cache.
4. FastScan-style methods shrink or split tables so lookups happen inside SIMD registers.
5. Code layout is transposed/grouped so one instruction processes many candidate codes.
6. The implementation changes the execution path without changing the high-level ANN algorithm.

Writing angle: this is the cleanest example of vectorization as data-layout co-design.

### 5. Mechanism B: Query Batching For Cache Reuse

Use [Milvus](../../source-notes/milvus-2021.md).

Core explanation:

1. One-query-per-thread scans reuse little data across queries.
2. A batch of queries can share cached database vectors.
3. Milvus partitions data by threads and queries by cache-fitting blocks.
4. Each loaded data block is compared against multiple queries before eviction.
5. SIMD dispatch is selected at runtime across SSE/AVX/AVX2/AVX512.

Writing angle: batching is not just higher throughput; it changes cache behavior.

### 6. Mechanism C: Graph ANN Needs Layout Co-Design

Use [SymphonyQG](../../source-notes/symphonyqg-2024.md), [Flash Graph Indexing](../../source-notes/flash-graph-indexing-2025.md), and [SIMD Investments](../../source-notes/simd-investments-2020.md).

Core explanation:

1. Graph search is irregular because each candidate expands a different neighborhood.
2. SIMD lanes become hard to fill when branch paths and candidate counts diverge.
3. SymphonyQG handles query-time traversal by storing neighbor quantization codes beside graph vertices and aligning graph out-degree with FastScan batch size.
4. Flash handles construction-time graph building by using compact codes and table lookup to avoid repeated random full-vector fetches.
5. The lesson is not "graph search is SIMD-friendly"; the lesson is that graph search can become more vectorization-friendly after changing layout and graph structure.

Writing angle: this is the key subsection if the user's system uses HNSW/NSG/DiskANN-like traversal.

### 7. Mechanism D: Compressed Lists, Filters, and Metadata

Use [Stream VByte](../../source-notes/stream-vbyte-2017.md), [SIMD-Based Posting List Decoding](../../source-notes/simd-based-decoding-posting-lists-2011.md), and [SIMD Compression and Intersection](../../source-notes/simd-compression-intersection-2014.md).

Core explanation:

1. Vector search systems often spend time on IDs, filters, posting lists, or adjacency lists.
2. SIMD helps only if the encoding exposes regular control flow.
3. Separating control bytes from data bytes or using block-based bitpacking can enable fast decoding.
4. Decompression alone is not enough; downstream intersection/filtering should also be vectorized.

Writing angle: this subsection supports hybrid vector search and vector database implementation details.

### 8. Mechanism E: Batch Scheduling Beyond CPU SIMD

Use [FAISS GPU](../../source-notes/faiss-gpu-2017.md) and [RUMMY](../../source-notes/rummy-2024.md) as analogies.

Core explanation:

1. GPU systems are not CPU SIMD systems, but they teach the same locality lesson.
2. FAISS GPU keeps selection state close to registers/shared memory and fuses distance with selection.
3. RUMMY batches and reorders query-cluster work so data transfer and computation overlap.
4. These papers help explain why batch is a systems scheduling decision, not only a vector-register decision.

Writing angle: use this only after CPU SIMD is clearly defined.

## Figure Ideas For The Chapter

Draw one pipeline figure with five stages: route, scan/estimate, graph expand, rerank, filter/list path.

Draw one "bad vs good" SIMD figure:

| Bad path | Good path |
|---|---|
| random codes, cache LUT, scalar table lookups | transposed codes, register LUT, SIMD shuffle |
| one query streams full database | query block reuses cached data vectors |
| graph neighbors fetch raw vectors randomly | neighbor codes colocated with graph vertices |
| variable branches leave SIMD lanes idle | batch, refill, or layout reduces divergence |

Draw one taxonomy box that separates CPU SIMD, vectorized execution, query batching, and GPU SIMT.

## Evaluation Checklist

Any paper or system claiming vectorization should report:

1. Which query stage is accelerated.
2. Whether speedup is instruction-level, cache-level, bandwidth-level, or algorithmic pruning.
3. SIMD ISA used: SSE, AVX2, AVX-512, NEON, or other.
4. Batch size and whether it affects tail latency.
5. Memory layout before and after optimization.
6. Cache misses, bandwidth, instruction count, or at least stage-level breakdown.
7. Recall or accuracy at matched settings.
8. Whether raw-vector reranking remains a bottleneck.
9. Whether graph traversal still performs random access.
10. Whether gains persist end-to-end, not only in microbenchmarks.

## Writing Pitfalls

Do not say "we vectorize ANNS" without naming the stage.

Do not cite GPU papers as evidence for CPU SIMD.

Do not cite quantization papers as vectorization papers unless the execution kernel is actually changed.

Do not claim batch improves everything. Batch can improve throughput and cache reuse while worsening tail latency.

Do not hide ISA dependence. AVX2, AVX-512, and compiler auto-vectorization can lead to different implementation constraints.

Do not ignore graph irregularity. HNSW-like search is not scan-like unless the layout is redesigned.
