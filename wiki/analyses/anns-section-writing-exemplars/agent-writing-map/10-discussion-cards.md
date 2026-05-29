---
id: anns-section-agent-map-discussion
type: analysis
status: active
created: 2026-05-27
updated: 2026-05-29
tags: [anns, paper-writing, discussion, conclusion, agent-map]
source_count: 6
sources:
  - raw/sources/papers/starling-2024.pdf
  - raw/sources/papers/gustann-2025.pdf
  - raw/inbox/chameleon-ralm-vector-search-vldb-best-scalable-data-science-2025.pdf
  - raw/sources/papers/odinann-2026.pdf
  - raw/inbox/warp-multi-vector-retrieval-sigir-best-paper-2025.pdf
  - raw/sources/papers/rummy-2024.pdf
related:
  - anns-section-agent-writing-map
confidence: medium
---

# Discussion / Conclusion Cards

## Current Top 5 Card Index

This index is authoritative for the current discussion/conclusion ranking. The detailed cards below are retained as expanded style notes; if they conflict with this index or [Discussion Ranking](../discussion-conclusion.md), follow the ranking.

| Rank | Paper | Use when | Writing move to copy | Do not copy |
|---|---|---|---|---|
| 1 | Starling | Disk-resident indexes with clear assumptions and likely reviewer objections. | Use discussion to answer objections that do not fit in evaluation. | Do not turn discussion into another related-work section. |
| 2 | GustANN | Hardware-assisted systems with throughput/capacity tradeoffs. | State scalability limits and latency tradeoffs explicitly. | Do not hide limitations until the final paragraph. |
| 3 | Chameleon | Serving systems with heterogeneous/disaggregated architecture. | Discuss deployment scope and service assumptions directly. | Do not overgeneralize beyond the measured service setting. |
| 4 | OdinANN | Dynamic graph indexes and update-heavy search. | Close by restating the update model and where direct insertion helps. | Do not imply universal dynamic support if the workload is narrower. |
| 5 | WARP | Multi-vector retrieval engines and execution optimizations. | Separate algorithmic retrieval quality from execution-system speedups. | Do not claim ANN-system generality from a retrieval-engine result. |

## Legacy Detailed Cards

The detailed cards below predate the Top 5 refresh. They are still useful for studying writing moves, but they are not a complete or current ranking.

## Starling - Sections 7-8 Discussion and Conclusion

Source pointer: [Starling source note](../../../source-notes/starling-2024.md); raw PDF Sections 7-8.

Use when writing: discussion for disk-resident indexes, segment-level systems, or designs with clear assumptions.

Section role: explain how the design relates to memory-based methods, SPANN, in-memory graph routing, SSD assumptions, updates, and range search.

Discussion skeleton:

1. State relationship to memory-based HVSS.
2. Compare carefully with the closest prior system.
3. Clarify the role of a key component, such as the in-memory graph.
4. State the central hardware/system assumption.
5. Explain update handling if the system is not primarily update-focused.
6. Mention additional query types only if supported by design.
7. Keep the conclusion short.

Reusable writing move: Starling uses discussion to answer likely reviewer objections that did not fit cleanly in evaluation.

Do not copy: turning discussion into another related-work section.

## GustANN - Sections 4.5 and 7 Discussion/Conclusion

Source pointer: [GustANN source note](../../../source-notes/gustann-2025.md); raw PDF Section 4.5, "Discussion", and Section 7, "Conclusion".

Use when writing: discussion for hardware-assisted systems with throughput, capacity, or generalization claims.

Section role: state scalability limits, generalizable techniques, and latency tradeoffs.

Discussion skeleton:

1. Explain what resource limits future scale.
2. Explain which techniques generalize beyond this exact system.
3. State the main limitation explicitly.
4. Relate the limitation to target workloads.
5. Keep the conclusion focused on the claim actually evaluated.

Reusable writing move: GustANN openly states that maximum throughput comes with a latency tradeoff.

Do not copy: delaying an important limitation until discussion if it should shape the introduction and evaluation.

## RUMMY - Sections 7 and 9 Discussion/Conclusion

Source pointer: [RUMMY source note](../../../source-notes/rummy-2024.md); raw PDF Section 7, "Discussion", and Section 9, "Conclusion".

Use when writing: discussion for query-processing systems built on an existing ANN index.

Section role: clarify that the contribution is a system and pipeline, not a new ANN index.

Discussion skeleton:

1. State what the paper is not.
2. Explain how the design is orthogonal to algorithmic improvements.
3. Discuss transferability to other accelerators or domains.
4. Connect the system to broader application pressure.
5. Conclude with the specific mechanism and measured scale.

Reusable writing move: RUMMY controls scope by explicitly saying it is not an index contribution.

Do not copy: orthogonality claims unless your system really composes with the omitted methods.
