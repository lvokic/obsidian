---
id: anns-section-agent-writing-map
type: analysis
status: active
created: 2026-05-27
updated: 2026-05-29
tags: [anns, paper-writing, agent-map, systems]
source_count: 65
sources:
  - wiki/source-notes/
related:
  - anns-section-writing-exemplars
  - simd-vectorization-anns-implementation-map
confidence: medium
---

# Agent Map: ANNS Section Writing Exemplars

This folder is a writing-guidance map for future agents. It points agents to the original paper sections first, then distills the winning sections from the ANNS section-quality audit into reusable section cards. Each card identifies the source paper section, the role that section plays, the argument skeleton, the writing moves worth copying, and the traps to avoid.

Do not treat this as a citation database or a place to copy prose. Treat it as a map for learning how strong ANNS systems papers build rhythm, contrast, paragraph order, evidence placement, and reviewer-facing scope control.

## Reading Protocol For Future Agents

1. Read this map first.
2. Identify the target section the user wants to write.
3. If the user asks for completeness or reviewer-style selection, read [Coverage Audit](../coverage-audit.md) before ranking anything.
4. Read the original source paper section listed in the "Original Section Targets" table before reading any card. The goal is to absorb the writing style, pacing, paragraph transitions, argument setup, and evidence placement directly from the paper.
5. While reading the original section, take brief notes on the writing moves: how the section opens, how it narrows scope, how it introduces prior work, where it places numbers, how it transitions into the contribution, and how it avoids overclaiming.
6. Open the current ranking file and matching style card only after reading the original section. Use them to convert observations into a reusable skeleton.
7. Read the linked source note for factual context and cross-paper synthesis.
8. Draft the user's section using the original section's style lessons and the card's skeleton, but adapt the bottleneck, evidence, limitations, and terminology to the user's own system.

The cards are not a substitute for reading the original sections. They are compression artifacts for after the agent has studied the source writing.

## Original Section Targets

| Target section to write | Read the original section first | Raw source | Then read |
|---|---|---|---|
| Abstract | SPFresh front-matter Abstract; OdinANN front-matter Abstract | `raw/sources/papers/spfresh-2023.pdf`; `raw/sources/papers/odinann-2026.pdf` | [Abstract Ranking](../abstract.md) |
| Introduction | Starling Section 1; OdinANN Section 1 | `raw/sources/papers/starling-2024.pdf`; `raw/sources/papers/odinann-2026.pdf` | [Introduction Ranking](../introduction.md) |
| Background / Preliminaries | VBASE Sections 2-3; OdinANN Section 2 | `raw/sources/papers/vbase-2023.pdf`; `raw/sources/papers/odinann-2026.pdf` | [Background Ranking](../background-preliminaries.md) |
| Motivation / Characterization | GustANN Section 3; OdinANN Section 2 | `raw/sources/papers/gustann-2025.pdf`; `raw/sources/papers/odinann-2026.pdf` | [Motivation Ranking](../motivation-characterization.md) |
| System Overview / Architecture | Milvus Section 2; SPFresh Section 4.1 | `raw/sources/papers/milvus-2021.pdf`; `raw/sources/papers/spfresh-2023.pdf` | [Architecture Ranking](../system-overview-architecture.md) |
| Method / Core Design | Starling Sections 3-5; SPFresh Sections 3-4; OdinANN Section 3 | `raw/sources/papers/starling-2024.pdf`; `raw/sources/papers/spfresh-2023.pdf`; `raw/sources/papers/odinann-2026.pdf` | [Method Ranking](../core-design-algorithms.md) |
| Optimization / Execution Layer | PQ Fast Scan Sections 1-3; Milvus Section 3.2; Flash design sections | `raw/sources/papers/pq-fast-scan-2015.pdf`; `raw/sources/papers/milvus-2021.pdf`; `raw/inbox/flash-graph-indexing-2025.pdf` | [Optimization Ranking](../optimization-execution-layer.md) |
| Implementation | SPFresh Section 4; OdinANN Section 3; GustANN Section 4 | `raw/sources/papers/spfresh-2023.pdf`; `raw/sources/papers/odinann-2026.pdf`; `raw/sources/papers/gustann-2025.pdf` | [Implementation Ranking](../implementation.md) |
| Evaluation | SPFresh Section 5; OdinANN Section 4; Starling Section 6 | `raw/sources/papers/spfresh-2023.pdf`; `raw/sources/papers/odinann-2026.pdf`; `raw/sources/papers/starling-2024.pdf` | [Evaluation Ranking](../evaluation.md) |
| Related Work | VBASE Section 6; OdinANN Section 5; GustANN Section 6 | `raw/sources/papers/vbase-2023.pdf`; `raw/sources/papers/odinann-2026.pdf`; `raw/sources/papers/gustann-2025.pdf` | [Related Work Ranking](../related-work.md) |
| Discussion / Conclusion | Starling Sections 7-8; GustANN Section 4.5; OdinANN Section 3.5 | `raw/sources/papers/starling-2024.pdf`; `raw/sources/papers/gustann-2025.pdf`; `raw/sources/papers/odinann-2026.pdf` | [Discussion Ranking](../discussion-conclusion.md) |

## What To Observe In The Original Paper

When reading the original section, do not only summarize content. Extract writing technique.

Track the opening move: broad trend, concrete pain, contradiction, missing abstraction, or measured bottleneck.

Track narrowing: how the paper moves from general ANNS to a specific setting such as segment-level disk search, update freshness, query-interface mismatch, or GPU/SSD throughput.

Track contrast: which prior systems are named, what exact property they lack, and whether the critique is fair.

Track evidence placement: whether numbers appear in the opening, after the mechanism, or only in the closing paragraph.

Track contribution staging: whether the paper introduces the system name early or only after the bottleneck is established.

Track scope control: where the paper admits workload assumptions, hardware assumptions, update assumptions, or latency-throughput tradeoffs.

## Current Ranking And Card Index

The current ranking files are authoritative. The older numbered card files remain useful as style-learning notes, but they may not include every paper added during the 2026-05-29 refresh.

| Target section to write | Current ranking | Style card | Primary model | Secondary models |
|---|---|---|---|---|
| Abstract | [Abstract Ranking](../abstract.md) | [01 Abstract Cards](01-abstract-cards.md) | SPFresh | OdinANN, Starling |
| Introduction | [Introduction Ranking](../introduction.md) | [02 Introduction Cards](02-introduction-cards.md) | Starling | OdinANN, VBASE |
| Background / Preliminaries | [Background Ranking](../background-preliminaries.md) | [03 Background Cards](03-background-cards.md) | VBASE | Starling, OdinANN |
| Motivation / Characterization | [Motivation Ranking](../motivation-characterization.md) | [04 Motivation Cards](04-motivation-cards.md) | GustANN | OdinANN, Starling |
| System Overview / Architecture | [Architecture Ranking](../system-overview-architecture.md) | [05 Architecture Cards](05-architecture-cards.md) | Milvus | SPFresh, FusionANNS |
| Method / Core Design | [Method Ranking](../core-design-algorithms.md) | [06 Design Cards](06-design-cards.md) | Starling | SPFresh, OdinANN |
| Optimization / Execution Layer | [Optimization Ranking](../optimization-execution-layer.md) | [SIMD/Batch Map](../../simd-vectorization-anns-implementation-map/AGENT_MAP.md) | PQ Fast Scan | Milvus, Flash |
| Implementation | [Implementation Ranking](../implementation.md) | [07 Implementation Cards](07-implementation-cards.md) | SPFresh | OdinANN, GustANN |
| Evaluation | [Evaluation Ranking](../evaluation.md) | [08 Evaluation Cards](08-evaluation-cards.md) | SPFresh | OdinANN, Starling |
| Related Work | [Related Work Ranking](../related-work.md) | [09 Related Work Cards](09-related-work-cards.md) | VBASE | OdinANN, GustANN |
| Discussion / Conclusion | [Discussion Ranking](../discussion-conclusion.md) | [10 Discussion Cards](10-discussion-cards.md) | Starling | GustANN, OdinANN |

## Practical Assembly Recipe

For a new ANNS systems paper, assemble section style from different papers rather than imitating one paper end to end.

For a technical chapter on SIMD, vectorization, and batch execution, use [SIMD, Vectorization, and Batch Execution for ANNS Implementation](../../simd-vectorization-anns-implementation-map/AGENT_MAP.md). The general section cards here are not enough for that topic because vectorization requires implementation-stage paper evaluation and mechanism-level reading.

Use Starling for the introduction and core design when the work is about disk/index layout, I/O locality, or segment-level search.

Use SPFresh for abstract, implementation, and evaluation when the work has update paths, background work, storage invariants, or online-vs-background interaction.

Use OdinANN when the work is about dynamic graph indexes, direct insert, stable search under update load, concurrency control, or SSD-resident graph records.

Use VBASE when the paper has a clean semantic abstraction, query interface, or database integration claim.

Use GustANN when the paper depends on hardware characterization, resource bottlenecks, GPU/SSD cooperation, or throughput-vs-latency tradeoffs.

Use Milvus only when the paper really is a full system or vector database. Do not borrow its breadth for a narrow index paper.

## Agent Warnings

Do not write "ANN is important" as the main opener. Every mature ANNS paper already assumes this.

Do not let "billion-scale" replace the actual problem. The real problem is usually memory capacity, random I/O, update freshness, GPU utilization, query semantics, or tier-crossing data movement.

Do not copy evaluation structures without matching the claim. Static-search papers should not imitate update-heavy SPFresh experiments unless they have freshness claims.

Do not hide the bad regime. If the system trades latency for throughput, memory for I/O, accuracy for update speed, or construction time for search time, state it explicitly.

Do not over-use hardware novelty. Hardware matters only when the paper proves a specific access pattern or pipeline benefits from it.
