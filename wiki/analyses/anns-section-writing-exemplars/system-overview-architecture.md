---
id: anns-section-exemplars-system-overview-architecture
type: analysis
status: active
created: 2026-05-26
updated: 2026-05-26
tags: [anns, paper-writing, system-overview, architecture]
source_count: 3
sources:
  - raw/sources/papers/milvus-2021.pdf
  - raw/sources/papers/spfresh-2023.pdf
  - raw/sources/papers/fusionanns-2025.pdf
related:
  - anns-section-writing-exemplars
confidence: medium
---

# System Overview / Architecture Exemplars

## Top Three

| Rank | Paper | Score | Why it works | Weakness |
|---|---:|---:|---|---|
| 1 | [Milvus](../../source-notes/milvus-2021.md) | 9.2 | Best full-system overview. It cleanly separates query engine, GPU/CPU execution, storage, dynamic data, and system APIs. | It is a production DBMS paper, so the architecture is broader than most focused ANNS papers need. |
| 2 | [SPFresh](../../source-notes/spfresh-2023.md) | 9.0 | Best update-oriented architecture. The Foreground Updater, Local Rebuilder, and Block Controller map directly to freshness and in-place update requirements. | It is tightly coupled to LIRE and disk-update semantics. |
| 3 | [FusionANNS](../../source-notes/fusionanns-2025.md) | 8.8 | Strong multi-tier architecture: SSD raw vectors, GPU compressed vectors, host graph/IDs, collaborative filtering, and reranking. | The overview is easier to believe after the reader already accepts the multi-tier premise. |

## What To Steal

Draw the architecture around data placement and control flow, not around module names.

For each component, say what bottleneck it removes. A box named "scheduler" is not meaningful unless the reader knows what it schedules and why order matters.

Separate offline construction, online query serving, update handling, and recovery paths when they exist. SPFresh does this better than most.

## What Not To Copy

Do not use one giant architecture figure with every thread, queue, cache, and data structure. Reviewers need the invariant first, details later.

Do not pretend a focused paper is a full vector database. Milvus can do this because that is the paper; most ANNS systems should not.

Do not hide data movement. For SSD/GPU/CXL papers, bytes crossing tiers are often the actual system.
