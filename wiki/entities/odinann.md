---
id: odinann
type: entity
status: active
created: 2026-05-29
updated: 2026-05-29
tags:
  - system
  - ann
  - graph-index
  - updates
  - ssd
source_count: 1
sources:
  - raw/sources/papers/odinann-2026.pdf
related:
  - odinann-2026
  - diskann
  - spfresh
  - ann-benchmarking-methodology
  - approximate-nearest-neighbor-search
  - second-tier-memory-for-vector-search
confidence: high
---

# OdinANN

## Profile

OdinANN is a FAST 2026 SSD-resident graph ANN system that supports online direct inserts into the on-disk graph. It is implemented on a DiskANN-style graph index but avoids the buffered-insert and periodic-merge path that causes search-latency fluctuation in dynamic workloads.

## Main Ideas

- Directly insert vectors into the on-disk graph instead of first absorbing them into an in-memory delta index.
- Use fixed-size records plus page-level space overprovisioning so out-of-place graph updates can be combined and old slots reused without explicit garbage collection.
- Relax graph-operation atomicity through approximate concurrency control: searches observe per-record consistency, while inserts use approximate neighbor snapshots.
- Keep deletes buffered with a dynamic candidate pool and two-pass delete merge.

## Why It Matters

OdinANN extends the disk-resident graph-ANN branch from static serving toward fresh online updates. It is especially useful when comparing graph-based [DiskANN](diskann.md) against update-oriented cluster systems such as [SPFresh](spfresh.md): OdinANN keeps graph-search accuracy/performance advantages while trying to make update interference predictable.

## Key Evidence

The paper reports SIFT100M median search-latency fluctuation of 1.07x under concurrent inserts, compared with DiskANN's 2.44x. At billion scale, it reports 5000 QPS search throughput and 1100 QPS insert throughput with median search latency around 3 ms.

## Trade-offs

The central trade-off is SSD space and write amplification for lower DRAM peak and steadier online performance. The default overprovisioning policy is about 2x disk space and 2x disk writes, and relaxed concurrency can slightly reduce graph quality.

## Related Pages

- [OdinANN Source Note](../source-notes/odinann-2026.md)
- [DiskANN](diskann.md)
- [SPFresh](spfresh.md)
- [ANN Benchmarking Methodology](../topics/ann-benchmarking-methodology.md)
- [Approximate Nearest Neighbor Search](../topics/approximate-nearest-neighbor-search.md)
- [Second-tier Memory for Vector Search](../topics/second-tier-memory-for-vector-search.md)
