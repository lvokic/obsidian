---
id: multi-probe-lsh
type: entity
status: active
created: 2026-05-29
updated: 2026-05-29
tags:
  - ann
  - lsh
  - multiprobe
  - nearest-neighbor
source_count: 1
sources:
  - raw/inbox/multi-probe-lsh-vldb-test-of-time-2017.pdf
related:
  - multi-probe-lsh-2007
  - falconn
  - flann
  - ann-benchmarks
  - approximate-nearest-neighbor-search
confidence: high
---

# Multi-Probe LSH

## Profile

Multi-Probe LSH is a classical approximate nearest-neighbor indexing method that reduces LSH memory overhead by probing multiple carefully chosen buckets in each hash table.

## Main Ideas

- Keep ordinary LSH hash tables.
- At query time, compute likely bucket perturbations around the query's primary bucket.
- Probe several nearby buckets per table instead of building many independent tables.
- Use query-directed probing to visit high-probability, non-duplicate buckets first.

## Position In The Vault

Multi-Probe LSH strengthens the non-graph ANN branch alongside [FLANN](flann.md) and [FALCONN](falconn.md). It is especially useful when a paper needs to acknowledge classical LSH space-time tradeoffs before moving to modern graph, PQ, or hybrid systems.

## Key Evidence

The VLDB 2007 paper reports 14x-18x fewer hash tables than basic LSH at similar recall, and 5x-8x fewer hash tables plus lower query time than entropy-based LSH.

## Limits

This method is not a graph index and should not be used to explain graph traversal, pruning, or disk-resident search. It is also not the strongest current production baseline for high-recall billion-scale embedding search, but it remains a core historical ANN reference.

## Related Pages

- [Multi-Probe LSH Source Note](../source-notes/multi-probe-lsh-2007.md)
- [FALCONN](falconn.md)
- [FLANN](flann.md)
- [ANN-Benchmarks](ann-benchmarks.md)
- [Approximate Nearest Neighbor Search](../topics/approximate-nearest-neighbor-search.md)
