---
id: panorama
type: entity
status: active
created: 2026-05-19
updated: 2026-05-19
tags:
  - method
  - ann
  - refinement
  - learned-transform
  - simd
source_count: 1
sources:
  - raw/inbox/panorama-2025.pdf
related:
  - panorama-2025
  - hnsw
  - faiss
  - product-quantization
  - simd-and-vectorization-for-ann-systems
confidence: medium
---

# Panorama

## Profile

Panorama is an ANN refinement accelerator. It uses a learned orthogonal transform and cumulative partial-distance bounds to prune candidates before all dimensions are processed, while preserving exact L2 refinement semantics.

## Core Mechanism

- Learn an orthogonal transform that concentrates energy in early dimensions.
- Process transformed vectors level by level.
- Use Cauchy-Schwarz lower and upper bounds from prefix products and tail energies.
- Stop processing a candidate once its lower bound exceeds the current kth-best threshold.
- Provide separate execution modes for point-centric graph/tree layouts and batched contiguous layouts.

## Why It Matters

Panorama is a good reference when an ANN system's bottleneck is exact verification after candidate generation. It is complementary to index-selection methods: it can sit behind IVFFlat, IVFPQ, HNSW, MRPT, or Annoy, with the largest gains expected when refinement dominates query time.

## Related Pages

- [Panorama Source Note](../source-notes/panorama-2025.md)
- [HNSW](hnsw.md)
- [FAISS](faiss.md)
- [Product Quantization](product-quantization.md)
- [SIMD and Vectorization for ANN Systems](../topics/simd-and-vectorization-for-ann-systems.md)
