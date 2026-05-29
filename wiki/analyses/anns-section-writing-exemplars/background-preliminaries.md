---
id: anns-section-exemplars-background-preliminaries
type: analysis
status: active
created: 2026-05-26
updated: 2026-05-29
tags: [anns, paper-writing, background, preliminaries]
source_count: 3
sources:
  - raw/sources/papers/vbase-2023.pdf
  - raw/sources/papers/starling-2024.pdf
  - raw/sources/papers/odinann-2026.pdf
related:
  - anns-section-writing-exemplars
confidence: medium
---

# Background / Preliminaries Exemplars

## Top Three

| Rank | Paper | Score | Why it works | Weakness |
|---|---:|---:|---|---|
| 1 | [VBASE](../../source-notes/vbase-2023.md) | 9.4 | The background is not a generic survey. It defines the query semantics and prepares the relaxed-monotonicity contribution. | It is most useful for papers with a query-processing or database-interface angle. |
| 2 | [Starling](../../source-notes/starling-2024.md) | 9.0 | It gives just enough high-dimensional vector similarity search and segment-level context to make the later disk graph design legible. | It does not try to teach the full ANN ecosystem, which is correct but narrow. |
| 3 | [OdinANN](../../source-notes/odinann-2026.md) | 8.8 | It teaches on-disk graph layout, search, buffered insert, and direct-insert challenges in exactly the order needed for the method. | It is update-specific and less reusable for non-dynamic systems. |

## What To Steal

Use background to introduce constraints, not to prove that you read the literature.

Define the abstraction your paper will modify. For VBASE this is vector query semantics; for Starling it is segment-level disk-resident HVSS; for SmartANNS it is host plus near-data execution.

Stop background right before it becomes related work. The best preliminaries make the next section feel necessary.

## What Not To Copy

Do not write a taxonomy dump of LSH, tree, quantization, graph, IVF, and GPU methods unless the taxonomy directly explains a design choice.

Do not mix background with claims of superiority. Background should establish what is true; motivation/design should argue why your system is better.

Do not define terms that never return in the design or evaluation.
