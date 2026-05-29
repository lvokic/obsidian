---
id: anns-section-agent-map-related-work
type: analysis
status: active
created: 2026-05-27
updated: 2026-05-29
tags: [anns, paper-writing, related-work, agent-map]
source_count: 6
sources:
  - raw/sources/papers/vbase-2023.pdf
  - raw/inbox/chameleon-ralm-vector-search-vldb-best-scalable-data-science-2025.pdf
  - raw/sources/papers/odinann-2026.pdf
  - raw/sources/papers/gustann-2025.pdf
  - raw/inbox/warp-multi-vector-retrieval-sigir-best-paper-2025.pdf
  - raw/sources/papers/fusionanns-2025.pdf
related:
  - anns-section-agent-writing-map
confidence: medium
---

# Related Work Cards

## Current Top 5 Card Index

This index is authoritative for the current related-work ranking. The detailed cards below are retained as expanded style notes; if they conflict with this index or [Related Work Ranking](../related-work.md), follow the ranking.

| Rank | Paper | Use when | Writing move to copy | Do not copy |
|---|---|---|---|---|
| 1 | VBASE | Query-interface, vector database, and semantic abstraction papers. | Position against interfaces and semantics, not just speed. | Do not use if the paper does not change query execution semantics. |
| 2 | Chameleon | RALM/vector serving architecture papers. | Classify related work by serving bottleneck and hardware placement. | Do not reduce the contrast to "prior systems are slower." |
| 3 | OdinANN | Dynamic graph ANNS papers. | Separate static graph search, batch rebuild, and direct update work. | Do not blur update models. |
| 4 | GustANN | GPU/SSD or hardware-assisted ANNS systems. | Distinguish work by data residency and compute placement. | Do not use vague scalability language without naming the resource bottleneck. |
| 5 | WARP | Multi-vector retrieval and compressed execution. | Place retrieval-engine execution beside ANN indexing without conflating them. | Do not cite multi-vector work as if it solved ordinary vector search. |

## Legacy Detailed Cards

The detailed cards below predate the Top 5 refresh. They are still useful for studying writing moves, but they are not a complete or current ranking.

## VBASE - Section 6 Related Works

Source pointer: [VBASE source note](../../../source-notes/vbase-2023.md); raw PDF Section 6, "Related Works".

Use when writing: related work for vector database/query-interface papers.

Section role: separate low-dimensional similarity databases, vector indexes, vector database systems, and query-processing approaches.

Positioning skeleton:

1. Identify older similarity query work and why it is not enough for high-dimensional vector indexes.
2. Categorize vector indexes by interface and algorithmic family.
3. Discuss vector database systems and why integration is incomplete.
4. State the paper's non-overlap in terms of query execution semantics.

Reusable writing move: VBASE positions against interfaces and semantics, not just performance.

Do not copy: if your paper does not change query semantics.

## GustANN - Section 6 Related Work

Source pointer: [GustANN source note](../../../source-notes/gustann-2025.md); raw PDF Section 6, "Related Work".

Use when writing: related work for GPU/SSD graph ANNS papers.

Section role: separate SSD-resident ANNS from GPU ANNS and explain why the combination is distinct.

Positioning skeleton:

1. Discuss SSD-resident ANNS and their CPU/latency orientation.
2. Discuss GPU ANNS and its memory-capacity limits.
3. Position the paper as GPU-centric search over SSD-resident graph data.
4. Explain how the design differs from cluster-based GPU approaches.

Reusable writing move: GustANN's related work is short but technically sharp.

Do not copy: vague "prior work is not scalable" language. State the resource bottleneck.

## FusionANNS - Section 6 Related Work

Source pointer: [FusionANNS source note](../../../source-notes/fusionanns-2025.md); raw PDF Section 6, "Related Work".

Use when writing: related work for multi-tier CPU/GPU/SSD search papers.

Section role: classify prior work by where the data and computation live.

Positioning skeleton:

1. Discuss in-memory ANNS and its memory cost.
2. Discuss SSD-based ANNS and its latency/throughput limitations.
3. Discuss GPU-accelerated ANNS and HBM capacity limits.
4. Position the paper as collaborative filtering and reranking across tiers.

Reusable writing move: FusionANNS maps related work to resource placement, which is useful for systems papers.

Do not copy: if your system does not have a clear tier-placement story.
