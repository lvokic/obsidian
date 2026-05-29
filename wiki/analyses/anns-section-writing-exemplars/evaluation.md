---
id: anns-section-exemplars-evaluation
type: analysis
status: active
created: 2026-05-26
updated: 2026-05-29
tags: [anns, paper-writing, evaluation]
source_count: 5
sources:
  - raw/sources/papers/spfresh-2023.pdf
  - raw/sources/papers/odinann-2026.pdf
  - raw/inbox/warp-multi-vector-retrieval-sigir-best-paper-2025.pdf
  - raw/sources/papers/starling-2024.pdf
  - raw/inbox/chameleon-ralm-vector-search-vldb-best-scalable-data-science-2025.pdf
related:
  - anns-section-writing-exemplars
confidence: medium
---

# Evaluation Exemplars

## Top Five

| Rank | Paper | Score | Why it works | Weakness |
|---|---:|---:|---|---|
| 1 | [SPFresh](../../source-notes/spfresh-2023.md) | 9.6 | Best evaluation discipline for dynamic search: freshness, accuracy, tail latency, update throughput, memory use, and resource behavior are all tested against the claimed problem. | It is harder to reuse for static-search papers. |
| 2 | [OdinANN](../../source-notes/odinann-2026.md) | 9.5 | Best graph-update evaluation: latency fluctuation, percentile latency, insert throughput, memory peak, disk-space/write tradeoff, and recall/index-quality drift are all visible. | It is insert-centric; delete support is less direct. |
| 3 | [WARP](../../source-notes/warp-multi-vector-retrieval-2025.md) | 9.4 | Best new execution-engine evaluation: it reports quality, latency, scalability, thread scaling, and memory footprint against appropriate XTR/ScaNN and PLAID baselines. | It is multi-vector IR, not a standard billion-scale single-vector ANN evaluation. |
| 4 | [Starling](../../source-notes/starling-2024.md) | 9.3 | Strong disk/index evaluation: performance, I/O efficiency, construction, ablation, sensitivity, scalability, and billion-scale behavior are aligned with the claim. | Segment-level framing means some comparisons are not direct whole-system comparisons. |
| 5 | [Chameleon](../../source-notes/chameleon-ralm-vector-search-2024.md) | 9.0 | It evaluates vector-search latency, energy, recall impact of approximate queues, end-to-end RALM speedups, and accelerator-ratio sensitivity. | It relies partly on synthetic RALM-scale vector datasets and hardware-specific assumptions. |

## What To Steal

Make each graph answer a reviewer objection. Accuracy, latency, throughput, cost, memory, update freshness, I/O count, construction time, and scalability are different objections.

Use matched-recall comparisons whenever possible. Raw QPS without recall control is weak evidence in ANNS.

Include ablations that map exactly to design components. Starling's layout/search ablations and SPFresh's update-path analysis are strong because they isolate mechanisms.

The lower slots are still useful but conditional. Starling is the disk-layout evaluation model; Chameleon is the accelerator/service evaluation model, not a generic ANN evaluation template.

## What Not To Copy

Do not compare only against old baselines when newer systems attack the same bottleneck.

Do not use one headline speedup as the evaluation. Reviewers need to know when the system loses.

Do not hide cost assumptions. For GPU, SSD, CXL, and SmartSSD papers, hardware cost and capacity are part of the claim.
