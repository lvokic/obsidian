---
id: anns-section-exemplars-abstract
type: analysis
status: active
created: 2026-05-26
updated: 2026-05-26
tags: [anns, paper-writing, abstract]
source_count: 3
sources:
  - raw/sources/papers/spfresh-2023.pdf
  - raw/sources/papers/starling-2024.pdf
  - raw/sources/papers/vbase-2023.pdf
related:
  - anns-section-writing-exemplars
confidence: medium
---

# Abstract Exemplars

## Top Three

| Rank | Paper | Score | Why it works | Weakness |
|---|---:|---:|---|---|
| 1 | [SPFresh](../../source-notes/spfresh-2023.md) | 9.5 | It states the operational pain point, explains why existing disk indexes fail under freshness pressure, names the key method, and gives concrete headline results. | It is highly tuned to update-heavy vector search, so it is less reusable for pure static-search papers. |
| 2 | [Starling](../../source-notes/starling-2024.md) | 9.0 | It frames segment-level disk HVSS as a missing layer in vector databases and immediately connects the design to I/O efficiency. | It assumes the reader already accepts segment-level search as important. |
| 3 | [VBASE](../../source-notes/vbase-2023.md) | 8.7 | It has the strongest conceptual hook: conventional TopK vector indexes do not compose cleanly with relational predicates, so the interface is the problem. | It is a vector database/query-processing paper more than a pure ANNS systems paper. |

## What To Steal

Start with the concrete deployment pain, not the algorithm family. SPFresh and Starling do not open with "ANN is important"; they open with what breaks at scale.

Name the mechanism in the abstract only after the reader understands why the mechanism is needed.

Use one or two quantitative results, not a wall of numbers. The abstract should prove the claim is real, not summarize the entire evaluation section.

## What Not To Copy

Do not write an abstract that says "we propose a novel framework" before specifying the bottleneck. Reviewers see this as empty.

Do not pack multiple hardware buzzwords into the abstract unless the paper later isolates which hardware property matters.

Do not make the result sound universal if the system is tuned for a workload class such as update-heavy search, batch throughput, SSD-resident graph search, or vector-relational queries.
