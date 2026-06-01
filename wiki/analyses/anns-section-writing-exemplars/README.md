---
id: anns-section-writing-exemplars
type: analysis
status: active
created: 2026-05-26
updated: 2026-05-30
tags: [anns, paper-writing, systems, section-exemplars]
source_count: 69
sources:
  - wiki/source-notes/
related:
  - approximate-nearest-neighbor-search
  - anns-research-figure-design-guide
  - simd-vectorization-anns-implementation-map
confidence: medium
---

# ANNS Section Writing Exemplars

This folder ranks the best section-level writing examples among the current ANNS-related papers in the vault. The lens is deliberately harsh: a good section is not the one with the most impressive system, but the one that would make a systems reviewer understand the problem, mechanism, evidence, and scope with the least friction.

## Scope

Coverage audit: [ANNS Section Coverage Audit](coverage-audit.md). I scanned all 69 current source-note pages and separated direct ANNS exemplars from supporting quantization, graph-theory, SIMD, benchmark, vector-database, and hardware-context papers.

Primary section-template candidates are now [SPFresh](../../source-notes/spfresh-2023.md), [Starling](../../source-notes/starling-2024.md), [OdinANN](../../source-notes/odinann-2026.md), [VBASE](../../source-notes/vbase-2023.md), [Milvus](../../source-notes/milvus-2021.md), [GustANN](../../source-notes/gustann-2025.md), [Chameleon](../../source-notes/chameleon-ralm-vector-search-2024.md), [WARP](../../source-notes/warp-multi-vector-retrieval-2025.md), [Integrating Vector Databases](../../source-notes/integrating-vector-databases-embedding-models-2026.md), [PQ Fast Scan](../../source-notes/pq-fast-scan-2015.md), and [Flash Graph Indexing](../../source-notes/flash-graph-indexing-2025.md).

Important supporting references include [DiskANN](../../source-notes/diskann-2019.md), [SPANN](../../source-notes/spann-2021.md), [RUMMY](../../source-notes/rummy-2024.md), [SmartANNS](../../source-notes/smartanns-2024.md), [CXL-ANNS](../../source-notes/cxl-anns-2024.md), [d-HNSW](../../source-notes/d-hnsw-2025.md), [ANSMET](../../source-notes/ansmet-2025.md), [SVFusion](../../source-notes/svfusion-2026.md), [Multi-Probe LSH](../../source-notes/multi-probe-lsh-2007.md), [ANN-Benchmarks](../../source-notes/ann-benchmarks-2018.md), and [Graph-Based ANNS Survey](../../source-notes/graph-based-anns-survey-2021.md). These are useful, but not always the best prose templates.

## Selection Criteria

I rewarded sections that do five things well: define the real bottleneck, narrow the scope honestly, map design choices to evidence, make reviewer objections easy to answer, and avoid pretending that scale alone is a contribution.

I penalized sections that overclaim, hide assumptions, blur algorithmic novelty with systems engineering, depend on too many moving parts without a crisp thesis, present hardware results without enough generalizable reasoning, or use "vector database" as branding without a clean database/system abstraction.

## Section Winners

| Section | Best | Second | Third | Fourth | Fifth | Brutal reviewer note |
|---|---|---|---|---|---|---|
| [Abstract](abstract.md) | SPFresh | WARP | OdinANN | Chameleon | Starling | The top abstracts state a precise pain, name a mechanism, and give scoped evidence; Chameleon and Starling are strong but less reusable. |
| [Introduction](introduction.md) | Starling | Integrating Vector DBs | Chameleon | OdinANN | VBASE | The best introductions create a missing-system capability, not just a bigger benchmark. VBASE is excellent but too interface-specific for broad copying. |
| [Background / Preliminaries](background-preliminaries.md) | VBASE | Chameleon | Integrating Vector DBs | Starling | OdinANN | Good background teaches exactly the abstraction that later breaks; survey-style completeness is not rewarded. |
| [Motivation / Characterization](motivation-characterization.md) | GustANN | Chameleon | WARP | OdinANN | Starling | The winners measure the bottleneck before selling the system. Starling is cleaner than many papers but narrower than the higher-ranked models. |
| [System Overview / Architecture](system-overview-architecture.md) | Milvus | Chameleon | SPFresh | FusionANNS | Starling | Architecture winners make placement and control flow explicit. FusionANNS is demoted because the premise carries too much load. |
| [Method / Core Design](core-design-algorithms.md) | Starling | WARP | SPFresh | OdinANN | Integrating Vector DBs | Method quality means design inevitability. Integrating Vector DBs is formally strong but not an ANNS execution template. |
| [Optimization / Execution Layer](optimization-execution-layer.md) | PQ Fast Scan | WARP | Chameleon | Milvus | Flash | PQ Fast Scan remains the cleanest optimization prose; Flash is valuable but too construction-specific to rank higher. |
| [Implementation](implementation.md) | SPFresh | Chameleon | OdinANN | GustANN | Milvus | Implementation prose should justify constraints. Milvus is broad and mature, but too system-wide for a focused implementation template. |
| [Evaluation](evaluation.md) | SPFresh | OdinANN | WARP | Starling | Chameleon | SPFresh/OdinANN win because they evaluate bad regimes, not just speedups. Chameleon is strong but partly synthetic and accelerator-specific. |
| [Related Work](related-work.md) | VBASE | Chameleon | OdinANN | GustANN | WARP | The best related work maps non-overlap by technical constraint. WARP is useful only if the target paper touches neural/multi-vector retrieval. |
| [Discussion / Conclusion](discussion-conclusion.md) | Starling | GustANN | Chameleon | OdinANN | WARP | Starling/GustANN are the only clearly mature discussion models. WARP is concise and honest, but barely a discussion section. |

## Brutal Exclusions

DiskANN is foundational, but it is no longer the best section-writing template for a new paper. Use it for substance, not for modern rhetorical structure.

SPANN is important and generally clear, but Starling and SPFresh write the disk-resident system story with sharper bottleneck-to-design linkage.

BANG is technically relevant, but the writing is not as clean as GustANN or RUMMY for explaining GPU memory pressure and host-device cooperation.

CXL-ANNS, d-HNSW, and ANSMET are useful for second-tier memory context, but they are too hardware-specialized or too diffuse to be the top writing models for a general ANNS systems paper.

SVFusion is interesting but not a top exemplar yet. It has too many interacting claims and should be treated cautiously until the publication status and evaluation maturity are clearer.

Flash and Panorama are strong execution-layer papers, but they are narrower than the system papers ranked here. Use them for SIMD/refinement ideas, not for overall ANNS systems paper structure.

Multi-Probe LSH is historically important and has a clean classical problem statement, but the 2007 prose style is not a modern SIGMOD/VLDB systems writing template.

Integrating Vector Databases is a top-tier conceptual/vector-DB paper, but it is not an ANNS performance paper. Copy its introduction style only if the new paper has a real data-management abstraction, not just a faster index.

ScaNN, PQ, RaBitQ, PQ Fast Scan, Quicker ADC, Flash, and SymphonyQG are important for method or optimization sections. They are not automatically good full-paper section templates because they are often narrower than systems papers.

ANN-Benchmarks and Graph-Based ANNS Survey are excellent for evaluation methodology and background taxonomy. They are not top templates for system introductions because they survey the field rather than introduce a new system.

## How To Use This Folder

For future agents, start with [Agent Map: ANNS Section Writing Exemplars](agent-writing-map/AGENT_MAP.md). It turns the rankings here into section cards with source pointers, argument skeletons, reusable writing moves, and traps to avoid.

For a faster visual workflow, open [Top 3 Section Writing Navigator](top3-section-writing-navigator.html). It turns the best three papers per section into a navigable HTML dashboard with PDF links, source-note links, section targets, writing moves, and warnings.

For direct original-section reading, open [Top 4 Section Excerpts](top4-section-excerpts/README.md). It contains boundary-cropped PDFs for each section's best four papers. Each excerpt starts on the page where the target section appears and ends on the page where the next chapter or subsection opens, so two-column section tails are not accidentally cut off.

When drafting a new paper, do not copy one whole paper's structure. Instead, assemble a section-by-section template: Starling-style introduction, VBASE/Chameleon-style background hook, GustANN-style motivation, Starling/WARP-style method, PQ Fast Scan/WARP-style optimization, SPFresh-style implementation/evaluation, and Starling/GustANN-style discussion.

The main writing lesson is that the best papers make the reviewer feel that every design decision was forced by a previously demonstrated bottleneck. The weaker papers ask the reviewer to trust that the system is important because the system is large or the hardware is fashionable.
