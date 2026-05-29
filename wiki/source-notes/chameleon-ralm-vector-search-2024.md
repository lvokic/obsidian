---
id: chameleon-ralm-vector-search-2024
type: source-note
status: active
created: 2026-05-29
updated: 2026-05-29
tags:
  - ann
  - vector-search
  - ralm
  - fpga
  - disaggregated-accelerator
  - product-quantization
source_count: 1
sources:
  - raw/inbox/chameleon-ralm-vector-search-vldb-best-scalable-data-science-2025.pdf
related:
  - chameleon-ralm
  - product-quantization
  - faiss
  - disaggregated-memory-vector-search
  - approximate-nearest-neighbor-search
confidence: high
---

# Chameleon: A Heterogeneous and Disaggregated Accelerator System for Retrieval-Augmented Language Models

## Bibliographic Note

Wenqi Jiang, Marco Zeller, Roger Waleffe, Torsten Hoefler, and Gustavo Alonso. 2024. *Chameleon: a Heterogeneous and Disaggregated Accelerator System for Retrieval-Augmented Language Models*. PVLDB 18(1): 42-52. DOI: 10.14778/3696435.3696439.

The related entity page is [Chameleon RALM](../entities/chameleon-ralm.md).

## Core Problem

Retrieval-augmented language model serving couples two expensive stages with different hardware profiles: LLM inference and large-scale vector search. The paper argues that a monolithic CPU-GPU setup is poorly matched to this workload because vector search over IVF-PQ databases needs very high memory capacity and efficient PQ-code scanning, while LLM inference needs GPU compute.

The specific ANN bottleneck is PQ-code scanning. Each PQ byte drives lookup-table reads and dependent accumulation, so CPU scans underuse memory-channel bandwidth. GPUs have higher bandwidth but limited memory capacity, and moving terabyte-scale PQ codes between CPU memory and GPU memory is not a clean answer.

## Design

Chameleon separates the RALM serving stack into independently scalable accelerators.

- ChamLM runs language-model inference on GPUs.
- ChamVS.idx scans the IVF index on GPUs colocated with ChamLM.
- ChamVS.mem stores quantized vector shards on FPGA-based disaggregated memory nodes.
- FPGA near-memory accelerators perform PQ decoding, distance evaluation, and local top-k selection.
- A CPU coordinator sends query vectors and selected IVF lists to the memory nodes, aggregates per-node results, and returns retrieved context to the GPU.

The most relevant ANN hardware mechanism is ChamVS. It uses parallel PQ decoding units to consume DRAM bandwidth and an approximate hierarchical priority queue for resource-efficient top-k selection on FPGA. The priority queue intentionally relaxes exact top-k selection because the overall ANN pipeline is already approximate.

## Evaluation Facts

- Evaluates billion-scale SIFT, Deep, and synthetic datasets with 16-byte, 32-byte, and 64-byte PQ codes.
- Sets IVF `nlist` around 32K and uses `nprobe = 32`, scanning about 0.1% of vectors per query.
- Reports ChamVS search latency speedups of 1.36x-6.13x for FPGA-CPU over CPU, and 2.25x-23.72x for FPGA-GPU over CPU.
- Reports 5.8x-26.2x better per-query energy efficiency than CPU baselines.
- Reports AHPQ recall nearly identical to software top-k on Deep and SIFT at `K = 100`.
- Reports Chameleon RALM latency reductions up to 2.16x and throughput speedups up to 3.18x over a hybrid CPU-GPU baseline.
- Shows that the optimal FPGA:GPU ratio changes across RALM model size and retrieval interval, motivating disaggregation rather than fixed accelerator ratios.

## Why It Matters

Chameleon extends the vault's ANN systems map beyond SSD, GPU, CXL, RDMA, and SmartSSD designs. Its central lesson is that RAG vector search is not just an algorithmic nearest-neighbor problem; it is a coupled serving problem where the search accelerator, model accelerator, memory capacity, and retrieval interval must be scaled together.

For ANNS papers, Chameleon is a useful reference when arguing that PQ scan bottlenecks can justify near-memory or accelerator-side distance evaluation. It is also a useful contrast to GPU-only systems: Chameleon keeps IVF-list selection on GPUs but pushes large PQ-code storage and scan work into disaggregated FPGA memory nodes.

## Limits And Open Questions

- The vector-search design is centered on IVF-PQ, not graph indexes.
- The hardware prototype uses FPGA memory nodes and a hardware TCP/IP stack; portability to commodity CXL or RDMA memory fabrics is not automatic.
- The evaluation models RALM settings and synthetic large vector datasets where real RALM vector corpora are unavailable.
- A useful follow-up is to compare Chameleon-style IVF-PQ disaggregation with graph-based SSD/GPU systems at matched retrieval quality, cost, energy, and update behavior.

## Related Pages

- [Chameleon RALM](../entities/chameleon-ralm.md)
- [Product Quantization](../entities/product-quantization.md)
- [FAISS](../entities/faiss.md)
- [Disaggregated Memory Vector Search](../topics/disaggregated-memory-vector-search.md)
- [Approximate Nearest Neighbor Search](../topics/approximate-nearest-neighbor-search.md)
