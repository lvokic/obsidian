---
id: anns-section-exemplars-core-design-algorithms
type: analysis
status: active
created: 2026-05-26
updated: 2026-05-29
tags: [anns, paper-writing, design, algorithms]
source_count: 5
sources:
  - raw/sources/papers/starling-2024.pdf
  - raw/inbox/warp-multi-vector-retrieval-sigir-best-paper-2025.pdf
  - raw/sources/papers/spfresh-2023.pdf
  - raw/sources/papers/odinann-2026.pdf
  - raw/inbox/integrating-vector-databases-across-embedding-models-sigmod-hm-2026.pdf
related:
  - anns-section-writing-exemplars
confidence: medium
---

# Method / Core Design Exemplars

## Top Five

| Rank | Paper | Score | Why it works | Weakness |
|---|---:|---:|---|---|
| 1 | [Starling](../../source-notes/starling-2024.md) | 9.5 | Best design alignment. It factors the disk graph problem into route length and block locality, then introduces in-memory navigation, block shuffling, and block search. | The design story is narrower than a general vector DB paper. |
| 2 | [WARP](../../source-notes/warp-multi-vector-retrieval-2025.md) | 9.4 | Best new execution-method section. WARPSELECT, implicit decompression, and two-stage reduction are introduced as answers to measured retrieval-engine bottlenecks. | It is specialized to XTR/ColBERT-style multi-vector retrieval. |
| 3 | [SPFresh](../../source-notes/spfresh-2023.md) | 9.3 | LIRE is unusually well explained: insert, delete, merge, split, reassign, and local rebuilds are tied to freshness and stability. | The design is complex; a weaker paper would drown the reader in cases. |
| 4 | [OdinANN](../../source-notes/odinann-2026.md) | 9.2 | Direct insert, GC-free update combining, and approximate concurrency control are tied tightly to the buffered-insert failure mode. | The method is coupled to on-disk graph records and inserts. |
| 5 | [Integrating Vector Databases](../../source-notes/integrating-vector-databases-embedding-models-2026.md) | 9.1 | LA2M is a strong formal method section: local grouping, Procrustes-style alignment, PCA/rank handling, and online integration all follow from one hypothesis. | It is not an ANNS execution method; use it only for papers with a real geometric/data-integration abstraction. |

## What To Steal

Introduce design principles before mechanisms. Starling's design philosophy makes the following layout and search policies feel inevitable.

Give each algorithmic component a failure mode it handles. SPFresh works because update operations are not just listed; they preserve index health under mutation.

If you introduce a formal property, use it to simplify the system story. VBASE's relaxed monotonicity is strong because it unifies query execution, not because it is mathematically fancy.

The fourth and fifth slots are intentionally conditional. OdinANN is the graph-update method model; Integrating Vector Databases is the formal/data-integration method model.

## What Not To Copy

Do not introduce many mechanisms with equal weight. Reviewers need to know which idea is central and which mechanisms are support.

Do not present pseudocode before the reader understands the invariant.

Do not use proof-like language unless the paper also states the assumptions under which the property matters.
