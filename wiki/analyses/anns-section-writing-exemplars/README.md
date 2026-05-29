---
id: anns-section-writing-exemplars
type: analysis
status: active
created: 2026-05-26
updated: 2026-05-29
tags: [anns, paper-writing, systems, section-exemplars]
source_count: 65
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

Coverage audit: [ANNS Section Coverage Audit](coverage-audit.md). I scanned all 65 current source-note pages and separated direct ANNS exemplars from supporting quantization, graph-theory, SIMD, benchmark, and hardware-context papers.

Primary section-template candidates are now [SPFresh](../../source-notes/spfresh-2023.md), [Starling](../../source-notes/starling-2024.md), [OdinANN](../../source-notes/odinann-2026.md), [VBASE](../../source-notes/vbase-2023.md), [Milvus](../../source-notes/milvus-2021.md), [GustANN](../../source-notes/gustann-2025.md), [FusionANNS](../../source-notes/fusionanns-2025.md), [PQ Fast Scan](../../source-notes/pq-fast-scan-2015.md), and [Flash Graph Indexing](../../source-notes/flash-graph-indexing-2025.md).

Important supporting references include [DiskANN](../../source-notes/diskann-2019.md), [SPANN](../../source-notes/spann-2021.md), [RUMMY](../../source-notes/rummy-2024.md), [SmartANNS](../../source-notes/smartanns-2024.md), [CXL-ANNS](../../source-notes/cxl-anns-2024.md), [d-HNSW](../../source-notes/d-hnsw-2025.md), [ANSMET](../../source-notes/ansmet-2025.md), [SVFusion](../../source-notes/svfusion-2026.md), [ANN-Benchmarks](../../source-notes/ann-benchmarks-2018.md), and [Graph-Based ANNS Survey](../../source-notes/graph-based-anns-survey-2021.md). These are useful, but not always the best prose templates.

## Selection Criteria

I rewarded sections that do four things well: define the real bottleneck, narrow the scope honestly, map design choices to evidence, and make reviewer objections easy to answer.

I penalized sections that overclaim, hide assumptions, blur algorithmic novelty with systems engineering, depend on too many moving parts without a crisp thesis, or present hardware results without enough generalizable reasoning.

## Section Winners

| Section | Best | Second | Third | Brutal reviewer note |
|---|---|---|---|---|
| [Abstract](abstract.md) | SPFresh | OdinANN | Starling | OdinANN enters the top tier after full coverage because its abstract states a clean buffered-insert failure and direct-insert fix. |
| [Introduction](introduction.md) | Starling | OdinANN | VBASE | Starling remains the best system-problem cascade; OdinANN is the clearest new update-stability intro. |
| [Background / Preliminaries](background-preliminaries.md) | VBASE | Starling | OdinANN | OdinANN replaces SmartANNS because its background directly teaches on-disk graph operations and update failure modes. |
| [Motivation / Characterization](motivation-characterization.md) | GustANN | OdinANN | Starling | GustANN still wins hardware characterization; OdinANN is now the best dynamic-workload characterization. |
| [System Overview / Architecture](system-overview-architecture.md) | Milvus | SPFresh | FusionANNS | Milvus is still the cleanest full-system architecture model; newer papers are narrower. |
| [Method / Core Design](core-design-algorithms.md) | Starling | SPFresh | OdinANN | VBASE is still the best formal abstraction, but OdinANN is the better ANNS method template after full coverage. |
| [Optimization / Execution Layer](optimization-execution-layer.md) | PQ Fast Scan | Milvus | Flash | This category was missing before; it is essential for SIMD/vectorization, batching, and construction optimization. |
| [Implementation](implementation.md) | SPFresh | OdinANN | GustANN | OdinANN now outranks Milvus for implementation prose because it ties layout, concurrency, and recovery to the update claim. |
| [Evaluation](evaluation.md) | SPFresh | OdinANN | Starling | OdinANN adds the best dynamic graph-update evaluation; GustANN remains the best hardware-throughput honorable mention. |
| [Related Work](related-work.md) | VBASE | OdinANN | GustANN | OdinANN has unusually clean positioning across hybrid storage, compression, and update-capable ANNS. |
| [Discussion / Conclusion](discussion-conclusion.md) | Starling | GustANN | OdinANN | OdinANN is now the third-best discussion model because it owns consistency, GC-free updates, insert latency, and memory usage. |

## Brutal Exclusions

DiskANN is foundational, but it is no longer the best section-writing template for a new paper. Use it for substance, not for modern rhetorical structure.

SPANN is important and generally clear, but Starling and SPFresh write the disk-resident system story with sharper bottleneck-to-design linkage.

BANG is technically relevant, but the writing is not as clean as GustANN or RUMMY for explaining GPU memory pressure and host-device cooperation.

CXL-ANNS, d-HNSW, and ANSMET are useful for second-tier memory context, but they are too hardware-specialized or too diffuse to be the top writing models for a general ANNS systems paper.

SVFusion is interesting but not a top exemplar yet. It has too many interacting claims and should be treated cautiously until the publication status and evaluation maturity are clearer.

Flash and Panorama are strong execution-layer papers, but they are narrower than the system papers ranked here. Use them for SIMD/refinement ideas, not for overall ANNS systems paper structure.

ScaNN, PQ, RaBitQ, PQ Fast Scan, Quicker ADC, Flash, and SymphonyQG are important for method or optimization sections. They are not automatically good full-paper section templates because they are often narrower than systems papers.

ANN-Benchmarks and Graph-Based ANNS Survey are excellent for evaluation methodology and background taxonomy. They are not top templates for system introductions because they survey the field rather than introduce a new system.

## How To Use This Folder

For future agents, start with [Agent Map: ANNS Section Writing Exemplars](agent-writing-map/AGENT_MAP.md). It turns the rankings here into section cards with source pointers, argument skeletons, reusable writing moves, and traps to avoid.

When drafting a new paper, do not copy one whole paper's structure. Instead, assemble a section-by-section template: Starling-style introduction, VBASE-style background hook, GustANN-style motivation, SPFresh-style implementation/evaluation, and Starling/GustANN-style discussion.

The main writing lesson is that the best papers make the reviewer feel that every design decision was forced by a previously demonstrated bottleneck. The weaker papers ask the reviewer to trust that the system is important because the system is large or the hardware is fashionable.
