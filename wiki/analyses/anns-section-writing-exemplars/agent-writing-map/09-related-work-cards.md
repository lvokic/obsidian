---
id: anns-section-agent-map-related-work
type: analysis
status: active
created: 2026-05-27
updated: 2026-05-27
tags: [anns, paper-writing, related-work, agent-map]
source_count: 3
sources:
  - raw/sources/papers/vbase-2023.pdf
  - raw/sources/papers/gustann-2025.pdf
  - raw/sources/papers/fusionanns-2025.pdf
related:
  - anns-section-agent-writing-map
confidence: medium
---

# Related Work Cards

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
