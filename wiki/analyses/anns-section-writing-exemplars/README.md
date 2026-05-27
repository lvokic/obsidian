---
id: anns-section-writing-exemplars
type: analysis
status: active
created: 2026-05-26
updated: 2026-05-26
tags: [anns, paper-writing, systems, section-exemplars]
source_count: 20
sources:
  - raw/sources/papers/diskann-2019.pdf
  - raw/sources/papers/spann-2021.pdf
  - raw/sources/papers/milvus-2021.pdf
  - raw/sources/papers/vbase-2023.pdf
  - raw/sources/papers/spfresh-2023.pdf
  - raw/sources/papers/starling-2024.pdf
  - raw/sources/papers/rummy-2024.pdf
  - raw/sources/papers/bang-2024.pdf
  - raw/sources/papers/smartanns-2024.pdf
  - raw/sources/papers/cxl-anns-2024.pdf
  - raw/sources/papers/performance-index-size-dilemma-2024.pdf
  - raw/sources/papers/d-hnsw-2025.pdf
  - raw/sources/papers/ansmet-2025.pdf
  - raw/sources/papers/gustann-2025.pdf
  - raw/sources/papers/fusionanns-2025.pdf
  - raw/sources/papers/svfusion-2026.pdf
  - raw/sources/papers/faiss-gpu-2017.pdf
  - raw/sources/papers/scann-2020.pdf
  - raw/inbox/flash-graph-indexing-2025.pdf
  - raw/inbox/panorama-2025.pdf
related:
  - approximate-nearest-neighbor-search
  - anns-research-figure-design-guide
confidence: medium
---

# ANNS Section Writing Exemplars

This folder ranks the best section-level writing examples among the current ANNS system papers in the vault. The lens is deliberately harsh: a good section is not the one with the most impressive system, but the one that would make a systems reviewer understand the problem, mechanism, evidence, and scope with the least friction.

## Scope

Included as primary candidates: [DiskANN](../../source-notes/diskann-2019.md), [SPANN](../../source-notes/spann-2021.md), [Milvus](../../source-notes/milvus-2021.md), [VBASE](../../source-notes/vbase-2023.md), [SPFresh](../../source-notes/spfresh-2023.md), [Starling](../../source-notes/starling-2024.md), [RUMMY](../../source-notes/rummy-2024.md), [BANG](../../source-notes/bang-2024.md), [SmartANNS](../../source-notes/smartanns-2024.md), [GustANN](../../source-notes/gustann-2025.md), [FusionANNS](../../source-notes/fusionanns-2025.md), and related memory-tier systems including [CXL-ANNS](../../source-notes/cxl-anns-2024.md), [d-HNSW](../../source-notes/d-hnsw-2025.md), [ANSMET](../../source-notes/ansmet-2025.md), and [SVFusion](../../source-notes/svfusion-2026.md).

Lower-weight references: [FAISS GPU](../../source-notes/faiss-gpu-2017.md), [ScaNN](../../source-notes/scann-2020.md), [Flash](../../source-notes/flash-graph-indexing-2025.md), and [Panorama](../../source-notes/panorama-2025.md). These are important, but they are not always the best models for a modern end-to-end ANNS systems paper.

## Selection Criteria

I rewarded sections that do four things well: define the real bottleneck, narrow the scope honestly, map design choices to evidence, and make reviewer objections easy to answer.

I penalized sections that overclaim, hide assumptions, blur algorithmic novelty with systems engineering, depend on too many moving parts without a crisp thesis, or present hardware results without enough generalizable reasoning.

## Section Winners

| Section | Best | Second | Third | Brutal reviewer note |
|---|---|---|---|---|
| [Abstract](abstract.md) | SPFresh | Starling | VBASE | SPFresh is the cleanest abstract because it compresses problem, failure mode, mechanism, and result without sounding inflated. |
| [Introduction](introduction.md) | Starling | VBASE | SPFresh | Starling has the best reviewer-friendly problem cascade; VBASE has the strongest conceptual hook. |
| [Background / Preliminaries](background-preliminaries.md) | VBASE | Starling | SmartANNS | Most ANNS papers over-survey here; these three actually set up the later design. |
| [Motivation / Characterization](motivation-characterization.md) | GustANN | Starling | RUMMY | GustANN is the clearest example of turning hardware facts into a systems problem. |
| [System Overview / Architecture](system-overview-architecture.md) | Milvus | SPFresh | FusionANNS | Milvus is still the cleanest full-system architecture model; newer papers are narrower. |
| [Core Design / Algorithms](core-design-algorithms.md) | Starling | SPFresh | VBASE | Starling and SPFresh have the strongest design-to-bottleneck alignment. |
| [Implementation](implementation.md) | SPFresh | Milvus | GustANN | SPFresh wins because implementation details are not decorative; they explain correctness and update behavior. |
| [Evaluation](evaluation.md) | SPFresh | Starling | GustANN | SPFresh has the best dynamic-evaluation discipline; Starling has the cleanest disk/index ablations. |
| [Related Work](related-work.md) | VBASE | GustANN | FusionANNS | VBASE positions the interface problem best; GustANN/FusionANNS position hardware tiers clearly. |
| [Discussion / Conclusion](discussion-conclusion.md) | Starling | GustANN | RUMMY | These are the rare papers that explicitly state assumptions, limits, and transferability. |

## Brutal Exclusions

DiskANN is foundational, but it is no longer the best section-writing template for a new paper. Use it for substance, not for modern rhetorical structure.

SPANN is important and generally clear, but Starling and SPFresh write the disk-resident system story with sharper bottleneck-to-design linkage.

BANG is technically relevant, but the writing is not as clean as GustANN or RUMMY for explaining GPU memory pressure and host-device cooperation.

CXL-ANNS, d-HNSW, and ANSMET are useful for second-tier memory context, but they are too hardware-specialized or too diffuse to be the top writing models for a general ANNS systems paper.

SVFusion is interesting but not a top exemplar yet. It has too many interacting claims and should be treated cautiously until the publication status and evaluation maturity are clearer.

Flash and Panorama are strong execution-layer papers, but they are narrower than the system papers ranked here. Use them for SIMD/refinement ideas, not for overall ANNS systems paper structure.

## How To Use This Folder

For future agents, start with [Agent Map: ANNS Section Writing Exemplars](agent-writing-map/AGENT_MAP.md). It turns the rankings here into section cards with source pointers, argument skeletons, reusable writing moves, and traps to avoid.

When drafting a new paper, do not copy one whole paper's structure. Instead, assemble a section-by-section template: Starling-style introduction, VBASE-style background hook, GustANN-style motivation, SPFresh-style implementation/evaluation, and Starling/GustANN-style discussion.

The main writing lesson is that the best papers make the reviewer feel that every design decision was forced by a previously demonstrated bottleneck. The weaker papers ask the reviewer to trust that the system is important because the system is large or the hardware is fashionable.
