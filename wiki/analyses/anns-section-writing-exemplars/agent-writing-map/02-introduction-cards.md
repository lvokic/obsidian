---
id: anns-section-agent-map-introduction
type: analysis
status: active
created: 2026-05-27
updated: 2026-05-27
tags: [anns, paper-writing, introduction, agent-map]
source_count: 3
sources:
  - raw/sources/papers/starling-2024.pdf
  - raw/sources/papers/vbase-2023.pdf
  - raw/sources/papers/spfresh-2023.pdf
related:
  - anns-section-agent-writing-map
confidence: medium
---

# Introduction Cards

## Starling - Section 1 Introduction

Source pointer: [Starling source note](../../../source-notes/starling-2024.md); raw PDF Section 1, "INTRODUCTION".

Use when writing: an introduction for disk-resident graph search, vector database segments, or locality-oriented ANNS systems.

Section role: create an inevitability chain from vector data growth to segment-level disk search, then show why SPANN-like and DiskANN-like choices are each incomplete.

Argument skeleton:

1. Start from unstructured data and embedding-based retrieval, but keep this short.
2. Show that in-memory indexes fail under large-scale memory pressure.
3. Explain why vector databases partition data into segments.
4. Define the open problem at the segment level, not the whole cluster level.
5. Contrast existing disk methods as two extremes: replication-heavy clustering versus graph search with I/O inefficiency.
6. Introduce the system as the middle path: graph quality plus disk locality.
7. List contributions only after the failure mode is obvious.

Reusable writing move: Starling names the closest alternatives and makes them fail for different reasons. This is much stronger than claiming all prior work is generically slow.

Do not copy: the long vector-database segment setup unless your contribution is really about the segment as a deployment unit.

## VBASE - Section 1 Introduction

Source pointer: [VBASE source note](../../../source-notes/vbase-2023.md); raw PDF Section 1, "Introduction".

Use when writing: an introduction for vector search inside databases, hybrid relational-vector queries, or query-interface redesign.

Section role: expose a mismatch between the conventional TopK vector-index interface and database query execution.

Argument skeleton:

1. Start from online vector similarity search as a database need.
2. Show that applications rarely ask pure nearest-neighbor queries in isolation.
3. Explain that predicates, joins, and query planning require more than a fixed TopK result.
4. Identify why tentative-K approaches are fragile.
5. Introduce relaxed monotonicity as the property that lets a DBMS consume vector indexes incrementally.
6. Tie the design back to PostgreSQL integration and complex query speedups.

Reusable writing move: VBASE makes the contribution feel fundamental because it attacks the interface between index and query engine, not only the index implementation.

Do not copy: the relational framing unless your paper can state a similarly precise interface problem.

## SPFresh - Section 1 Introduction

Source pointer: [SPFresh source note](../../../source-notes/spfresh-2023.md); raw PDF Section 1, "Introduction".

Use when writing: an introduction for mutable indexes, freshness, online update paths, or storage-maintenance papers.

Section role: make index maintenance the central problem and show why rebuild-oriented systems are operationally unacceptable.

Argument skeleton:

1. Establish vector search as a core online-service component.
2. Explain that fresh vectors arrive continuously.
3. Describe why high-dimensional index updates are hard.
4. Show the conventional solution: accumulate updates separately and rebuild globally.
5. Quantify why global rebuild damages resources, latency, and accuracy.
6. Introduce local incremental rebalancing as the paper's escape route.
7. Summarize contributions around protocol, pipeline, storage engine, and evaluation.

Reusable writing move: SPFresh gives concrete real-world update rates and rebuild costs, then uses them to justify the design.

Do not copy: the "freshness" urgency unless your system actually maintains online freshness under updates.
