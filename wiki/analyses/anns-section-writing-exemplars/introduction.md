---
id: anns-section-exemplars-introduction
type: analysis
status: active
created: 2026-05-26
updated: 2026-05-29
tags: [anns, paper-writing, introduction]
source_count: 5
sources:
  - raw/sources/papers/starling-2024.pdf
  - raw/inbox/integrating-vector-databases-across-embedding-models-sigmod-hm-2026.pdf
  - raw/inbox/chameleon-ralm-vector-search-vldb-best-scalable-data-science-2025.pdf
  - raw/sources/papers/odinann-2026.pdf
  - raw/sources/papers/vbase-2023.pdf
related:
  - anns-section-writing-exemplars
confidence: medium
---

# Introduction Exemplars

## Top Five

| Rank | Paper | Score | Why it works | Weakness |
|---|---:|---:|---|---|
| 1 | [Starling](../../source-notes/starling-2024.md) | 9.6 | Best overall problem cascade: vector DB segment search, memory pressure, DiskANN/SPANN limits, I/O locality, then Starling. | The segment-level framing may be less obvious to non-vector-DB reviewers. |
| 2 | [Integrating Vector Databases](../../source-notes/integrating-vector-databases-embedding-models-2026.md) | 9.5 | Best new conceptual database introduction. It turns vector stores from "fast similarity search" into a data-sharing/interoperability problem with concrete application pressure. | It is not an ANNS performance paper; use the style only when the new work has a real data-management abstraction. |
| 3 | [Chameleon](../../source-notes/chameleon-ralm-vector-search-2024.md) | 9.4 | Best service-architecture introduction. It connects RALM serving, vector search bottlenecks, accelerator heterogeneity, disaggregation, and headline results in one coherent chain. | It is RALM-centric and assumes IVF-PQ vector search, so it is less reusable for graph-index papers. |
| 4 | [OdinANN](../../source-notes/odinann-2026.md) | 9.3 | It turns buffered-insert instability into a concrete dynamic-graph systems problem and makes direct insert feel technically necessary. | It is not a template for static search, filtering, or vector-DB query papers. |
| 5 | [VBASE](../../source-notes/vbase-2023.md) | 9.2 | It makes a crisp interface-mismatch argument: TopK-only vector APIs cannot express important vector-relational queries. | It is broader database-query framing; copying it for a narrow index paper would overinflate the contribution. |

## What To Steal

Build a chain of inevitability: application demand, system constraint, failure of the closest prior design, missing capability, then your design.

Name prior systems concretely. Starling is persuasive because it does not attack "existing work" abstractly; it separates SPANN-style clustering from DiskANN-style graph search and explains what each misses.

Use examples only if they expose a technical constraint. VBASE's value is not that it mentions database use cases; it uses those use cases to show why TopK-only vector APIs are structurally wrong.

The fourth and fifth slots are intentionally narrow. OdinANN is the safer template for dynamic graph-update work; VBASE is the safer template for vector-relational query semantics.

## What Not To Copy

Do not spend the first page re-teaching ANN basics unless the paper's novelty depends on a specific property of ANN algorithms.

Do not make "billion-scale" the whole motivation. Scale is table stakes in this literature; the introduction must explain which resource or interface becomes the bottleneck.

Do not bury the paper's actual unit of contribution. A system paper can contribute an index layout, query pipeline, update protocol, architecture, or database interface, but the introduction must say which one.
