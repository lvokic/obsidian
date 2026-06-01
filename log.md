# Log

This file is the append-only chronological history of wiki operations.

## [2026-04-08 00:00] refactor | Initial scaffold

- Created the initial vault scaffold for the LLM wiki.
- Added `AGENTS.md`, `index.md`, and `log.md`.
- Created the base directory structure under `raw/`, `wiki/`, and `templates/`.
- Next step: add the first real source or create the first durable wiki page.

## [2026-04-08 11:12] ingest | QJL, Product Quantization, TurboQuant

- Ingested `raw/QJL.pdf`, `raw/pq.pdf`, and `raw/TurboQuant.pdf`.
- Added source notes for QJL, Product Quantization, and TurboQuant under `wiki/source-notes/`.
- Added synthesis pages under `wiki/overview/`, `wiki/topics/`, and `wiki/entities/` to connect retrieval-oriented quantization with KV-cache compression.
- Updated `index.md` so the new pages are navigable from the root catalog.
- Working synthesis: Product Quantization is the foundational retrieval baseline, QJL is the specialized zero-overhead KV-cache method, and TurboQuant is the broader online framework that reuses QJL on residuals.
- Open questions: whether TurboQuant beats plain QJL head-to-head on KV-cache tasks at matched latency budgets, and how much tuned offline PQ still outperforms online methods on mature ANN workloads.

## [2026-04-08 11:18] ingest | RaBitQ extension for ANN search

- Ingested `raw/rabbitq.pdf`.
- Added a source note and entity page for the multi-bit RaBitQ extension under `wiki/source-notes/` and `wiki/entities/`.
- Updated the overview and topic synthesis pages so the retrieval branch now distinguishes PQ-style learned codebooks from RaBitQ-style randomized data-oblivious quantization.
- Updated `index.md` so the new method and source are navigable from the root catalog.
- Working synthesis: RaBitQ strengthens the retrieval side of the vault as a theory-heavy alternative to PQ, while TurboQuant remains the broader framework trying to span both retrieval and inference.
- Open questions: whether RaBitQ or TurboQuant is the stronger practical retrieval path under equal engineering effort, and when PQ still wins enough on mature ANN workloads to justify offline indexing complexity.

## [2026-04-08 17:18] ingest | HNSW, NSG, DiskANN, CXL-ANNS, second-tier-memory trade-offs, d-HNSW

- Ingested six new ANN/system sources: `raw/HNSW.pdf`, `raw/NSG.pdf`, `raw/DiskANN.pdf`, `raw/CXL-ANNS.pdf`, `raw/Characterizing the Dilemma of Performance and Index Size in Billion-Scale Vector Search .pdf`, and `raw/Efficient Vector Search on Disaggregated Memory with d-HNSW.pdf`.
- Added six source notes under `wiki/source-notes/` for the above papers.
- Added five new entity pages under `wiki/entities/`: HNSW, NSG, DiskANN, CXL-ANNS, and d-HNSW.
- Added two new systems topics under `wiki/topics/`: `second-tier-memory-for-vector-search` and `disaggregated-memory-vector-search`.
- Rewrote `wiki/topics/approximate-nearest-neighbor-search.md` to integrate the quantization branch with the graph/system co-design branch.
- Updated `index.md` so all newly added topic/entity/source-note pages are navigable from the root catalog.
- Working synthesis: the vault now distinguishes ANN method design (PQ/RaBitQ/TurboQuant, HNSW/NSG) from ANN systems design (DiskANN on SSD, CXL/RDMA/second-tier-memory pathways), making the memory-tier trade-off explicit.
- Open questions: crossover point between SSD-centric and disaggregated-memory-centric serving under matched hardware budgets, and how robust published wins are under mixed update/query production workloads.

## [2026-04-08 17:20] lint | ANN systems branch cross-link health check

- Checked wiki markdown links for broken references across `wiki/` and `index.md`; no broken local links found.
- Checked inbound-link counts and found weak linkage on `wiki/source-notes/performance-index-size-dilemma-2024.md`.
- Added explicit cross-links from `wiki/topics/second-tier-memory-for-vector-search.md` and `wiki/topics/disaggregated-memory-vector-search.md` to the performance/index-size source note.
- Expanded related links in `wiki/source-notes/performance-index-size-dilemma-2024.md` to include disaggregated-memory pathways (`cxl-anns`, `d-hnsw`).
- Remaining risk: no structural contradictions detected at markdown-link level, but benchmark comparability across papers still needs manual methodological alignment when building seminar-level comparative claims.

## [2026-04-08 17:36] ingest | CXLfork, PolarCXLMem, ANSMET and CXL cross-domain systems

- Ingested four new raw sources: `raw/CXLfork.pdf`, `raw/Unlocking the Potential of CXL for Disaggregated Memory in Cloud-Native Databases.md`, `raw/Unlocking the Potential of CXL for Disaggregated Memory in CloudNative Databases.pdf`, and `raw/ANSMET- .pdf`.
- Added three source notes under `wiki/source-notes/`: `cxlfork-2025.md`, `polarcxlmem-2025.md`, and `ansmet-2025.md`.
- Added three entity pages under `wiki/entities/`: `cxlfork.md`, `polarcxlmem.md`, and `ansmet.md`.
- Added one new topic page: `wiki/topics/cxl-disaggregated-memory-systems.md` to connect CXL work across ANN, cloud databases, and serverless runtimes.
- Updated `wiki/topics/approximate-nearest-neighbor-search.md` to include ANSMET as a near-memory acceleration branch.
- Updated `wiki/topics/disaggregated-memory-vector-search.md` and `index.md` for navigation and cross-link coverage.
- Working synthesis: the vault now separates memory-fabric-aware ANN serving (CXL/RDMA) from broader CXL-native system-interface redesigns (process cloning, database buffer/recovery/coherence).
- Open questions: portability of current gains across future CXL switch generations, and which abstractions can be standardized across ANN, DBMS, and serverless stacks.

## [2026-04-08 17:42] ingest | Patience in Proximity (HNSW early termination)

- Ingested `raw/patience.pdf`.
- Added `wiki/source-notes/patience-in-proximity-2025.md` with source-grounded summary of the saturation-based early-termination strategy for HNSW traversal.
- Added `wiki/entities/patience-in-proximity.md` and linked it with `wiki/entities/hnsw.md`.
- Updated `wiki/topics/approximate-nearest-neighbor-search.md` to include the HNSW-traversal-heuristic branch.
- Updated `index.md` so the new entity/source note are reachable from root navigation.
- Working synthesis: this source strengthens the "lightweight runtime heuristics on top of HNSW" lane, complementary to system-level accelerations like ANSMET and disaggregated-memory serving.
- Open questions: how robust patience thresholds are across datasets, and whether this heuristic composes cleanly with DiskANN/HNSW production variants under strict recall targets.

## [2026-04-10 00:00] refactor | Tidy raw/ directory structure

- Reorganized all 26 flat files from `raw/` root into three logical subdirectories under `raw/sources/`.
- Moved 16 academic PDFs to `raw/sources/papers/` with slug names matching wiki source-notes (e.g., `ansmet-2025.pdf`, `hnsw-2016.pdf`).
- Moved 2 hand-written notes/summaries to `raw/sources/notes/` (`turboquant-notes.md`, `polarcxlmem-notes.md`).
- Fixed malformed filenames: removed trailing space/dash from `ANSMET- .pdf`, renamed all-caps MDs to snake-case, corrected Chinese filename encoding for TurboQuant CN summary.
- `raw/inbox/`, `raw/sources/`, and `raw/assets/` are now empty of misplaced files; all content is properly nested.
- No wiki pages were changed; this was a raw/ housekeeping pass only.

## [2026-04-10 01:00] ingest | FAISS, ScaNN, SPANN, Milvus, ANN-Benchmarks, CXL Memory Characterization

Ingested 7 new sources from `raw/inbox/` (2 FAISS papers counted as one entity):

**Papers ingested:**
- `faiss.pdf` → `raw/sources/papers/faiss-gpu-2017.pdf` (Johnson et al. 2017, GPU IVFPQ + WarpSelect)
- `faiss_2024.pdf` → `raw/sources/papers/faiss-library-2025.pdf` (Douze et al. 2025, Faiss library overview)
- `ScaNN.pdf` → `raw/sources/papers/scann-2020.pdf` (Guo et al. ICML 2020, anisotropic quantization)
- `SPANN.pdf` → `raw/sources/papers/spann-2021.pdf` (Chen et al. NeurIPS 2021, memory-disk IVF)
- `Milvus.pdf` → `raw/sources/papers/milvus-2021.pdf` (Wang et al. SIGMOD 2021, vector DBMS)
- `ANN-Benchmarks.pdf` → `raw/sources/papers/ann-benchmarks-2018.pdf` (Aumüller et al. 2018)
- `CXL-Memory.pdf` → `raw/sources/papers/cxl-memory-characterization-2023.pdf` (Sun et al. Micro 2023)

**New source notes created (7):** `faiss-gpu-2017.md`, `faiss-library-2025.md`, `scann-2020.md`, `spann-2021.md`, `milvus-2021.md`, `ann-benchmarks-2018.md`, `cxl-memory-characterization-2023.md`

**New entity pages created (5):** `faiss.md`, `scann.md`, `spann.md`, `milvus.md`, `ann-benchmarks.md`

**Topic pages updated (3):**
- `approximate-nearest-neighbor-search.md`: expanded to three-layer view (compression, graph, systems); added FAISS, ScaNN, SPANN, Milvus, ANN-Benchmarks; updated system progression narrative.
- `second-tier-memory-for-vector-search.md`: added SPANN as primary DRAM+SSD baseline; added CXL memory characterization for hardware grounding; added tier comparison table.
- `cxl-disaggregated-memory-systems.md`: added CXL memory characterization as hardware grounding section; added CXL latency/bandwidth findings table.

**index.md updated:** 5 new entity entries, 7 new source note entries added to navigation.

**Working synthesis:** The vault now has complete baseline coverage for the ANN systems branch. Key relationship: FAISS (in-DRAM library baseline) → ScaNN (in-DRAM quantized ANN) → SPANN (DRAM+SSD system, deployed at Bing scale) → CXL/RDMA disaggregated-memory systems.

**Open questions:** (1) At what scale/hardware budget do CXL/RDMA memory systems outperform SPANN? (2) Can score-aware quantization improve compressed coarse routing? (3) What billion-scale benchmark protocol should be used given ANN-Benchmarks is in-memory only?

## [2026-05-08 11:42] ingest | GustANN, FusionANNS, and billion-scale vector search literature map

Processed `raw/sources/papers/gustann-2025.pdf` and `raw/sources/papers/fusionanns-2025.pdf` into source notes and entity pages. Updated the ANN and second-tier-memory topic pages to account for SSD+GPU systems as adjacent related work. Created `wiki/analyses/billion-scale-vector-search-literature-map.md` with external paper leads not yet ingested, including RUMMY, SmartANNS, Starling, BANG, SPFresh, VBASE, GRIP, iDEC, ParANN, and iQAN.

Touched pages: `wiki/source-notes/gustann-2025.md`, `wiki/source-notes/fusionanns-2025.md`, `wiki/entities/gustann.md`, `wiki/entities/fusionanns.md`, `wiki/topics/approximate-nearest-neighbor-search.md`, `wiki/topics/second-tier-memory-for-vector-search.md`, `wiki/analyses/billion-scale-vector-search-literature-map.md`, `index.md`.

Unresolved questions: decide which SSD+GPU papers should be fully ingested next, and whether the literature map should include a taxonomy figure separating DRAM-only, SSD-only, SSD+GPU, SmartSSD/NDP, CXL, and RDMA-disaggregated systems.

## [2026-05-08 11:52] refactor | Remove stale project cluster and broken local references

Removed stale project-specific CXL ANN pages and root drafts from the maintained vault graph. Updated ANN, CXL, SSD/GPU, benchmark, and source-note pages to avoid links to deleted project pages. Normalized stale raw source paths to current `raw/sources/` locations and removed missing TurboQuant image links that created broken Obsidian graph nodes.

## [2026-05-08 12:12] ingest | RUMMY, SmartANNS, VBASE, Starling, BANG, and SPFresh

Downloaded and ingested six relevant billion-scale vector search papers not previously present in the repo: `raw/sources/papers/rummy-2024.pdf`, `raw/sources/papers/smartanns-2024.pdf`, `raw/sources/papers/vbase-2023.pdf`, `raw/sources/papers/starling-2024.pdf`, `raw/sources/papers/bang-2024.pdf`, and `raw/sources/papers/spfresh-2023.pdf`.

Created source notes: `wiki/source-notes/rummy-2024.md`, `wiki/source-notes/smartanns-2024.md`, `wiki/source-notes/vbase-2023.md`, `wiki/source-notes/starling-2024.md`, `wiki/source-notes/bang-2024.md`, and `wiki/source-notes/spfresh-2023.md`.

Created entity pages: `wiki/entities/rummy.md`, `wiki/entities/smartanns.md`, `wiki/entities/vbase.md`, `wiki/entities/starling.md`, `wiki/entities/bang.md`, and `wiki/entities/spfresh.md`.

Updated synthesis pages: `wiki/topics/approximate-nearest-neighbor-search.md`, `wiki/topics/second-tier-memory-for-vector-search.md`, and `wiki/analyses/billion-scale-vector-search-literature-map.md`. Updated `index.md` for navigation.

Working synthesis: the billion-scale vector search branch now covers GPU/host-memory execution, SmartSSD/NDP, vector-relational query semantics, segment-level disk graph layout, single-GPU graph search, and fresh-update maintenance in addition to the existing DiskANN/SPANN/GustANN/FusionANNS/CXL/RDMA coverage.

Unresolved questions: remaining candidate papers for future ingest are GRIP, iDEC, ParANN/ParlayANN, and iQAN; decide whether these should be source-note depth or literature-map-only references.

## [2026-05-08 12:21] refactor | Move inbox papers to organized sources

Moved the remaining inbox PDFs into `raw/sources/papers/`: `raw/sources/papers/gustann-2025.pdf` and `raw/sources/papers/fusionanns-2025.pdf`.

Updated source frontmatter references in GustANN/FusionANNS source notes, entity pages, topic pages, and the billion-scale literature map so they no longer point to `raw/inbox/`.

`raw/inbox/` now only retains `.gitkeep`.

## [2026-05-08 14:55] query | Graph-theoretic ANN inbox candidates

Explored graph-theoretic papers related to the current ANN graph-index branch, especially proximity graphs, RNG/MRNG/HSP/MSNET, and navigable small-world ideas connected to HNSW, NSG, and DiskANN. Added six PDFs to `raw/inbox/`: Kleinberg small-world navigability, Malkov et al. NSW, Zhu/Zhang MRNG generalization, Satellite System Graph, Relative NN-Descent, and RNSG/RRNG. Created `wiki/analyses/graph-theoretic-ann-inbox-candidates.md` with the selection rationale, priority order, and high-value candidates not yet downloaded. Updated `index.md`.

Unresolved questions: locate stable downloadable copies for Toussaint 1980 RNG, Jaromczyk/Toussaint 1992 RNG survey, Dearholt MSNET, Aurenhammer Voronoi survey, Navigating Nets, HHSP, and GRNG; decide whether to create a standalone topic page for proximity graph theory after ingest.

## [2026-05-08 15:00] ingest | Proximity graph theory for ANN

Ingested the graph-theoretic ANN PDFs from `raw/inbox/` and moved them to `raw/sources/papers/`: `kleinberg-small-world-2000.pdf`, `navigable-small-world-graph-ann-2014.pdf`, `monotonic-proximity-graphs-2021.pdf`, `satellite-system-graph-2019.pdf`, `relative-nn-descent-2023.pdf`, `rnsg-2026.pdf`, and the supplemental `graph-based-anns-survey-2021.pdf`.

Created source notes for all seven papers, a new topic page `wiki/topics/proximity-graph-theory-for-ann.md`, and five entity pages: `monotonic-relative-neighborhood-graph.md`, `navigable-small-world-graph.md`, `satellite-system-graph.md`, `relative-nn-descent.md`, and `rnsg.md`. Updated `index.md`, `wiki/topics/approximate-nearest-neighbor-search.md`, HNSW/NSG/DiskANN/VBASE entity pages, and relevant HNSW/NSG/DiskANN source notes. Updated `wiki/analyses/graph-theoretic-ann-inbox-candidates.md` so the first batch is recorded as ingested, not still pending in inbox.

Unresolved questions: still need stable copies for Toussaint RNG, Jaromczyk/Toussaint RNG survey, Dearholt MSNET, Aurenhammer Voronoi, Navigating Nets, HHSP, and GRNG; RNSG publication metadata remains uncertain because the arXiv PDF has placeholder PVLDB/DOI fields.

## [2026-05-08 15:16] ingest | ANN benchmarks, graph survey expansion, and SVFusion

Ingested the new inbox contents. `raw/inbox/sv-fusion.pdf` was moved to `raw/sources/papers/svfusion-2026.pdf` and converted into `wiki/source-notes/svfusion-2026.md` plus `wiki/entities/svfusion.md`. `raw/inbox/ann-benchmarks.pdf` was verified as byte-identical to the existing canonical `raw/sources/papers/ann-benchmarks-2018.pdf`; the duplicate inbox copy was removed after updating the canonical ANN-Benchmarks note and entity.

Expanded `wiki/source-notes/ann-benchmarks-2018.md` with implementation-vs-algorithm benchmarking lessons, evaluated algorithm families, key results, and connections to graph/system benchmarks. Expanded `wiki/source-notes/graph-based-anns-survey-2021.md` with the four-family graph taxonomy, 13-algorithm map, seven pipeline components, empirical lessons, and missing primary-source coverage.

Created `wiki/topics/ann-benchmarking-methodology.md` to separate implementation benchmarking, graph-component attribution, and hardware/update-aware system benchmarking. Created `wiki/analyses/ann-benchmarking-and-graph-coverage-gaps.md` as a candidate queue seeded by ANN-Benchmarks, Graph-Based ANNS Survey 2021, and SVFusion references.

Updated `wiki/topics/approximate-nearest-neighbor-search.md`, `wiki/topics/second-tier-memory-for-vector-search.md`, `wiki/analyses/billion-scale-vector-search-literature-map.md`, `wiki/entities/fusionanns.md`, `wiki/entities/bang.md`, `wiki/entities/spfresh.md`, and `index.md`.

Working synthesis: the ANN branch now has a clearer evaluation stack: ANN-Benchmarks for in-memory implementation-level Pareto frontiers, Graph-Based ANNS Survey 2021 for graph-family and component attribution, and SVFusion/SPFresh-style metrics for streaming updates and heterogeneous memory tiers.

Unresolved questions: prioritize primary-source ingests for KGraph/NN-Descent, SPTAG, NGT, CAGRA, FreshDiskANN, and the Big ANN streaming benchmark protocol; decide whether lightweight entity pages should exist before those primary sources are downloaded.

## [2026-05-08 15:29] query | ANN benchmark and graph survey inbox candidates

Explored candidate papers based on `wiki/entities/ann-benchmarks.md` and `raw/sources/papers/graph-based-anns-survey-2021.pdf`. Downloaded eight valuable, non-duplicate PDFs into `raw/inbox/`: `nn-descent-2011.pdf`, `gnns-knn-graph-2011.pdf`, `efanna-2016.pdf`, `fanng-2016.pdf`, `dpg-ann-experiments-2016.pdf`, `ngt-onng-2018.pdf`, `flann-2014.pdf`, and `falconn-lsh-angular-2015.pdf`.

Updated `wiki/analyses/ann-benchmarking-and-graph-coverage-gaps.md` with the downloaded inbox batch, rationale, and deferred candidates. Updated `index.md` to clarify that this analysis now records an inbox candidate queue.

Working synthesis: the next ANN ingest batch should fill the gap between benchmark baselines and graph algorithm internals: KNNG construction (NN-Descent/KGraph), early graph traversal (GNNS), tree-initialized graph construction (EFANNA), RNG-style pruning (FANNG/DPG/NGT), and non-graph benchmark baselines (FLANN/FALCONN).

Unresolved questions: still need stable PDFs or source decisions for SPTAG, HCNNG, PANNG/pruned bi-directed KNNG, Annoy, PyNNDescent, and IEH.

## [2026-05-08 15:43] ingest | ANN graph baseline and non-graph benchmark papers

Ingested the eight new inbox papers selected from ANN-Benchmarks and Graph-Based ANNS Survey 2021, then moved them from `raw/inbox/` into `raw/sources/papers/`: `nn-descent-2011.pdf`, `gnns-knn-graph-2011.pdf`, `efanna-2016.pdf`, `fanng-2016.pdf`, `dpg-ann-experiments-2016.pdf`, `ngt-onng-2018.pdf`, `flann-2014.pdf`, and `falconn-lsh-angular-2015.pdf`.

Created source notes: `wiki/source-notes/nn-descent-2011.md`, `wiki/source-notes/gnns-knn-graph-2011.md`, `wiki/source-notes/efanna-2016.md`, `wiki/source-notes/fanng-2016.md`, `wiki/source-notes/dpg-ann-experiments-2016.md`, `wiki/source-notes/ngt-onng-2018.md`, `wiki/source-notes/flann-2014.md`, and `wiki/source-notes/falconn-lsh-angular-2015.md`.

Created entity pages: `wiki/entities/nn-descent.md`, `wiki/entities/gnns.md`, `wiki/entities/efanna.md`, `wiki/entities/fanng.md`, `wiki/entities/diversified-proximity-graph.md`, `wiki/entities/ngt-onng.md`, `wiki/entities/flann.md`, and `wiki/entities/falconn.md`.

Updated synthesis and navigation pages: `wiki/topics/approximate-nearest-neighbor-search.md`, `wiki/topics/proximity-graph-theory-for-ann.md`, `wiki/topics/ann-benchmarking-methodology.md`, `wiki/source-notes/ann-benchmarks-2018.md`, `wiki/source-notes/graph-based-anns-survey-2021.md`, `wiki/entities/ann-benchmarks.md`, `wiki/entities/nsg.md`, `wiki/source-notes/nsg-2019.md`, `wiki/entities/relative-nn-descent.md`, `wiki/source-notes/relative-nn-descent-2023.md`, `wiki/analyses/ann-benchmarking-and-graph-coverage-gaps.md`, and `index.md`.

Working synthesis: the ANN branch now covers the missing bridge between benchmark baselines and graph-index internals: NN-Descent/KGraph for KNNG construction, GNNS for early graph traversal, EFANNA for tree-initialized graph construction and seeding, FANNG/DPG/NGT/ONNG for practical pruning and degree/path control, and FLANN/FALCONN for non-graph tree/LSH baselines.

Unresolved questions: still need stable primary sources or source decisions for SPTAG, HCNNG, PANNG/pruned bi-directed KNNG, Annoy, PyNNDescent, IEH, CAGRA, FreshDiskANN, and Big ANN streaming benchmark protocols.

## [2026-05-08 15:49] refactor | CXL-Vector paper agent cache and review/writer guides

Created three root-level operating guides for CXL-Vector paper work: `CACHE.md`, `reviewer.md`, and `writer.md`.

`CACHE.md` provides a short read path into the CXL/ANN knowledge base and fixes the intended CXL-Vector framing: capacity-wall motivation, bandwidth-sensitive transparent all-CXL placement, host-local compact traversal state, CXL-resident raw vectors, bounded exact rerank, and matched-recall evaluation.

`reviewer.md` adapts the `vldb-section-reviewer` skill to this vault, including section-specific read paths, CXL-Vector-specific review checks, output file expectations, and minimum-fix bias.

`writer.md` adapts the conservative `vldb-review-writer` workflow for CXL-Vector sections, including claim boundaries, allowed edit actions, forbidden overclaims, and expected writer change-summary output.

Updated `index.md` with an operating-guides section so new agents can find these files before reading deeper wiki pages.

Unresolved questions: once the actual CXL-Vector paper repository path and section filenames are known, these guides may need one line pointing to the paper-local implementation context file.

## [2026-05-08 15:53] refactor | General ANNS system paper cache and review/writer guides

Created root-level general ANNS operating guides: `CACHE.md`, `reviewer.md`, and `writer.md`.

`CACHE.md` is now a compact read path for ANNS system agents, covering the main ANN synthesis, benchmarking methodology, graph survey, proximity-graph theory, in-memory graph baselines, quantization/library baselines, SSD/second-tier systems, GPU/heterogeneous systems, CXL/RDMA/NDP systems, and vector DB semantics.

`reviewer.md` adapts the `vldb-section-reviewer` skill to general ANNS system paper review. It defines claim-specific source paths, baseline expectations, evaluation checks, minimum-fix stance, and exact review/fix output requirements.

`writer.md` provides a conservative writer workflow for ANNS paper sections after review: weaken unsupported claims, clarify mechanisms, preserve matched-recall framing, and avoid invented numbers, baselines, experiments, or citations.

Updated `index.md` operating-guide labels from CXL-Vector-specific to general ANNS-system-specific.

Unresolved questions: if a specific ANNS paper repository has local implementation context, add a short pointer from `CACHE.md` to that paper-local file.

## [2026-05-09 12:36] refactor | ANNS research figure drawing guide and skill

Created a figure-drawing entry point for ANNS system paper work.

Added `FIGURE_CACHE.md` as the short read path for drawing and reviewing ANNS figures. It maps common needs to concrete rendered reference pages: system architecture, data placement, query workflow, graph/algorithm intuition, recall-QPS curves, ablation/sensitivity, and hardware characterization.

Created `wiki/analyses/anns-research-figure-design-guide.md` with a full taxonomy of ANNS paper figures. It separates system figures from experiment figures, summarizes visual patterns across HNSW/NSG/PQ/FAISS, DiskANN/SPANN/Starling/SPFresh, BANG/RUMMY/GustANN/FusionANNS/SVFusion/SmartANNS, CXL-ANNS/CXL memory characterization, ANN-Benchmarks, and Graph-Based ANNS Survey.

Rendered 25 representative PDF pages into `wiki/assets/figure-guide/` for quick visual reference. These include architecture/workflow pages, graph and quantization intuition pages, recall-QPS/Pareto pages, ablation/sensitivity pages, and hardware characterization pages.

Created a vault-local skill at `skills/anns-research-figure-drawing/SKILL.md` for future agents drawing or reviewing ANNS research figures.

Updated `CACHE.md` and `index.md` so the new figure cache, figure guide, and skill are discoverable.

Unresolved questions: future work should add cropped single-figure assets and paper-local figure templates once a concrete target paper repository is available.

## [2026-05-10 18:40] ingest | SIMD and vectorization execution-layer papers

Ingested three inbox PDFs and moved them into organized sources: `raw/sources/papers/simd-investments-2020.pdf`, `raw/sources/papers/fastlanes-2023.pdf`, and `raw/sources/papers/compiled-vectorized-queries-2018.pdf`.

Created source notes: `wiki/source-notes/simd-investments-2020.md`, `wiki/source-notes/fastlanes-2023.md`, and `wiki/source-notes/compiled-vectorized-queries-2018.md`.

Created entity pages: `wiki/entities/simd-investments.md`, `wiki/entities/fastlanes.md`, and `wiki/entities/compiled-vectorized-queries.md`.

Created topic page: `wiki/topics/simd-and-vectorization-for-ann-systems.md`, connecting database SIMD/vectorized execution papers to ANN system concerns such as distance kernels, compressed scans, filtered search, cache-aware batching, and irregular graph traversal.

Updated `wiki/topics/approximate-nearest-neighbor-search.md` and `index.md` so the new execution-layer branch is discoverable.

Working synthesis: SIMD/vectorization should be treated as an execution-layer issue for ANN systems. Dense scans and compressed decoding are SIMD-friendly; sparse graph traversal, selection vectors, and branch-heavy filters can erase SIMD gains unless the layout and pipeline are designed for them.

Unresolved questions: identify ANN-specific SIMD/vectorization papers and libraries worth downloading next, especially work on SIMDized distance kernels, SIMD compression/posting-list decoding, and CPU vector search implementations.

## [2026-05-10 18:48] query | SIMD and scalar quantization inbox expansion

Researched and downloaded a new `raw/inbox/` queue for ANN SIMD/vectorization and scalar/bit quantization papers.

Downloaded ANN/PQ SIMD and vectorized execution candidates: `raw/inbox/pq-fast-scan-2015.pdf`, `raw/inbox/quicker-adc-2019.pdf`, `raw/inbox/rethinking-simd-vectorization-2015.pdf`, `raw/inbox/simd-posting-list-decoding-2011.pdf`, `raw/inbox/simd-compression-intersection-2014.pdf`, and `raw/inbox/stream-vbyte-2017.pdf`.

Downloaded scalar/bit quantization and quantization-plus-graph candidates: `raw/inbox/rabitq-extension-2024.pdf`, `raw/inbox/low-precision-quantization-knn-2021.pdf`, `raw/inbox/norm-explicit-quantization-mips-2020.pdf`, `raw/inbox/quantization-to-speedup-ann-2024.pdf`, `raw/inbox/symphonyqg-2024.pdf`, `raw/inbox/aqr-hnsw-2026.pdf`, `raw/inbox/quantization-enhanced-hnsw-lavq-2025.pdf`, and `raw/inbox/information-theoretic-binarization-vector-search-2026.pdf`.

Created `wiki/analyses/simd-scalar-quantization-inbox-candidates.md` and updated `index.md` so the next ingest pass has a prioritized queue and caveats. The strongest immediate ingest targets are PQ Fast Scan, Quicker ADC, the RaBitQ multi-bit extension, Low-Precision Quantization for KNN, and Norm-Explicit Quantization for MIPS.

Unresolved questions: whether scalar quantization should become a standalone topic page after ingest, and whether the user's ANNS systems work should prioritize HNSW traversal quantization, IVF/PQ reranking quantization, or compressed raw-vector storage.

## [2026-05-10 19:02] ingest | SIMD and scalar quantization inbox batch

Ingested the `raw/inbox/` batch recorded in `wiki/analyses/simd-scalar-quantization-inbox-candidates.md` and moved the PDFs into `raw/sources/papers/`.

Created source notes for PQ/ADC SIMD and compressed-list execution: `wiki/source-notes/pq-fast-scan-2015.md`, `wiki/source-notes/quicker-adc-2019.md`, `wiki/source-notes/rethinking-simd-vectorization-2015.md`, `wiki/source-notes/simd-based-decoding-posting-lists-2011.md`, `wiki/source-notes/simd-compression-intersection-2014.md`, and `wiki/source-notes/stream-vbyte-2017.md`.

Created source notes for scalar/binary and graph-integrated quantization: `wiki/source-notes/low-precision-quantization-knn-2021.md`, `wiki/source-notes/norm-explicit-quantization-mips-2020.md`, `wiki/source-notes/quantization-to-speedup-ann-2024.md`, `wiki/source-notes/symphonyqg-2024.md`, `wiki/source-notes/aqr-hnsw-2026.md`, `wiki/source-notes/quantization-enhanced-hnsw-lavq-2025.md`, and `wiki/source-notes/information-theoretic-binarization-vector-search-2026.md`.

Created entity pages for the new methods/papers and a new topic page: `wiki/topics/scalar-and-binary-quantization-for-ann.md`. Updated `wiki/topics/simd-and-vectorization-for-ann-systems.md`, `wiki/topics/vector-quantization.md`, `wiki/topics/approximate-nearest-neighbor-search.md`, `wiki/overview/vector-quantization-research-overview.md`, `wiki/entities/product-quantization.md`, `wiki/entities/rabitq.md`, `wiki/source-notes/rabitq-extension-2024.md`, `wiki/analyses/simd-scalar-quantization-inbox-candidates.md`, and `index.md`.

Working synthesis: ANN quantization should now be treated as both a compression method and an execution path. PQ/ADC needs in-register lookup and layout-aware SIMD. Scalar quantization needs careful range/norm handling and can become a traversal-time distance estimator, not just a storage-saving format. Graph-plus-quantization methods need layout, graph degree, and reranking policy co-designed with the SIMD batch kernel.

Unresolved questions: the mature sources are PQ Fast Scan, Quicker ADC, RaBitQ extension, Low-Precision Quantization, Norm-Explicit Quantization, and SymphonyQG. AQR-HNSW, HNSW-LAVQ, and Information-Theoretic Binarization remain low-confidence exploratory sources until independently validated.

## [2026-05-19 07:59] ingest | Flash graph indexing and Panorama refinement

Ingested two inbox PDFs without moving or renaming the immutable raw files: `raw/inbox/flash-graph-indexing-2025.pdf` and `raw/inbox/panorama-2025.pdf`.

Created source notes: `wiki/source-notes/flash-graph-indexing-2025.md` and `wiki/source-notes/panorama-2025.md`.

Created entity pages: `wiki/entities/flash-graph-indexing.md` and `wiki/entities/panorama.md`.

Updated synthesis and navigation pages: `wiki/topics/approximate-nearest-neighbor-search.md`, `wiki/topics/simd-and-vectorization-for-ann-systems.md`, `wiki/topics/scalar-and-binary-quantization-for-ann.md`, `wiki/entities/hnsw.md`, `CACHE.md`, and `index.md`.

Working synthesis: Flash adds a graph-construction acceleration branch for HNSW-style indexes, while Panorama adds an exact-refinement acceleration branch for candidate verification. Both are CPU execution-layer papers, but they optimize different lifecycle stages: build-time graph formation versus query-time final scoring.

Unresolved questions: verify final publication metadata for both inbox PDFs before formal citation; decide whether to move these PDFs from `raw/inbox/` to organized `raw/sources/papers/` only if raw-file mutation is explicitly requested.

## [2026-05-26 21:05] query | ANNS section writing exemplars

Created `wiki/analyses/anns-section-writing-exemplars/` as a section-by-section writing-quality audit of the ANNS systems literature in the vault.

Added a summary matrix and focused notes for abstract, introduction, background/preliminaries, motivation/characterization, system overview/architecture, core design/algorithms, implementation, evaluation, related work, and discussion/conclusion.

Working synthesis: the best writing models are not the most famous papers globally. Starling is the strongest introduction/design/discussion model, SPFresh is the strongest abstract/implementation/evaluation model, VBASE is the strongest conceptual/background/related-work model, and GustANN is the strongest hardware-characterization model.

Updated `index.md` so the new analysis folder is discoverable.

Unresolved questions: if this analysis is used for an actual paper draft, the next pass should turn each exemplar into a concrete section template with target paragraph roles and anti-pattern checks.

## [2026-05-27 12:40] query | ANNS section exemplar agent map

Created `wiki/analyses/anns-section-writing-exemplars/agent-writing-map/` as a future-agent writing guide derived from the section exemplar audit.

Added `AGENT_MAP.md` plus ten section-card files covering abstract, introduction, background/preliminaries, motivation/characterization, system overview/architecture, core design/algorithms, implementation, evaluation, related work, and discussion/conclusion.

Each card points to the corresponding paper section, source note, section role, argument skeleton, reusable writing move, and traps to avoid. The guide intentionally avoids copying full paper prose and instead distills writing structure.

Updated `wiki/analyses/anns-section-writing-exemplars/README.md` and `index.md` to surface the agent map.

Unresolved questions: for a concrete target paper, the next step is to turn the relevant cards into paragraph-level outlines using the user's own system claims, figures, and evaluation data.

## [2026-05-27 12:48] query | Agent map style-first reading protocol

Updated `wiki/analyses/anns-section-writing-exemplars/agent-writing-map/AGENT_MAP.md` so future agents are instructed to read original paper sections before reading the distilled cards.

Added an "Original Section Targets" table mapping each target paper section to the raw PDF section to study first, then the corresponding card file.

Added a writing-technique checklist covering opening moves, narrowing, contrast, evidence placement, contribution staging, and scope control.

Working synthesis: the section cards should guide and compress learning, but the agent must first study the original section to absorb writing rhythm, argument pacing, and reviewer-facing rhetorical technique.

## [2026-05-27 19:09] query | SIMD vectorization and batch ANNS implementation map

Created `wiki/analyses/simd-vectorization-anns-implementation-map/` as a specialized future-agent entry point for writing ANNS implementation material on SIMD, vectorized execution, query batching, graph layout, compressed-code scanning, and reranking.

Added `AGENT_MAP.md`, `paper-evaluation.md`, and `chapter-blueprint.md`.

Working synthesis: the central papers are PQ Fast Scan, Quicker ADC, Milvus, SymphonyQG, and Flash Graph Indexing. FastLanes, SIMD Investments, Compiled/Vectorized Queries, and Rethinking SIMD provide execution-model support. Posting-list SIMD papers are useful only for ID/filter/list paths. GPU papers such as FAISS GPU and RUMMY should be used as batch/scheduling analogies, not CPU SIMD evidence.

Updated `wiki/topics/simd-and-vectorization-for-ann-systems.md`, `wiki/analyses/anns-section-writing-exemplars/agent-writing-map/AGENT_MAP.md`, and `index.md` so future agents can find the specialized map.

Unresolved questions: for a concrete target chapter, the next step is to map the user's own ANNS pipeline stages to these mechanisms and decide which figures are needed.

## [2026-05-29 05:20] ingest | OdinANN direct-insert SSD graph ANN

Ingested Hao Guo and Youyou Lu's FAST 2026 paper `OdinANN: Direct Insert for Consistently Stable Performance in Billion-Scale Graph-Based Vector Search` from <https://www.usenix.org/system/files/fast26-guo.pdf>.

Stored the PDF at `raw/sources/papers/odinann-2026.pdf`.

Created `wiki/source-notes/odinann-2026.md` and `wiki/entities/odinann.md`.

Updated `wiki/topics/approximate-nearest-neighbor-search.md`, `wiki/topics/second-tier-memory-for-vector-search.md`, `wiki/topics/ann-benchmarking-methodology.md`, `wiki/entities/diskann.md`, `wiki/entities/spfresh.md`, `CACHE.md`, and `index.md`.

Working synthesis: OdinANN extends the SSD-resident graph-ANN branch from static DiskANN-style serving to online direct inserts. Its main trade-off is SSD space/write amplification for lower peak DRAM and more stable search latency than buffered-insert merge designs. It is the graph-based counterpart to SPFresh's cluster-based fresh-update story.

Unresolved questions: whether OdinANN-style direct insert can combine with segment/block layouts such as Starling, how to benchmark SSD write amplification/endurance for dynamic graph ANN, and what update-mix benchmark should become the default for fresh ANN systems.

## [2026-05-29 13:46] query | Complete ANNS section exemplar refresh

Refreshed `wiki/analyses/anns-section-writing-exemplars/` after scanning all 65 current source-note pages in the vault.

Added `coverage-audit.md` to record which papers were direct candidates, supporting ANNS context, adjacent execution/hardware/database context, or excluded as non-ANNS.

Added `optimization-execution-layer.md` as a missing section category for SIMD/vectorization, cache-aware batching, graph construction optimization, and execution-layer implementation writing.

Updated the section winner matrix and revised the Top 3 files for abstract, introduction, background/preliminaries, motivation/characterization, method/core design, implementation, evaluation, related work, and discussion/conclusion.

Working synthesis: SPFresh remains the best abstract/evaluation model; Starling remains the best introduction/method/discussion model; OdinANN is now a top-tier model for dynamic graph-update abstract, introduction, motivation, implementation, evaluation, related work, and discussion; PQ Fast Scan, Milvus, and Flash anchor the new optimization/execution-layer category.

Updated `index.md` so the expanded coverage audit and optimization category are discoverable.

## [2026-05-29 14:57] query | Complete ANNS section exemplar refresh after knowledge-base update

Refreshed `wiki/analyses/anns-section-writing-exemplars/` after re-scanning all 69 current source-note pages in the vault.

Updated `coverage-audit.md` from 65 to 69 source notes and added the newly covered direct/supporting papers: Chameleon, WARP, Integrating Vector Databases Across Embedding Models, and Multi-Probe LSH.

Revised the section Top 3 rankings under a stricter SIGMOD/VLDB systems-review lens. Chameleon now affects introduction, background, motivation, architecture, optimization, implementation, related work, and discussion. WARP now affects abstract, motivation, method, optimization, and evaluation. Integrating Vector Databases now affects introduction and background. Multi-Probe LSH is recorded as an important classical supporting source, but not a modern writing template.

Updated `README.md`, the individual section ranking files, `agent-writing-map/AGENT_MAP.md`, and `index.md`.

Working synthesis: the best papers are not the same for every section. Starling remains the strongest disk/index introduction and core design model, SPFresh remains the strongest update/evaluation model, Chameleon is now the strongest heterogeneous service-architecture model, WARP is now the strongest retrieval execution-layer model, and Integrating Vector Databases is the strongest conceptual vector-DB framing model. Multi-Probe LSH remains technically foundational but stylistically dated.

Unresolved questions: if the next task is drafting a concrete paper section, the agent should read the original paper sections named in `agent-writing-map/AGENT_MAP.md` before using the distilled cards.

## [2026-05-29 15:09] query | Expand ANNS section exemplar rankings to Top 5

Expanded `wiki/analyses/anns-section-writing-exemplars/` from Top 3 to Top 5 rankings for every major paper section: abstract, introduction, background/preliminaries, motivation/characterization, system overview/architecture, method/core design, optimization/execution layer, implementation, evaluation, related work, and discussion/conclusion.

Updated the main section winner matrix, each individual section ranking file, `coverage-audit.md`, and `agent-writing-map/AGENT_MAP.md`.

Working synthesis: the Top 5 expansion makes the rankings more honest rather than more generous. The first three entries remain the best templates for most use cases; the fourth and fifth entries are often conditional models that should be copied only when the target paper shares their narrow setting, such as RALM serving, dynamic graph updates, vector-DB interoperability, multi-vector retrieval, or disk-layout architecture.

Unresolved questions: the older numbered card files under `agent-writing-map/` still mainly reflect the earlier compressed card set. Future agents should treat the ranking files and `AGENT_MAP.md` as authoritative when the cards disagree.
## [2026-05-29 15:23] query | Refresh ANNS agent writing cards for Top 5 rankings

- Updated the ANNS section-writing card files under `wiki/analyses/anns-section-writing-exemplars/agent-writing-map/` so each numbered cards file now begins with a current Top 5 card index.
- Preserved the older detailed cards as legacy style-learning notes instead of deleting them, because they still capture useful writing moves but are no longer authoritative rankings.
- Updated `AGENT_MAP.md` to tell future agents that ranking files and the new Top 5 card indexes override any stale detailed card.
- Unresolved: the optimization/execution-layer section still points to the separate SIMD/batch map rather than a numbered card file, which is intentional because that topic needs mechanism-level implementation guidance.
## [2026-05-30 13:36] query | Build ANNS Top 3 section-writing HTML navigator

- Created `wiki/analyses/anns-section-writing-exemplars/top3-section-writing-navigator.html`, a standalone dark academic dashboard for navigating each section's best three exemplar papers.
- Added PDF links, source-note links, ranking-file links, exact section targets, paraphrased writing moves, and do-not-copy warnings for 33 section/paper cards.
- Updated `wiki/analyses/anns-section-writing-exemplars/README.md` and `index.md` so the navigator is discoverable.
- Copyright/sourcing constraint: the page intentionally avoids reproducing long paper-section text; it points to local PDFs for original text and gives safe writing-method summaries.
## [2026-06-01 12:31] query | Regenerate Top 4 ANNS section excerpt PDFs with boundary-page rule

- Created and then corrected `wiki/analyses/anns-section-writing-exemplars/top4-section-excerpts/` as a per-section folder of Top 4 paper excerpt PDFs.
- Regenerated all 44 excerpt PDFs using the boundary-page rule: start on the physical PDF page where the target section appears and end on the physical PDF page where the next chapter or subsection opens.
- Fixed the `02-introduction/` excerpts in particular so Starling, Integrating Vector DBs, Chameleon, and OdinANN include the full introduction tail plus the next-section opening page.
- Updated the exemplar README and root index with a direct entry to the excerpt folder.
- Constraint: excerpts are PDFs for private vault reading rather than raw-text markdown dumps, avoiding long verbatim reproduction in wiki text.

## [2026-06-01 20:01] query | Merge ANNS background and motivation agent cards

- Re-read ANNS-related source notes and checked raw PDF headings for papers with true combined Background and Motivation sections.
- Replaced `wiki/analyses/anns-section-writing-exemplars/agent-writing-map/03-background-cards.md` with one ranked Background & Motivation card covering OdinANN, FusionANNS, Chameleon, RUMMY, Flash Graph Indexing, SmartANNS, and AQR-HNSW.
- Replaced `wiki/analyses/anns-section-writing-exemplars/agent-writing-map/04-motivation-cards.md` with a compatibility pointer to the canonical card so future agents do not use a separate motivation card.
- Updated `agent-writing-map/AGENT_MAP.md` so future agents read the original combined sections first and route to the canonical card.
- Working synthesis: the best combined background/motivation model is OdinANN, followed by FusionANNS and Chameleon. AQR-HNSW matches the section-title filter but should be treated as a low-confidence negative example rather than a style exemplar.

## [2026-06-01 20:36] query | Expand ANNS section excerpt PDFs to Top 5 and audit boundaries

- Expanded `wiki/analyses/anns-section-writing-exemplars/top4-section-excerpts/` from 44 Top 4 PDFs to 55 Top 5 PDFs while keeping the path stable for existing links.
- Regenerated every excerpt with a stricter minimal-page boundary rule: keep the next heading page only when it shares the target section tail; do not include a fresh page that belongs only to the next section.
- Added `boundary-audit.md` with a per-PDF audit table for all 55 excerpts.
- Corrected overlong or ambiguous excerpts including Chameleon motivation, Starling motivation, Starling architecture, Integrating Vector DBs method, and Milvus implementation; visual inspection trimmed Milvus before the Applications section.
- Recompressed oversized Integrating Vector DB excerpts after regeneration.
- Updated the exemplar README and root index to point to the Top 5 excerpt set.

## [2026-06-01 20:22] query | Rename ANNS excerpts to Top 5 and merge background motivation

- Renamed `wiki/analyses/anns-section-writing-exemplars/top4-section-excerpts/` to `wiki/analyses/anns-section-writing-exemplars/top5-section-excerpts/`.
- Removed the old split excerpt folders `03-background-preliminaries/` and `04-motivation-characterization/` because the requested target is one combined Background & Motivation chapter, not standalone preliminary or characterization sections.
- Added `top5-section-excerpts/03-background-motivation/` with only the Top 5 combined Background & Motivation excerpts from the canonical card: OdinANN, FusionANNS, Chameleon, RUMMY, and Flash Graph Indexing.
- Corrected the RUMMY excerpt to pages `3-5` after rendering showed page `2` contained only title/abstract/introduction content before the target Section 2 page.
- Deleted `wiki/analyses/anns-section-writing-exemplars/agent-writing-map/04-motivation-cards.md` and removed its agent-map references.
- Updated `03-background-cards.md`, `AGENT_MAP.md`, `README.md`, `boundary-audit.md`, and `index.md` so future agents use the combined Top 5 Background & Motivation package.
