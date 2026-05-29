---
id: anns-section-exemplars-system-overview-architecture
type: analysis
status: active
created: 2026-05-26
updated: 2026-05-29
tags: [anns, paper-writing, system-overview, architecture]
source_count: 5
sources:
  - raw/sources/papers/milvus-2021.pdf
  - raw/inbox/chameleon-ralm-vector-search-vldb-best-scalable-data-science-2025.pdf
  - raw/sources/papers/spfresh-2023.pdf
  - raw/sources/papers/fusionanns-2025.pdf
  - raw/sources/papers/starling-2024.pdf
related:
  - anns-section-writing-exemplars
confidence: medium
---

# System Overview / Architecture Exemplars

## Top Five

| Rank | Paper | Score | Why it works | Weakness |
|---|---:|---:|---|---|
| 1 | [Milvus](../../source-notes/milvus-2021.md) | 9.2 | Best full-system overview. It cleanly separates query engine, GPU/CPU execution, storage, dynamic data, and system APIs. | It is a production DBMS paper, so the architecture is broader than most focused ANNS papers need. |
| 2 | [Chameleon](../../source-notes/chameleon-ralm-vector-search-2024.md) | 9.1 | Best heterogeneous/disaggregated architecture overview. It separates ChamLM, ChamVS.idx, ChamVS.mem, and CPU coordination, then walks the retrieval/inference dataflow. | It is an RALM architecture, not a general vector DBMS or graph-index architecture. |
| 3 | [SPFresh](../../source-notes/spfresh-2023.md) | 9.0 | Best update-oriented architecture. The Foreground Updater, Local Rebuilder, and Block Controller map directly to freshness and in-place update requirements. | It is tightly coupled to LIRE and disk-update semantics. |
| 4 | [FusionANNS](../../source-notes/fusionanns-2025.md) | 8.8 | It gives a useful multi-tier placement story: SSD raw vectors, GPU compressed vectors, host graph/IDs, filtering, and reranking. | The overview relies too much on accepting the multi-tier premise before the reader sees enough evidence. |
| 5 | [Starling](../../source-notes/starling-2024.md) | 8.7 | Its architecture is disciplined around segment-level disk graph search, in-memory navigation, block shuffling, and block search. | It is a framework layout more than a full-system architecture; copying it for broad systems papers would under-specify control flow. |

## What To Steal

Draw the architecture around data placement and control flow, not around module names.

For each component, say what bottleneck it removes. A box named "scheduler" is not meaningful unless the reader knows what it schedules and why order matters.

Separate offline construction, online query serving, update handling, and recovery paths when they exist. SPFresh does this better than most.

Chameleon is the best new architecture model when the contribution is a placement and orchestration argument. Its overview works because the accelerator split is justified before the module list appears.

## What Not To Copy

Do not use one giant architecture figure with every thread, queue, cache, and data structure. Reviewers need the invariant first, details later.

Do not pretend a focused paper is a full vector database. Milvus can do this because that is the paper; most ANNS systems should not.

Do not hide data movement. For SSD/GPU/CXL papers, bytes crossing tiers are often the actual system.

FusionANNS and Starling are useful architecture references, but they should be copied only when the paper's contribution is actually tier placement or disk-layout organization.
