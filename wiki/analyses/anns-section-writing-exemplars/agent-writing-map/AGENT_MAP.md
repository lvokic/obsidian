---
id: anns-section-agent-writing-map
type: analysis
status: active
created: 2026-05-27
updated: 2026-05-27
tags: [anns, paper-writing, agent-map, systems]
source_count: 12
sources:
  - raw/sources/papers/spfresh-2023.pdf
  - raw/sources/papers/starling-2024.pdf
  - raw/sources/papers/vbase-2023.pdf
  - raw/sources/papers/gustann-2025.pdf
  - raw/sources/papers/rummy-2024.pdf
  - raw/sources/papers/milvus-2021.pdf
  - raw/sources/papers/fusionanns-2025.pdf
  - raw/sources/papers/smartanns-2024.pdf
  - raw/sources/papers/diskann-2019.pdf
  - raw/sources/papers/spann-2021.pdf
  - raw/sources/papers/bang-2024.pdf
  - raw/sources/papers/cxl-anns-2024.pdf
related:
  - anns-section-writing-exemplars
confidence: medium
---

# Agent Map: ANNS Section Writing Exemplars

This folder is a writing-guidance map for future agents. It points agents to the original paper sections first, then distills the winning sections from the ANNS section-quality audit into reusable section cards. Each card identifies the source paper section, the role that section plays, the argument skeleton, the writing moves worth copying, and the traps to avoid.

Do not treat this as a citation database or a place to copy prose. Treat it as a map for learning how strong ANNS systems papers build rhythm, contrast, paragraph order, evidence placement, and reviewer-facing scope control.

## Reading Protocol For Future Agents

1. Read this map first.
2. Identify the target section the user wants to write.
3. Read the original source paper section listed in the "Original Section Targets" table before reading any card. The goal is to absorb the writing style, pacing, paragraph transitions, argument setup, and evidence placement directly from the paper.
4. While reading the original section, take brief notes on the writing moves: how the section opens, how it narrows scope, how it introduces prior work, where it places numbers, how it transitions into the contribution, and how it avoids overclaiming.
5. Open the matching card file only after reading the original section. Use the card to convert your observations into a reusable skeleton.
6. Read the linked source note for factual context and cross-paper synthesis.
7. Draft the user's section using the original section's style lessons and the card's skeleton, but adapt the bottleneck, evidence, limitations, and terminology to the user's own system.

The cards are not a substitute for reading the original sections. They are compression artifacts for after the agent has studied the source writing.

## Original Section Targets

| Target section to write | Read the original section first | Raw source | Then read |
|---|---|---|---|
| Abstract | SPFresh front-matter Abstract | `raw/sources/papers/spfresh-2023.pdf` | [01 Abstract Cards](01-abstract-cards.md) |
| Introduction | Starling Section 1, "INTRODUCTION" | `raw/sources/papers/starling-2024.pdf` | [02 Introduction Cards](02-introduction-cards.md) |
| Background / Preliminaries | VBASE Sections 2-3 setup; Starling Section 2 as a narrower alternative | `raw/sources/papers/vbase-2023.pdf`; `raw/sources/papers/starling-2024.pdf` | [03 Background Cards](03-background-cards.md) |
| Motivation / Characterization | GustANN Section 3, "Motivation" | `raw/sources/papers/gustann-2025.pdf` | [04 Motivation Cards](04-motivation-cards.md) |
| System Overview / Architecture | Milvus Section 2, "SYSTEM DESIGN" | `raw/sources/papers/milvus-2021.pdf` | [05 Architecture Cards](05-architecture-cards.md) |
| Core Design / Algorithms | Starling Sections 3-5 | `raw/sources/papers/starling-2024.pdf` | [06 Design Cards](06-design-cards.md) |
| Implementation | SPFresh Section 4, "SPFresh Design and Implementation" | `raw/sources/papers/spfresh-2023.pdf` | [07 Implementation Cards](07-implementation-cards.md) |
| Evaluation | SPFresh Section 5, "Evaluation"; Starling Section 6 for disk-index ablations | `raw/sources/papers/spfresh-2023.pdf`; `raw/sources/papers/starling-2024.pdf` | [08 Evaluation Cards](08-evaluation-cards.md) |
| Related Work | VBASE Section 6, "Related Works" | `raw/sources/papers/vbase-2023.pdf` | [09 Related Work Cards](09-related-work-cards.md) |
| Discussion / Conclusion | Starling Sections 7-8; GustANN Section 4.5 for explicit limitations | `raw/sources/papers/starling-2024.pdf`; `raw/sources/papers/gustann-2025.pdf` | [10 Discussion Cards](10-discussion-cards.md) |

## What To Observe In The Original Paper

When reading the original section, do not only summarize content. Extract writing technique.

Track the opening move: broad trend, concrete pain, contradiction, missing abstraction, or measured bottleneck.

Track narrowing: how the paper moves from general ANNS to a specific setting such as segment-level disk search, update freshness, query-interface mismatch, or GPU/SSD throughput.

Track contrast: which prior systems are named, what exact property they lack, and whether the critique is fair.

Track evidence placement: whether numbers appear in the opening, after the mechanism, or only in the closing paragraph.

Track contribution staging: whether the paper introduces the system name early or only after the bottleneck is established.

Track scope control: where the paper admits workload assumptions, hardware assumptions, update assumptions, or latency-throughput tradeoffs.

## Section Card Index

| Target section to write | Read this card file | Primary model | Secondary models |
|---|---|---|---|
| Abstract | [01 Abstract Cards](01-abstract-cards.md) | SPFresh abstract | Starling abstract, VBASE abstract |
| Introduction | [02 Introduction Cards](02-introduction-cards.md) | Starling Section 1 | VBASE Section 1, SPFresh Section 1 |
| Background / Preliminaries | [03 Background Cards](03-background-cards.md) | VBASE Sections 2-3 setup | Starling Section 2, SmartANNS Section 2 |
| Motivation / Characterization | [04 Motivation Cards](04-motivation-cards.md) | GustANN Section 3 | Starling Section 3, RUMMY Sections 2-3 |
| System Overview / Architecture | [05 Architecture Cards](05-architecture-cards.md) | Milvus Section 2 | SPFresh Section 4.1, FusionANNS Section 3 |
| Core Design / Algorithms | [06 Design Cards](06-design-cards.md) | Starling Sections 3-5 | SPFresh Sections 3-4, VBASE Sections 3-4 |
| Implementation | [07 Implementation Cards](07-implementation-cards.md) | SPFresh Section 4 | Milvus Sections 2-5, GustANN Section 4 |
| Evaluation | [08 Evaluation Cards](08-evaluation-cards.md) | SPFresh Section 5 | Starling Section 6, GustANN Section 5 |
| Related Work | [09 Related Work Cards](09-related-work-cards.md) | VBASE Section 6 | GustANN Section 6, FusionANNS Section 6 |
| Discussion / Conclusion | [10 Discussion Cards](10-discussion-cards.md) | Starling Sections 7-8 | GustANN Sections 4.5/7, RUMMY Sections 7/9 |

## Practical Assembly Recipe

For a new ANNS systems paper, assemble section style from different papers rather than imitating one paper end to end.

Use Starling for the introduction and core design when the work is about disk/index layout, I/O locality, or segment-level search.

Use SPFresh for abstract, implementation, and evaluation when the work has update paths, background work, storage invariants, or online-vs-background interaction.

Use VBASE when the paper has a clean semantic abstraction, query interface, or database integration claim.

Use GustANN when the paper depends on hardware characterization, resource bottlenecks, GPU/SSD cooperation, or throughput-vs-latency tradeoffs.

Use Milvus only when the paper really is a full system or vector database. Do not borrow its breadth for a narrow index paper.

## Agent Warnings

Do not write "ANN is important" as the main opener. Every mature ANNS paper already assumes this.

Do not let "billion-scale" replace the actual problem. The real problem is usually memory capacity, random I/O, update freshness, GPU utilization, query semantics, or tier-crossing data movement.

Do not copy evaluation structures without matching the claim. Static-search papers should not imitate update-heavy SPFresh experiments unless they have freshness claims.

Do not hide the bad regime. If the system trades latency for throughput, memory for I/O, accuracy for update speed, or construction time for search time, state it explicitly.

Do not over-use hardware novelty. Hardware matters only when the paper proves a specific access pattern or pipeline benefits from it.
