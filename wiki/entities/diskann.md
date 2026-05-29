---
id: diskann
type: entity
status: active
created: 2026-04-08
updated: 2026-05-29
tags:
  - system
  - ann
  - ssd
source_count: 2
sources:
  - raw/sources/papers/diskann-2019.pdf
  - raw/sources/papers/odinann-2026.pdf
related:
  - diskann-2019
  - odinann
  - hnsw
  - nsg
  - proximity-graph-theory-for-ann
  - second-tier-memory-for-vector-search
  - approximate-nearest-neighbor-search
confidence: high
---

# DiskANN

## Profile

DiskANN is an SSD-resident billion-scale ANN system that combines the Vamana graph index with storage-aware search layout and caching.

## Why It Matters

- It is a reference system for high-recall ANN under constrained DRAM budgets.
- It anchors the SSD-centered design point in this vault's ANN systems branch.
- It is also the main graph-based baseline for dynamic-update work such as [OdinANN](odinann.md), which critiques DiskANN/FreshDiskANN-style buffered inserts because periodic merge can increase latency variance and peak memory.

## Related Pages

- [DiskANN Source Note](../source-notes/diskann-2019.md)
- [OdinANN](odinann.md)
- [HNSW](hnsw.md)
- [NSG](nsg.md)
- [Proximity Graph Theory for ANN](../topics/proximity-graph-theory-for-ann.md)
- [Second-tier Memory for Vector Search](../topics/second-tier-memory-for-vector-search.md)
- [Approximate Nearest Neighbor Search](../topics/approximate-nearest-neighbor-search.md)
