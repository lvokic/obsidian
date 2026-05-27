---
id: anns-section-agent-map-abstract
type: analysis
status: active
created: 2026-05-27
updated: 2026-05-27
tags: [anns, paper-writing, abstract, agent-map]
source_count: 3
sources:
  - raw/sources/papers/spfresh-2023.pdf
  - raw/sources/papers/starling-2024.pdf
  - raw/sources/papers/vbase-2023.pdf
related:
  - anns-section-agent-writing-map
confidence: medium
---

# Abstract Cards

## SPFresh - Abstract

Source pointer: [SPFresh source note](../../../source-notes/spfresh-2023.md); raw PDF front matter, Abstract.

Use when writing: an abstract for an update-aware, storage-aware, online ANNS system.

Section role: compress the whole paper into a clear operational failure story: vector indexes need freshness, global rebuild is too expensive, local in-place maintenance is the missing mechanism.

Argument skeleton:

1. Establish ANNS as a serving primitive.
2. Identify continuous vector updates as the pressure point.
3. Explain why existing update support relies on secondary indexes and global rebuild.
4. Introduce the local mechanism, LIRE, as the reason the system can update in place.
5. Close with resource and performance evidence at billion scale.

Reusable writing move: the abstract makes the prior-work limitation specific before naming the system. It does not say "existing methods are inefficient"; it says they accumulate updates separately and rebuild globally.

Do not copy: the exact update-heavy framing unless your paper really has a freshness/update claim.

## Starling - Abstract

Source pointer: [Starling source note](../../../source-notes/starling-2024.md); raw PDF front matter, Abstract.

Use when writing: an abstract for a disk-resident index, data-layout, or segment-level vector database paper.

Section role: frame a constrained deployment unit, the vector database segment, and argue that disk search must balance accuracy, efficiency, and space at that unit.

Argument skeleton:

1. State that in-memory vector indexes do not fit large vector datasets.
2. Move from "disk-based search" to the more precise setting: vector database segments.
3. Explain why existing disk methods fail to satisfy all requirements at once.
4. Introduce the two-part design: locality-aware layout and I/O-minimizing search.
5. Use a small set of headline numbers to prove the design is not just conceptual.

Reusable writing move: it narrows the system context early. "Disk-based ANNS" becomes "disk-resident graph index within a data segment," which makes the contribution more defensible.

Do not copy: the segment argument if your target system is not actually segment-oriented.

## VBASE - Abstract

Source pointer: [VBASE source note](../../../source-notes/vbase-2023.md); raw PDF front matter, Abstract.

Use when writing: an abstract for a vector database, query-processing, or interface-level ANNS paper.

Section role: turn vector search from an index problem into a query semantics problem.

Argument skeleton:

1. Start from the need to combine vector similarity with relational predicates.
2. Identify the TopK interface as the blocker.
3. Introduce relaxed monotonicity as the common abstraction.
4. Explain that the system can integrate vector indexes into a relational engine.
5. Finish with performance evidence on complex vector queries.

Reusable writing move: the abstract names a semantic property, not just a faster implementation. That gives the paper a durable conceptual hook.

Do not copy: the database-interface rhetoric for a paper whose contribution is only a faster kernel or index layout.
