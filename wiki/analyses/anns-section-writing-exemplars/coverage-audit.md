---
id: anns-section-writing-coverage-audit
type: analysis
status: active
created: 2026-05-29
updated: 2026-05-29
tags: [anns, paper-writing, coverage-audit, section-exemplars]
source_count: 69
sources:
  - wiki/source-notes/
related:
  - anns-section-writing-exemplars
confidence: medium
---

# ANNS Section Writing Coverage Audit

This audit records the full candidate pool used for the May 29, 2026 refresh of [ANNS Section Writing Exemplars](README.md). I scanned all 69 current source-note pages in the vault. The table below states whether each paper was directly eligible for section-exemplar ranking, supporting only, or excluded as non-ANNS context.

## Coverage Categories

| Category | Meaning |
|---|---|
| Direct candidate | Evaluated for at least one section Top 5. |
| Supporting | Read as ANNS-related context, but not strong enough or not section-compatible enough for Top 5. |
| Adjacent | Useful for hardware, execution, or database context, but not an ANNS paper-template source. |
| Excluded | Present in the vault but not relevant to ANNS section writing. |

## Direct Candidates And Supporting Sources

| Source note | Category | Section-exemplar decision |
|---|---|---|
| [SPFresh](../../source-notes/spfresh-2023.md) | Direct candidate | Top 5 for abstract, method, architecture, implementation, and evaluation. |
| [Starling](../../source-notes/starling-2024.md) | Direct candidate | Top 5 for abstract, introduction, background, motivation, architecture, method, evaluation, and discussion. |
| [OdinANN](../../source-notes/odinann-2026.md) | Direct candidate | Top 5 for abstract, introduction, background, motivation, method, implementation, evaluation, related work, and discussion. |
| [VBASE](../../source-notes/vbase-2023.md) | Direct candidate | Top 5 for introduction, background, and related work; still too query-interface-specific for most method sections. |
| [Milvus](../../source-notes/milvus-2021.md) | Direct candidate | Top 5 for architecture, optimization, and implementation; best source for broad vector DB execution. |
| [GustANN](../../source-notes/gustann-2025.md) | Direct candidate | Top 5 for motivation, implementation, related work, and discussion. |
| [Chameleon](../../source-notes/chameleon-ralm-vector-search-2024.md) | Direct candidate | Top 5 for abstract, introduction, background, motivation, architecture, optimization, implementation, evaluation, related work, and discussion. |
| [WARP](../../source-notes/warp-multi-vector-retrieval-2025.md) | Direct candidate | Top 5 for abstract, motivation, method, optimization, evaluation, related work, and discussion. |
| [Integrating Vector Databases](../../source-notes/integrating-vector-databases-embedding-models-2026.md) | Direct candidate | Top 5 for introduction, background, and method; use only for vector-DB/data-management framing, not ANNS execution claims. |
| [FusionANNS](../../source-notes/fusionanns-2025.md) | Direct candidate | Top 5 for architecture; still useful for multi-tier GPU/SSD reranking context, but not cleaner than Chameleon. |
| [PQ Fast Scan](../../source-notes/pq-fast-scan-2015.md) | Direct candidate | Top 5 for optimization/execution layer; not a full system-section template. |
| [Flash Graph Indexing](../../source-notes/flash-graph-indexing-2025.md) | Direct candidate | Top 5 for optimization/execution layer; supporting for graph construction method. |
| [Quicker ADC](../../source-notes/quicker-adc-2019.md) | Supporting | Strong optimization source, but prose is less clean as a section template than PQ Fast Scan. |
| [SymphonyQG](../../source-notes/symphonyqg-2024.md) | Supporting | Strong graph+SIMD source, but too many interacting mechanisms for a Top 5 writing template. |
| [DiskANN](../../source-notes/diskann-2019.md) | Supporting | Foundational and must cite, but not the best modern section-writing template. |
| [SPANN](../../source-notes/spann-2021.md) | Supporting | Important memory-disk IVF source; Starling/SPFresh/OdinANN now write sharper system sections. |
| [RUMMY](../../source-notes/rummy-2024.md) | Supporting | Strong batching/pipeline source; still not Top 5 after adding WARP and Chameleon execution-path exemplars. |
| [BANG](../../source-notes/bang-2024.md) | Supporting | Important GPU graph source; prose is weaker than GustANN/RUMMY for explaining hardware cooperation. |
| [SmartANNS](../../source-notes/smartanns-2024.md) | Supporting | Useful NDP/SmartSSD source; background less clean than OdinANN/Starling/VBASE. |
| [SVFusion](../../source-notes/svfusion-2026.md) | Supporting | Interesting streaming GPU/CPU/disk system; not mature or clean enough for Top 5 writing models. |
| [CXL-ANNS](../../source-notes/cxl-anns-2024.md) | Supporting | Useful hardware co-design context; too specialized/diffuse for general section templates. |
| [d-HNSW](../../source-notes/d-hnsw-2025.md) | Supporting | Useful disaggregated-memory context; not a top prose exemplar. |
| [ANSMET](../../source-notes/ansmet-2025.md) | Supporting | Near-memory ANN acceleration context; not a top writing model. |
| [Performance/Index-Size Dilemma](../../source-notes/performance-index-size-dilemma-2024.md) | Supporting | Strong systems framing source, but not enough section detail in current note for Top 5. |
| [FAISS GPU](../../source-notes/faiss-gpu-2017.md) | Supporting | Foundational GPU/vector search implementation source; use for GPU batching analogy, not section prose. |
| [FAISS Library](../../source-notes/faiss-library-2025.md) | Supporting | Canonical taxonomy and library architecture; not a section-writing exemplar. |
| [ScaNN](../../source-notes/scann-2020.md) | Supporting | Strong quantization/method source; less useful for ANNS systems section prose. |
| [Product Quantization](../../source-notes/product-quantization-for-nearest-neighbor-search-2011.md) | Supporting | Foundational method; older style and not a modern systems template. |
| [RaBitQ Extension](../../source-notes/rabitq-extension-2024.md) | Supporting | Important quantization method; better used through SymphonyQG/optimization discussion. |
| [TurboQuant](../../source-notes/turboquant-2025.md) | Supporting | Relevant to vector quantization; mixed KV-cache/retrieval scope makes it unsuitable for ANNS section Top 5. |
| [Low-Precision KNN](../../source-notes/low-precision-quantization-knn-2021.md) | Supporting | Useful int8 implementation context; not a top writing exemplar. |
| [Norm-Explicit Quantization](../../source-notes/norm-explicit-quantization-mips-2020.md) | Supporting | Useful for MIPS quantization argument; not a section-writing model. |
| [Quantization to Speedup ANN](../../source-notes/quantization-to-speedup-ann-2024.md) | Supporting | Adaptive IVF/HNSW control source; not a top section template. |
| [AQR-HNSW](../../source-notes/aqr-hnsw-2026.md) | Supporting | Low-confidence preprint; do not use as top writing model. |
| [HNSW-LAVQ](../../source-notes/quantization-enhanced-hnsw-lavq-2025.md) | Supporting | Low-confidence source; not top writing model. |
| [Information-Theoretic Binarization](../../source-notes/information-theoretic-binarization-vector-search-2026.md) | Supporting | Speculative binary architecture source; not top writing model. |
| [Panorama](../../source-notes/panorama-2025.md) | Supporting | Strong refinement source; narrower than system section templates. |
| [ANN-Benchmarks](../../source-notes/ann-benchmarks-2018.md) | Supporting | Excellent evaluation methodology reference; not a new-system section template. |
| [Graph-Based ANNS Survey](../../source-notes/graph-based-anns-survey-2021.md) | Supporting | Excellent background taxonomy; survey style is not the same as systems-paper section writing. |
| [HNSW](../../source-notes/hnsw-2016.md) | Supporting | Foundational graph method; older algorithm paper style. |
| [NSG](../../source-notes/nsg-2019.md) | Supporting | Important graph method; supporting rather than top prose template. |
| [Multi-Probe LSH](../../source-notes/multi-probe-lsh-2007.md) | Supporting | Classical VLDB/Test-of-Time source; technically important, but too old in framing and scale to be a modern section-writing template. |
| [NN-Descent](../../source-notes/nn-descent-2011.md) | Supporting | Foundational graph-construction primitive; not a systems section template. |
| [GNNS](../../source-notes/gnns-knn-graph-2011.md) | Supporting | Historical graph traversal source; not top template. |
| [EFANNA](../../source-notes/efanna-2016.md) | Supporting | Tree-initialized graph source; not top template. |
| [FANNG](../../source-notes/fanng-2016.md) | Supporting | RNG-like pruning source; not top template. |
| [DPG](../../source-notes/dpg-ann-experiments-2016.md) | Supporting | Empirical graph-analysis source; not top template. |
| [NGT/ONNG](../../source-notes/ngt-onng-2018.md) | Supporting | Practical graph-library source; not top template. |
| [Navigable Small World](../../source-notes/navigable-small-world-graph-ann-2014.md) | Supporting | HNSW predecessor; historical support only. |
| [Kleinberg Small World](../../source-notes/kleinberg-small-world-2000.md) | Adjacent | Theory context only, not ANNS section template. |
| [Monotonic Proximity Graphs](../../source-notes/monotonic-proximity-graphs-2021.md) | Supporting | Graph theory source; useful for background, not system prose. |
| [Satellite System Graph](../../source-notes/satellite-system-graph-2019.md) | Supporting | Graph pruning/theory source; not top template. |
| [Relative NN-Descent](../../source-notes/relative-nn-descent-2023.md) | Supporting | Construction method source; not top template. |
| [RNSG](../../source-notes/rnsg-2026.md) | Supporting | Range-filtered graph method; not enough maturity for Top 5. |
| [Patience in Proximity](../../source-notes/patience-in-proximity-2025.md) | Supporting | HNSW early termination source; useful optimization idea, not section template. |
| [FLANN](../../source-notes/flann-2014.md) | Supporting | Classical baseline/library source; older style. |
| [FALCONN](../../source-notes/falconn-lsh-angular-2015.md) | Supporting | LSH baseline source; not top section model. |
| [FastLanes](../../source-notes/fastlanes-2023.md) | Adjacent | SIMD layout source for optimization context, not an ANNS paper. |
| [SIMD Investments](../../source-notes/simd-investments-2020.md) | Adjacent | Divergence/vectorized execution context, not an ANNS paper. |
| [Compiled/Vectorized Queries](../../source-notes/compiled-vectorized-queries-2018.md) | Adjacent | Batch/vectorized execution context, not an ANNS paper. |
| [Rethinking SIMD](../../source-notes/rethinking-simd-vectorization-2015.md) | Adjacent | SIMD operator context, not an ANNS paper. |
| [SIMD Posting Lists](../../source-notes/simd-based-decoding-posting-lists-2011.md) | Adjacent | Filter/list-path context only. |
| [SIMD Compression/Intersection](../../source-notes/simd-compression-intersection-2014.md) | Adjacent | Filter/list-path context only. |
| [Stream VByte](../../source-notes/stream-vbyte-2017.md) | Adjacent | Filter/list-path context only. |
| [QJL](../../source-notes/qjl-2024.md) | Adjacent | KV-cache quantization source; not an ANNS paper template. |
| [CXL Memory Characterization](../../source-notes/cxl-memory-characterization-2023.md) | Adjacent | Hardware characterization context only. |
| [CXLfork](../../source-notes/cxlfork-2025.md) | Excluded | CXL process cloning, not ANNS. |
| [PolarCXLMem](../../source-notes/polarcxlmem-2025.md) | Excluded | CXL cloud-native database memory system, not ANNS. |
| [Morsel-Driven Parallelism](../../source-notes/morsel-driven-parallelism-2014.md) | Adjacent | Scheduling concept; useful analogy, not ANNS section template. |

## Completeness Claim

This audit covers every current source-note file under `wiki/source-notes/` as of 2026-05-29: 69 source-note pages total. The Top 5 section rankings are drawn only from papers that are direct ANNS systems/methods, vector-database papers with a reusable database abstraction, or highly relevant ANNS execution-layer papers. Adjacent database, CXL, SIMD, and KV-cache papers were considered but excluded from Top 5 unless they directly help explain an ANNS implementation section.
