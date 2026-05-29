---
id: anns-section-exemplars-abstract
type: analysis
status: active
created: 2026-05-26
updated: 2026-05-29
tags: [anns, paper-writing, abstract]
source_count: 5
sources:
  - raw/sources/papers/spfresh-2023.pdf
  - raw/inbox/warp-multi-vector-retrieval-sigir-best-paper-2025.pdf
  - raw/sources/papers/odinann-2026.pdf
  - raw/inbox/chameleon-ralm-vector-search-vldb-best-scalable-data-science-2025.pdf
  - raw/sources/papers/starling-2024.pdf
related:
  - anns-section-writing-exemplars
confidence: medium
---

# Abstract Exemplars

## Top Five

| Rank | Paper | Score | Why it works | Weakness |
|---|---:|---:|---|---|
| 1 | [SPFresh](../../source-notes/spfresh-2023.md) | 9.5 | It states the operational pain point, explains why existing disk indexes fail under freshness pressure, names the key method, and gives concrete headline results. | It is highly tuned to update-heavy vector search, so it is less reusable for pure static-search papers. |
| 2 | [WARP](../../source-notes/warp-multi-vector-retrieval-2025.md) | 9.3 | It compresses the multi-vector retrieval bottleneck, three named execution mechanisms, and hard end-to-end latency/index-size evidence into a tight abstract. | It is an IR retrieval-engine paper, so the abstract should not be copied wholesale for single-vector ANNS. |
| 3 | [OdinANN](../../source-notes/odinann-2026.md) | 9.2 | It gives a sharp direct-insert versus buffered-insert contrast, states the stability problem, and closes with stable billion-scale search/update evidence. | It is focused on inserts, not general update semantics. |
| 4 | [Chameleon](../../source-notes/chameleon-ralm-vector-search-2024.md) | 9.0 | It clearly names the RALM serving split, heterogeneous/disaggregated architecture, prototype mapping, and headline latency/throughput gains. | It sells the architecture more than the vector-search bottleneck; for a pure ANNS paper this would feel too application-layer. |
| 5 | [Starling](../../source-notes/starling-2024.md) | 8.9 | It frames a precise disk-resident segment-search gap and ties the abstract to I/O-efficient graph layout. | The segment-level premise is specialized, and the abstract assumes readers already care about that layer. |

## What To Steal

Start with the concrete deployment pain, not the algorithm family. SPFresh and Starling do not open with "ANN is important"; they open with what breaks at scale.

Name the mechanism in the abstract only after the reader understands why the mechanism is needed.

Use one or two quantitative results, not a wall of numbers. The abstract should prove the claim is real, not summarize the entire evaluation section.

WARP is the cleanest new example of this rule: the 41x and 3x headline numbers are useful because they are attached to named mechanisms, not because the abstract tries to list every benchmark.

## What Not To Copy

Do not write an abstract that says "we propose a novel framework" before specifying the bottleneck. Reviewers see this as empty.

Do not pack multiple hardware buzzwords into the abstract unless the paper later isolates which hardware property matters.

Do not make the result sound universal if the system is tuned for a workload class such as update-heavy search, batch throughput, SSD-resident graph search, or vector-relational queries.
