---
id: anns-section-exemplars-evaluation
type: analysis
status: active
created: 2026-05-26
updated: 2026-05-29
tags: [anns, paper-writing, evaluation]
source_count: 3
sources:
  - raw/sources/papers/spfresh-2023.pdf
  - raw/sources/papers/odinann-2026.pdf
  - raw/sources/papers/starling-2024.pdf
related:
  - anns-section-writing-exemplars
confidence: medium
---

# Evaluation Exemplars

## Top Three

| Rank | Paper | Score | Why it works | Weakness |
|---|---:|---:|---|---|
| 1 | [SPFresh](../../source-notes/spfresh-2023.md) | 9.6 | Best evaluation discipline for dynamic search: freshness, accuracy, tail latency, update throughput, memory use, and resource behavior are all tested against the claimed problem. | It is harder to reuse for static-search papers. |
| 2 | [OdinANN](../../source-notes/odinann-2026.md) | 9.5 | Best graph-update evaluation: latency fluctuation, percentile latency, insert throughput, memory peak, disk-space/write tradeoff, and recall/index-quality drift are all visible. | It is insert-centric; delete support is less direct. |
| 3 | [Starling](../../source-notes/starling-2024.md) | 9.4 | Best disk/index evaluation: performance, I/O efficiency, index construction, ablation, sensitivity, scalability, and billion-scale behavior are well aligned. | Segment-level framing means some comparisons are not direct whole-system comparisons. |

## What To Steal

Make each graph answer a reviewer objection. Accuracy, latency, throughput, cost, memory, update freshness, I/O count, construction time, and scalability are different objections.

Use matched-recall comparisons whenever possible. Raw QPS without recall control is weak evidence in ANNS.

Include ablations that map exactly to design components. Starling's layout/search ablations and SPFresh's update-path analysis are strong because they isolate mechanisms.

## What Not To Copy

Do not compare only against old baselines when newer systems attack the same bottleneck.

Do not use one headline speedup as the evaluation. Reviewers need to know when the system loses.

Do not hide cost assumptions. For GPU, SSD, CXL, and SmartSSD papers, hardware cost and capacity are part of the claim.
