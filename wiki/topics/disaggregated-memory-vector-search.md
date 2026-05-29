---
id: disaggregated-memory-vector-search
type: topic
status: active
created: 2026-04-08
updated: 2026-05-29
tags:
  - ann
  - systems
  - disaggregated-memory
  - cxl
  - rdma
source_count: 5
sources:
  - raw/sources/papers/cxl-anns-2024.pdf
  - raw/sources/papers/d-hnsw-2025.pdf
  - raw/sources/papers/performance-index-size-dilemma-2024.pdf
  - raw/sources/papers/cxl-memory-characterization-2023.pdf
  - raw/inbox/chameleon-ralm-vector-search-vldb-best-scalable-data-science-2025.pdf
related:
  - cxl-anns
  - d-hnsw
  - chameleon-ralm
  - cxl-disaggregated-memory-systems
  - second-tier-memory-for-vector-search
  - approximate-nearest-neighbor-search
confidence: medium
---

# Disaggregated Memory Vector Search

## Summary

This topic covers ANN systems that move beyond local-DRAM-only design and explicitly optimize for disaggregated or second-tier memory access patterns.

## Current View

- Naively porting ANN indexes to far memory underperforms because graph traversal issues many small, irregular accesses.
- Strong designs combine index-layout changes, caching or prefetching, and execution-pipeline restructuring.
- Hardware-aware coordination remains first-class, but the hardware assumption matters: CXL-ANNS assumes custom endpoint acceleration, d-HNSW assumes RDMA-scale disaggregation, and Chameleon assumes FPGA-based disaggregated memory nodes for IVF-PQ search.

[Chameleon RALM](../entities/chameleon-ralm.md) adds a RAG-serving version of disaggregated vector search. It keeps IVF-list selection and LLM inference on GPUs while pushing large PQ-code storage, PQ decoding, distance evaluation, and local top-k selection into FPGA-attached memory nodes.

## Design Axes

| Axis | CXL-ANNS | d-HNSW | Chameleon |
|---|---|---|---|
| Memory fabric | CXL | RDMA/disaggregated memory | FPGA-attached disaggregated memory nodes |
| Main bottleneck | device/host coordination | network round trips | PQ-code scan plus RALM accelerator balance |
| Computation | hardware/software co-design | host-side traversal adaptations | near-memory PQ decoding and top-k selection |
| Index family | ANN acceleration co-design | HNSW | IVF-PQ |
| Current vault role | external related work | external related work | RAG/vector-search accelerator reference |

## Open Questions

- Which design principles transfer cleanly across CXL, RDMA, and other memory fabrics?
- How much of measured gain comes from algorithmic changes versus hardware-specific tuning?
- When is disaggregation justified by accelerator utilization rather than only memory capacity?

## Related Pages

- [CXL-ANNS](../entities/cxl-anns.md)
- [d-HNSW](../entities/d-hnsw.md)
- [Chameleon RALM](../entities/chameleon-ralm.md)
- [CXL Disaggregated Memory Systems](cxl-disaggregated-memory-systems.md)
- [Second-tier Memory for Vector Search](second-tier-memory-for-vector-search.md)
- [Approximate Nearest Neighbor Search](approximate-nearest-neighbor-search.md)
