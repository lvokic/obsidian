---
id: anns-section-agent-map-background
type: analysis
status: active
created: 2026-05-27
updated: 2026-05-27
tags: [anns, paper-writing, background, preliminaries, agent-map]
source_count: 3
sources:
  - raw/sources/papers/vbase-2023.pdf
  - raw/sources/papers/starling-2024.pdf
  - raw/sources/papers/smartanns-2024.pdf
related:
  - anns-section-agent-writing-map
confidence: medium
---

# Background / Preliminaries Cards

## VBASE - Sections 2-3 Setup

Source pointer: [VBASE source note](../../../source-notes/vbase-2023.md); raw PDF Sections 2 and 3 setup around database/vector-index division and relaxed monotonicity.

Use when writing: background for a paper whose contribution depends on query semantics or index/engine interfaces.

Section role: define the abstraction that the design will later exploit.

Argument skeleton:

1. Explain what current vector indexes expose to the system.
2. Explain what database query execution needs.
3. Identify the mismatch between those two surfaces.
4. Introduce the property that bridges them.
5. Delay implementation details until the reader accepts the abstraction.

Reusable writing move: VBASE turns background into a setup for the central theorem-like idea. It is not a generic literature survey.

Do not copy: the formalism unless the rest of the paper will use it repeatedly.

## Starling - Section 2 Preliminaries

Source pointer: [Starling source note](../../../source-notes/starling-2024.md); raw PDF Section 2, "PRELIMINARIES".

Use when writing: background for a disk-resident ANNS paper with a specific workload unit.

Section role: define query types, the data-segment setting, and the optimization objective before the design appears.

Argument skeleton:

1. Define the query types the system supports.
2. Define the data segment as the deployment unit.
3. State the resource constraints on that unit.
4. Convert the setup into an optimization objective.

Reusable writing move: the section cuts away irrelevant ANN taxonomy and only defines concepts needed for the later design.

Do not copy: the narrowness if your paper needs a broader system model or distributed setting.

## SmartANNS - Section 2 Background and Motivation

Source pointer: [SmartANNS source note](../../../source-notes/smartanns-2024.md); raw PDF Section 2, "Background and Motivation".

Use when writing: background for hardware-software co-design, near-data processing, SmartSSD, or accelerator-assisted ANNS.

Section role: connect ANNS basics to the relevant hardware substrate.

Argument skeleton:

1. Briefly introduce ANNS and the index family used.
2. Introduce the hardware substrate and its constraints.
3. Explain why naive use of the hardware is insufficient.
4. Prepare the reader for the system overview.

Reusable writing move: SmartANNS tries to make hardware context relevant to ANNS rather than presenting a separate hardware survey.

Do not copy: the hardware background unless your paper proves that hardware placement changes the ANNS execution path.
