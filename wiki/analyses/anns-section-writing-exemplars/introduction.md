---
id: anns-section-exemplars-introduction
type: analysis
status: active
created: 2026-05-26
updated: 2026-05-29
tags: [anns, paper-writing, introduction]
source_count: 3
sources:
  - raw/sources/papers/starling-2024.pdf
  - raw/sources/papers/odinann-2026.pdf
  - raw/sources/papers/vbase-2023.pdf
related:
  - anns-section-writing-exemplars
confidence: medium
---

# Introduction Exemplars

## Top Three

| Rank | Paper | Score | Why it works | Weakness |
|---|---:|---:|---|---|
| 1 | [Starling](../../source-notes/starling-2024.md) | 9.6 | Best overall problem cascade: vector DB segment search, memory pressure, DiskANN/SPANN limits, I/O locality, then Starling. | The segment-level framing may be less obvious to non-vector-DB reviewers. |
| 2 | [OdinANN](../../source-notes/odinann-2026.md) | 9.4 | Best new dynamic-graph introduction. It shows why buffered insert destabilizes search, then turns direct insert into a precise systems problem. | It is not a template for static ANNS papers. |
| 3 | [VBASE](../../source-notes/vbase-2023.md) | 9.3 | Best conceptual introduction. It turns "vector search in databases" into a precise interface mismatch: TopK is not enough for complex relational predicates. | The paper's core problem is broader than ANNS, so copying it directly can pull an ANNS paper off-scope. |

## What To Steal

Build a chain of inevitability: application demand, system constraint, failure of the closest prior design, missing capability, then your design.

Name prior systems concretely. Starling is persuasive because it does not attack "existing work" abstractly; it separates SPANN-style clustering from DiskANN-style graph search and explains what each misses.

Use examples only if they expose a technical constraint. VBASE's value is not that it mentions database use cases; it uses those use cases to show why TopK-only vector APIs are structurally wrong.

## What Not To Copy

Do not spend the first page re-teaching ANN basics unless the paper's novelty depends on a specific property of ANN algorithms.

Do not make "billion-scale" the whole motivation. Scale is table stakes in this literature; the introduction must explain which resource or interface becomes the bottleneck.

Do not bury the paper's actual unit of contribution. A system paper can contribute an index layout, query pipeline, update protocol, architecture, or database interface, but the introduction must say which one.
