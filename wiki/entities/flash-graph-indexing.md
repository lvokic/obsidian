---
id: flash-graph-indexing
type: entity
status: active
created: 2026-05-19
updated: 2026-05-19
tags:
  - method
  - ann
  - hnsw
  - graph-index
  - simd
  - quantization
source_count: 1
sources:
  - raw/inbox/flash-graph-indexing-2025.pdf
related:
  - flash-graph-indexing-2025
  - hnsw
  - nsg
  - simd-and-vectorization-for-ann-systems
  - scalar-and-binary-quantization-for-ann
confidence: medium
---

# Flash Graph Indexing

## Profile

Flash is a CPU-oriented graph-index construction accelerator for HNSW-style ANN indexes. It uses compact construction-time codes, PCA/PQ-style subspaces, register-resident distance tables, and a neighbor-list layout designed for SIMD batch distance comparisons.

## Core Mechanism

- Replace many full-vector construction-time comparisons with compact code comparisons.
- Store neighbor IDs and codewords together to avoid random raw-vector fetches during construction.
- Use asymmetric distance tables for Candidate Acquisition and symmetric distance tables for Neighbor Selection.
- Quantize table entries so SIMD registers can hold and shuffle partial distances efficiently.
- Keep raw vectors available for final search-time reranking.

## Why It Matters

Flash is useful when build time, periodic rebuilds, or shard refreshes are the bottleneck. It also clarifies that query-time quantization and construction-time quantization are different design problems: construction must preserve navigable-neighbor choices, not only nearest-candidate scores.

## Related Pages

- [Flash Source Note](../source-notes/flash-graph-indexing-2025.md)
- [HNSW](hnsw.md)
- [NSG](nsg.md)
- [SIMD and Vectorization for ANN Systems](../topics/simd-and-vectorization-for-ann-systems.md)
- [Scalar and Binary Quantization for ANN](../topics/scalar-and-binary-quantization-for-ann.md)
