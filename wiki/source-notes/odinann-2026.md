---
id: odinann-2026
type: source-note
status: active
created: 2026-05-29
updated: 2026-05-29
tags:
  - ann
  - vector-search
  - graph-index
  - billion-scale
  - updates
  - ssd
source_count: 1
sources:
  - raw/sources/papers/odinann-2026.pdf
related:
  - odinann
  - diskann
  - spfresh
  - approximate-nearest-neighbor-search
  - second-tier-memory-for-vector-search
  - ann-benchmarking-methodology
confidence: high
---

# OdinANN: Direct Insert for Consistently Stable Performance in Billion-Scale Graph-Based Vector Search

## Bibliographic Note

Hao Guo and Youyou Lu. 2026. *OdinANN: Direct Insert for Consistently Stable Performance in Billion-Scale Graph-Based Vector Search*. FAST 2026, 24th USENIX Conference on File and Storage Technologies.

Primary PDF: <https://www.usenix.org/system/files/fast26-guo.pdf>.

The system name is [OdinANN](../entities/odinann.md).

## Core Problem

OdinANN targets online billion-scale graph-based ANN indexes where inserts and searches run concurrently on an SSD-resident graph.

The paper argues that the common buffered-insert design, represented by DiskANN/FreshDiskANN-style graph systems, is a poor fit for stable online serving. Buffered inserts absorb new vectors into an in-memory index and periodically merge them into the on-disk graph. That merge can interfere with frontend search through disk bandwidth contention, consumes high peak memory, and still bottlenecks on per-vector graph insertion work.

## Main Idea

OdinANN inserts new vectors directly into the on-disk graph rather than buffering them in memory for later batch merge.

Its direct-insert design is built around two main techniques:

- **GC-free update combining:** fixed-size graph records and page-level overprovisioning let OdinANN update graph records out of place, combine multiple record updates into fewer page writes, and reuse old record slots without a separate garbage-collection pass.
- **Approximate concurrency control:** searches need only a consistent snapshot of each record, not an atomic snapshot of the whole graph. Inserts can link against an approximate neighbor snapshot, use short per-record/per-page critical sections, move disk I/O out of the critical section with a write-back page cache, and reduce pruning cost with delta neighbor pruning.

The paper also keeps deletes buffered rather than direct. Deletes are recorded as IDs in memory, search uses a dynamic candidate pool to avoid returning deleted vectors, and periodic delete merge scans the on-disk index in two passes.

## Evaluation Facts

- On SIFT100M with another 100M inserted vectors, OdinANN's median search latency fluctuates by at most 1.07x, compared with DiskANN's 2.44x.
- In the same SIFT100M setting, OdinANN reports 13.3% lower average P50 latency than DiskANN and 51.7%/36.5%/28.4% lower P50/P90/P99 latency than SPFresh.
- On SIFT100M, OdinANN reports 1.15x and 1.99x average search throughput compared with DiskANN and SPFresh, respectively.
- OdinANN's peak memory usage is reported as 29.3% of DiskANN in the SIFT100M insert experiment, because it avoids DiskANN's in-memory insert index and merge deltas.
- On SIFT1B, the paper builds an 800M-vector initial index and inserts 200M vectors. OdinANN reports 85.7% and 62.1% median latency on average compared with DiskANN and SPFresh.
- The headline billion-scale result is simultaneous 5000 QPS search throughput and 1100 QPS insert throughput with stable median search latency around 3 ms.
- The insert-technique breakdown reaches 2000 QPS insert throughput with 11.1 ms median insert latency after combining async I/O, out-of-place overprovisioned updates, and delta pruning.
- The default overprovisioning policy costs about 2x disk space and about 2x disk writes, but the authors frame this as cheaper than the DRAM peak required by buffered inserts at billion scale.
- Approximate concurrency control costs some index quality: after inserting 93M vectors into DEEP100M, OdinANN needs about 4.5% more disk pages than DiskANN at the same recall.

## Relevance To This Vault

OdinANN is the graph-based counterpart to [SPFresh](../entities/spfresh.md)'s update-freshness story. SPFresh shows that cluster-based disk indexes can support incremental in-place updates through local rebalancing. OdinANN shows that graph-based SSD indexes can also support fresh inserts, but need a different mechanism because graph insert touches many scattered neighbor records.

For [DiskANN](../entities/diskann.md), OdinANN is both a continuation and a critique. It keeps the SSD-resident graph premise but treats buffered insert and merge as the main obstacle to stable online service.

For [ANN Benchmarking Methodology](../topics/ann-benchmarking-methodology.md), OdinANN is a useful example of why dynamic ANN evaluation must report latency fluctuation, percentile latency, update throughput, memory peak, disk space amplification, and recall drift rather than only static recall-QPS.

## Limits And Uncertainty

- The design trades extra SSD space for lower peak DRAM and more stable search latency. That trade-off depends on SSD capacity price, endurance, and workload write intensity.
- Delete support is still buffered. The paper argues delete merge has little interference, but this remains a different freshness model than direct insert.
- The direct-insert design is evaluated in a DiskANN-derived implementation. Its portability to other graph layouts, pruning policies, and vector database segment architectures needs separate validation.
- The relaxed concurrency model deliberately accepts approximate neighbor snapshots. The measured quality cost is modest in the paper, but it should be checked for other datasets and update distributions.

## Follow-up Questions

- Can OdinANN-style direct insert be combined with Starling-style segment/block layouts?
- How should SSD write amplification and endurance be reported for dynamic graph ANN systems?
- Can approximate concurrency control be exposed as a general graph-ANN update protocol, or is it tightly coupled to DiskANN/Vamana-style fixed-size records?
- What is the right benchmark for mixed search/insert/delete workloads: fixed update QPS, fixed search latency SLO, or fixed freshness bound?
