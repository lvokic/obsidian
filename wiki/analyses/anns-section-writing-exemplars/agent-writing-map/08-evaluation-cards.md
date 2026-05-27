---
id: anns-section-agent-map-evaluation
type: analysis
status: active
created: 2026-05-27
updated: 2026-05-27
tags: [anns, paper-writing, evaluation, agent-map]
source_count: 3
sources:
  - raw/sources/papers/spfresh-2023.pdf
  - raw/sources/papers/starling-2024.pdf
  - raw/sources/papers/gustann-2025.pdf
related:
  - anns-section-agent-writing-map
confidence: medium
---

# Evaluation Cards

## SPFresh - Section 5 Evaluation

Source pointer: [SPFresh source note](../../../source-notes/spfresh-2023.md); raw PDF Section 5.

Use when writing: evaluation for mutable, online, update-heavy vector search systems.

Section role: prove that freshness support does not destroy search latency, accuracy, or resource usage.

Evaluation skeleton:

1. Define setup and update workloads.
2. Compare against rebuild-based or update-capable baselines.
3. Report search latency and tail behavior.
4. Report accuracy under updates.
5. Report update throughput and foreground/background interaction.
6. Report resource usage and parameter sensitivity.

Reusable writing move: SPFresh evaluates the operational claim, not just nearest-neighbor speed.

Do not copy: update-specific experiments for a static-search system.

## Starling - Section 6 Experiments

Source pointer: [Starling source note](../../../source-notes/starling-2024.md); raw PDF Section 6, "EXPERIMENTS".

Use when writing: evaluation for disk-resident index layout and I/O-efficient search.

Section role: prove that layout and search strategy reduce I/O while preserving accuracy and scalability.

Evaluation skeleton:

1. Define dataset, segment memory/disk budget, baselines, and metrics.
2. Compare search performance at matched accuracy.
3. Measure I/O efficiency directly.
4. Measure index cost.
5. Run ablations for layout and search components.
6. Run sensitivity and scalability studies.
7. Include large-scale or billion-scale confirmation.

Reusable writing move: Starling's ablations match the design decomposition, which makes the evaluation feel complete.

Do not copy: segment-specific comparisons if your system's evaluation unit is a whole server or distributed cluster.

## GustANN - Section 5 Evaluation

Source pointer: [GustANN source note](../../../source-notes/gustann-2025.md); raw PDF Section 5.

Use when writing: evaluation for high-throughput hardware-assisted ANNS systems.

Section role: prove throughput, cost-effectiveness, and bottleneck removal under GPU/SSD constraints.

Evaluation skeleton:

1. Define hardware setup and datasets.
2. Compare overall throughput and accuracy against CPU/GPU/SSD baselines.
3. Break down kernel, transfer, and pipeline contributions.
4. Run sensitivity analysis.
5. Analyze cost.
6. Show latency tradeoff explicitly.

Reusable writing move: GustANN is honest that max throughput and low latency are not the same operating point.

Do not copy: cost or throughput claims without stating hardware assumptions.
