---
id: multi-probe-lsh-2007
type: source-note
status: active
created: 2026-05-29
updated: 2026-05-29
tags:
  - ann
  - lsh
  - multiprobe
  - nearest-neighbor
  - classical-baseline
source_count: 1
sources:
  - raw/inbox/multi-probe-lsh-vldb-test-of-time-2017.pdf
related:
  - multi-probe-lsh
  - falconn
  - flann
  - ann-benchmarks
  - approximate-nearest-neighbor-search
confidence: high
---

# Multi-Probe LSH: Efficient Indexing for High-Dimensional Similarity Search

## Bibliographic Note

Qin Lv, William Josephson, Zhe Wang, Moses Charikar, and Kai Li. 2007. *Multi-Probe LSH: Efficient Indexing for High-Dimensional Similarity Search*. VLDB 2007, Vienna.

The inbox filename records this as a VLDB test-of-time source. This note focuses on the technical content of the 2007 paper.

The related entity page is [Multi-Probe LSH](../entities/multi-probe-lsh.md).

## Core Problem

Basic LSH supports approximate nearest-neighbor search, but high recall often requires many independent hash tables. This creates large memory overhead and expensive index construction. Entropy-based LSH also probes multiple buckets, but the paper argues that it produces redundant buckets and depends on hard-to-tune nearest-neighbor distance assumptions.

## Design

Multi-Probe LSH keeps the basic LSH table structure but changes query processing. Instead of looking up only the exact bucket for each hash table, it derives a probing sequence of perturbation vectors and checks several nearby buckets that are likely to contain near neighbors.

The paper develops two probing strategies.

- Step-wise probing checks all one-step perturbations, then two-step perturbations, and so on.
- Query-directed probing orders perturbations by their success probability for the specific query and avoids duplicate buckets.

The key insight is that a small number of well-chosen probes per table can replace many separate hash tables.

## Evaluation Facts

- Evaluates on two high-dimensional datasets: an image dataset with about 1.3M objects and 64 dimensions, and an audio dataset with about 54K objects and 192 dimensions.
- Compares basic LSH, entropy-based LSH, and multi-probe LSH.
- Reports that, at the same recall, multi-probe LSH reduces the number of basic LSH hash tables by a factor of 14-18.
- Reports that, compared with entropy-based LSH, multi-probe LSH uses less query time and 5-8x fewer hash tables.
- Shows query-directed probing is much stronger than step-wise probing, often requiring an order of magnitude fewer probes for similar recall.
- Measures search quality by recall and effective error ratio, and search cost by query time plus number of hash tables.

## Why It Matters

Multi-Probe LSH is a direct classical ANN source and an important counterweight to the vault's graph-heavy branch. It explains why "more buckets per table" can be a space-saving substitute for "more independent hash tables."

It also gives historical context for later practical multiprobe LSH libraries such as [FALCONN](../entities/falconn.md), although FALCONN focuses on angular/cosine distance and cross-polytope hashing rather than the exact Euclidean LSH setup here.

## Limits And Open Questions

- The experiments are small by modern billion-scale vector-search standards.
- The paper predates modern HNSW, DiskANN, IVF-PQ, and learned embedding workloads.
- It is strongest as a conceptual and baseline reference for LSH space-time tradeoffs, not as a default production baseline for current high-recall vector databases.
- A useful follow-up is to compare multiprobe LSH assumptions against modern embedding distributions and ANN-Benchmarks-style recall-latency Pareto curves.

## Related Pages

- [Multi-Probe LSH](../entities/multi-probe-lsh.md)
- [FALCONN](../entities/falconn.md)
- [FLANN](../entities/flann.md)
- [ANN-Benchmarks](../entities/ann-benchmarks.md)
- [Approximate Nearest Neighbor Search](../topics/approximate-nearest-neighbor-search.md)
