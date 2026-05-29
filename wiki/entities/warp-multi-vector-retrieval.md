---
id: warp-multi-vector-retrieval
type: entity
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
  - warp-multi-vector-retrieval-2025
  - scann
  - product-quantization
  - vector-quantization
  - approximate-nearest-neighbor-search
confidence: high
---

# WARP Multi-Vector Retrieval

## Profile

WARP is a CPU retrieval engine for XTR-style multi-vector retrieval. It accelerates late-interaction search by combining compressed residual storage, candidate-generation-aware missing similarity estimates, implicit decompression, and two-stage score reduction.

## Main Ideas

- Store document token vectors as centroid assignments plus low-bit residuals.
- Reuse query-centroid scores for both candidate generation and missing similarity imputation.
- Avoid reconstructing decompressed token vectors during retrieval.
- Reduce token scores first by per-query-token maxima and then by document-level sums.
- Use optimized C++ kernels to remove Python and score-matrix construction overhead.

## Position In The Vault

WARP is a multi-vector retrieval system, not a general-purpose ANN index. Its vault role is to connect vector-search systems to dense retrieval engines where the core bottleneck is no longer only nearest-neighbor search, but the downstream token-level scoring and aggregation path.

## Key Evidence

The paper reports 41x lower single-threaded latency than the XTR reference implementation on LoTTE Pooled, about 3x lower latency than ColBERTv2/PLAID, and 2x-4x smaller index size than the ScaNN-based XTR baseline depending on the residual bit width.

## Limits

WARP should not be cited as evidence that a single-vector ANN index is faster. Its claims are specific to XTR/ColBERT-style late interaction and depend on the scoring simplification that enables missing-similarity imputation and two-stage reduction.

## Related Pages

- [WARP Source Note](../source-notes/warp-multi-vector-retrieval-2025.md)
- [ScaNN](scann.md)
- [Product Quantization](product-quantization.md)
- [Vector Quantization](../topics/vector-quantization.md)
- [Approximate Nearest Neighbor Search](../topics/approximate-nearest-neighbor-search.md)
