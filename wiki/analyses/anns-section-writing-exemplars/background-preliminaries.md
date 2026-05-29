---
id: anns-section-exemplars-background-preliminaries
type: analysis
status: active
created: 2026-05-26
updated: 2026-05-29
tags: [anns, paper-writing, background, preliminaries]
source_count: 5
sources:
  - raw/sources/papers/vbase-2023.pdf
  - raw/inbox/chameleon-ralm-vector-search-vldb-best-scalable-data-science-2025.pdf
  - raw/inbox/integrating-vector-databases-across-embedding-models-sigmod-hm-2026.pdf
  - raw/sources/papers/starling-2024.pdf
  - raw/sources/papers/odinann-2026.pdf
related:
  - anns-section-writing-exemplars
confidence: medium
---

# Background / Preliminaries Exemplars

## Top Five

| Rank | Paper | Score | Why it works | Weakness |
|---|---:|---:|---|---|
| 1 | [VBASE](../../source-notes/vbase-2023.md) | 9.4 | The background is not a generic survey. It defines the query semantics and prepares the relaxed-monotonicity contribution. | It is most useful for papers with a query-processing or database-interface angle. |
| 2 | [Chameleon](../../source-notes/chameleon-ralm-vector-search-2024.md) | 9.2 | It teaches only the pieces the design needs: RALM retrieval, large-scale vector search, IVF-PQ scanning, CPU/GPU limits, and disaggregation pressure. | It is centered on IVF-PQ and RALM, not graph ANN or general vector DBMS internals. |
| 3 | [Integrating Vector Databases](../../source-notes/integrating-vector-databases-embedding-models-2026.md) | 9.0 | It uses background to introduce the local-vs-global isometry hypothesis and the quality metrics that later justify LA2M. | It is mathematically/data-management oriented rather than a systems execution background. |
| 4 | [Starling](../../source-notes/starling-2024.md) | 8.9 | It gives just enough HVSS and segment-level disk-search context to make the later layout choices legible. | It is deliberately narrow; it will not help a paper that needs broader ANN taxonomy. |
| 5 | [OdinANN](../../source-notes/odinann-2026.md) | 8.8 | It teaches on-disk graph layout, search, buffered insert, and direct-insert challenges in the order needed for the method. | It is update-specific and less reusable than Starling for general disk-resident search. |

## What To Steal

Use background to introduce constraints, not to prove that you read the literature.

Define the abstraction your paper will modify. For VBASE this is vector query semantics; for Starling it is segment-level disk-resident HVSS; for SmartANNS it is host plus near-data execution.

For hardware papers, Chameleon is the cleaner model than most CXL/accelerator papers because it does not dump devices first. It starts from workload components and only then introduces hardware constraints.

Stop background right before it becomes related work. The best preliminaries make the next section feel necessary.

## What Not To Copy

Do not write a taxonomy dump of LSH, tree, quantization, graph, IVF, and GPU methods unless the taxonomy directly explains a design choice.

Do not mix background with claims of superiority. Background should establish what is true; motivation/design should argue why your system is better.

Do not define terms that never return in the design or evaluation.
