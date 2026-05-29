---
id: anns-section-exemplars-discussion-conclusion
type: analysis
status: active
created: 2026-05-26
updated: 2026-05-29
tags: [anns, paper-writing, discussion, conclusion]
source_count: 3
sources:
  - raw/sources/papers/starling-2024.pdf
  - raw/sources/papers/gustann-2025.pdf
  - raw/sources/papers/odinann-2026.pdf
related:
  - anns-section-writing-exemplars
confidence: medium
---

# Discussion / Conclusion Exemplars

## Top Three

| Rank | Paper | Score | Why it works | Weakness |
|---|---:|---:|---|---|
| 1 | [Starling](../../source-notes/starling-2024.md) | 9.3 | Best discussion. It explains memory-based related work, comparison with SPANN, in-memory graph role, central SSD assumption, update handling, and range-search relevance. | It is long; weaker authors would turn this into a second related-work section. |
| 2 | [GustANN](../../source-notes/gustann-2025.md) | 9.1 | Best honest limitation statement. It discusses scalability, generalization, GPU memory pressure, quantization orthogonality, and the latency-throughput tradeoff. | It should foreground the latency tradeoff earlier in the paper. |
| 3 | [OdinANN](../../source-notes/odinann-2026.md) | 8.9 | Strong practical discussion of consistency, GC-free behavior, insert latency, memory usage, and delete handling. | The discussion is concise and update-specific. |

## What To Steal

Use discussion to state the exact operating envelope of the system. Good reviewers punish papers that only reveal assumptions through failed experiments.

Separate limitations from future work. A limitation constrains the current claim; future work is optional.

Explain transferability carefully. GustANN's discussion is useful because it distinguishes techniques that generalize from the specific ANNS system.

## What Not To Copy

Do not write a conclusion that only repeats the abstract.

Do not hide the system's bad regime. If the system trades latency for throughput, memory for I/O, accuracy for update freshness, or construction cost for query speed, say it.

Do not use discussion to introduce a new contribution that should have been evaluated.
