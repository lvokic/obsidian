---
id: warp-multi-vector-retrieval-2025
type: source-note
status: active
created: 2026-05-29
updated: 2026-05-29
tags:
  - ann
  - dense-retrieval
  - multi-vector-retrieval
  - compression
  - query-processing
source_count: 1
sources:
  - raw/inbox/warp-multi-vector-retrieval-sigir-best-paper-2025.pdf
related:
  - warp-multi-vector-retrieval
  - scann
  - product-quantization
  - vector-quantization
  - approximate-nearest-neighbor-search
confidence: high
---

# WARP: An Efficient Engine for Multi-Vector Retrieval

## Bibliographic Note

Jan Luca Scheerer, Matei Zaharia, Christopher Potts, Gustavo Alonso, and Omar Khattab. 2025. *WARP: An Efficient Engine for Multi-Vector Retrieval*. SIGIR 2025. DOI: 10.1145/3726302.3729904.

Code: https://github.com/jlscheerer/xtr-warp

The related entity page is [WARP Multi-Vector Retrieval](../entities/warp-multi-vector-retrieval.md).

## Core Problem

Multi-vector retrieval systems such as ColBERT, PLAID, and XTR improve retrieval quality by representing each document as many token vectors, but this creates a heavy serving path: candidate generation touches many token embeddings, decompression can dominate latency, and score aggregation can require a large sparse query-token by document score matrix.

WARP targets XTR-style ColBERT models. Its question is not how to train a better retriever, but how to make XTR-style retrieval efficient enough for CPU serving while preserving retrieval quality.

## Design

WARP combines PLAID-style compression and pruning with XTR's simplified scoring.

- During indexing, document token embeddings are clustered and stored as quantized residuals relative to centroids.
- Residuals are usually stored with 4 bits per dimension, giving 8x compression relative to float32 residual values.
- WARPSELECT uses query-centroid scores for candidate generation and also derives missing similarity estimates from cumulative cluster sizes.
- Implicit decompression avoids reconstructing full token vectors. It decomposes scoring into query-centroid scores plus a selective sum over residual bucket weights.
- Scoring uses two reductions: token-level max reduction for each query token, then document-level sum reduction with missing similarities filled in.
- Dedicated C++ kernels implement decompression/scoring and avoid explicitly materializing the full score matrix.

## Evaluation Facts

- Evaluates on six BEIR datasets and six LoTTE datasets.
- Reports 41x lower single-threaded end-to-end latency than the XTR reference implementation on LoTTE Pooled, cutting latency from over 6 seconds to 171 ms.
- Reports about 3x lower latency than ColBERTv2/PLAID while preserving retrieval quality.
- Reports XTR/WARP speedups of 4.6x-12.8x over optimized XTR/ScaNN on LoTTE and 2.7x-6x on BEIR.
- Reports WARP `b = 4` index size as 7.3x smaller than brute-force XTR and 2x smaller than XTR/ScaNN across the evaluated datasets.
- Shows that latency scales roughly with the square root of dataset size because the number of clusters is proportional to the square root of the collection size.
- Shows useful multi-thread scaling, with a 3.1x speedup at `nprobe = 32` using 16 threads on LoTTE Pooled.

## Why It Matters

WARP is not a standard single-vector ANN index, but it is highly relevant to vector-search systems because it exposes the execution costs of multi-vector retrieval: compressed token storage, missing-score imputation, candidate aggregation, and score-matrix reduction.

For ANNS system writing, WARP is a useful exemplar for explaining how an apparently model-level retrieval method becomes a systems problem once the engine must move, decompress, score, reduce, and sort large numbers of token-level vectors.

## Limits And Open Questions

- WARP is specialized for XTR-based ColBERT models and late-interaction retrieval.
- The paper focuses on CPU serving; the authors leave GPU implementation as future work.
- It does not replace standard ANN baselines such as HNSW, IVF-PQ, or graph SSD systems for single-vector search.
- A useful follow-up is whether WARP's implicit decompression and reduction strategy can combine with SIMD-heavy approaches such as EMVB or with vector-database engines that support filters and updates.

## Related Pages

- [WARP Multi-Vector Retrieval](../entities/warp-multi-vector-retrieval.md)
- [ScaNN](../entities/scann.md)
- [Product Quantization](../entities/product-quantization.md)
- [Vector Quantization](../topics/vector-quantization.md)
- [Approximate Nearest Neighbor Search](../topics/approximate-nearest-neighbor-search.md)
