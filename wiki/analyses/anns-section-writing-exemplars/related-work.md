---
id: anns-section-exemplars-related-work
type: analysis
status: active
created: 2026-05-26
updated: 2026-05-29
tags: [anns, paper-writing, related-work]
source_count: 3
sources:
  - raw/sources/papers/vbase-2023.pdf
  - raw/sources/papers/odinann-2026.pdf
  - raw/sources/papers/gustann-2025.pdf
related:
  - anns-section-writing-exemplars
confidence: medium
---

# Related Work Exemplars

## Top Three

| Rank | Paper | Score | Why it works | Weakness |
|---|---:|---:|---|---|
| 1 | [VBASE](../../source-notes/vbase-2023.md) | 9.0 | Best positioning for an interface/DB paper. It separates similarity query processing, vector indices, and vector database integration instead of lumping everything under ANN. | It is not the best template for a pure SSD/GPU index paper. |
| 2 | [OdinANN](../../source-notes/odinann-2026.md) | 8.9 | Cleanly separates billion-scale indexes, hybrid storage, near-data processing, vector compression, update-capable indexes, and reserved-space update designs. | It is short and scoped around direct insert. |
| 3 | [GustANN](../../source-notes/gustann-2025.md) | 8.7 | Concise and adversarially useful. It distinguishes SSD-resident ANNS from GPU ANNS and explains why GustANN's GPU-plus-SSD stance is different. | It is short; if the new paper needs broad historical context, this is not enough. |

## What To Steal

Related work should be a map of non-overlap. For each category, explain what prior work solves and what your paper deliberately changes.

Group by technical constraint, not by citation chronology. Memory-resident graph indexes, SSD-resident graph/cluster indexes, GPU systems, vector DB query interfaces, and update-heavy systems are different categories.

Be explicit when a method is orthogonal. RUMMY does this well for vector quantization and algorithmic IVF variants, even if its related-work section is not the strongest overall.

## What Not To Copy

Do not use related work as a place to dump every citation that did not fit earlier.

Do not dismiss prior systems with vague words like "inefficient" or "not scalable" unless the exact resource bottleneck is stated.

Do not claim unfair separation. If your paper depends on a baseline's algorithmic family, say whether you improve the algorithm, the execution path, or the deployment tier.
