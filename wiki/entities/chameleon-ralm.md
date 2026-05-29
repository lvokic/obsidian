---
id: chameleon-ralm
type: entity
status: active
created: 2026-05-29
updated: 2026-05-29
tags:
  - ann
  - vector-search
  - ralm
  - fpga
  - disaggregated-accelerator
source_count: 1
sources:
  - raw/inbox/chameleon-ralm-vector-search-vldb-best-scalable-data-science-2025.pdf
related:
  - chameleon-ralm-vector-search-2024
  - product-quantization
  - faiss
  - disaggregated-memory-vector-search
  - approximate-nearest-neighbor-search
confidence: high
---

# Chameleon RALM

## Profile

Chameleon is a heterogeneous and disaggregated accelerator system for retrieval-augmented language model serving. It pairs GPU language-model inference with FPGA-based disaggregated memory nodes for large-scale IVF-PQ vector search.

## Main Ideas

- Split the RALM pipeline into GPU LLM inference, GPU IVF-list selection, FPGA near-memory PQ-code scanning, and CPU coordination.
- Store PQ-code shards in FPGA-attached DRAM so vector search capacity scales separately from GPU memory.
- Use parallel PQ decoding units to turn memory bandwidth into distance-evaluation throughput.
- Use an approximate hierarchical priority queue to make top-k selection affordable on FPGA resources.
- Treat disaggregation as a utilization mechanism: the right FPGA:GPU ratio depends on model size and retrieval interval.

## Position In The Vault

Chameleon is closest to [Disaggregated Memory Vector Search](../topics/disaggregated-memory-vector-search.md), but it is not a CXL or RDMA graph-search system. It is an IVF-PQ accelerator design for RALM workloads where vector search and LLM inference have different scaling needs.

It also belongs in the quantized ANN branch because its hardware argument is built around PQ-code scan bottlenecks rather than raw-vector graph traversal.

## Key Evidence

The paper reports up to 23.72x lower vector-search latency for ChamVS versus optimized CPU search, 5.8x-26.2x better per-query energy efficiency than CPU, and up to 2.16x lower RALM latency plus 3.18x higher RALM throughput versus a hybrid CPU-GPU baseline.

## Limits

Chameleon should not be treated as evidence for graph indexes or CPU SIMD search. Its strongest evidence is for disaggregated IVF-PQ search in RALM serving, with an FPGA-specific top-k and PQ-decoding design.

## Related Pages

- [Chameleon Source Note](../source-notes/chameleon-ralm-vector-search-2024.md)
- [Product Quantization](product-quantization.md)
- [FAISS](faiss.md)
- [Disaggregated Memory Vector Search](../topics/disaggregated-memory-vector-search.md)
- [Approximate Nearest Neighbor Search](../topics/approximate-nearest-neighbor-search.md)
