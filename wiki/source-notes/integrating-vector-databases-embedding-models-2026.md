---
id: integrating-vector-databases-embedding-models-2026
type: source-note
status: active
created: 2026-05-29
updated: 2026-05-29
tags:
  - vector-database
  - embedding-models
  - data-integration
  - similarity-search
  - ann
source_count: 1
sources:
  - raw/inbox/integrating-vector-databases-across-embedding-models-sigmod-hm-2026.pdf
related:
  - vector-database-integration
  - milvus
  - vbase
  - approximate-nearest-neighbor-search
confidence: high
---

# Integrating Vector Databases Across Embedding Models

## Bibliographic Note

Beining Yang, Yang Cao, and Yang Ren. 2025. *Integrating Vector Databases across Embedding Models*. Proc. ACM Manag. Data 3(6), Article 338, SIGMOD/PODS 2026. DOI: 10.1145/3769803.

The related entity page is [Vector Database Integration](../entities/vector-database-integration.md).

## Core Problem

Vector databases are not interoperable in the same way relational databases are. Two databases may encode related objects with different embedding models, so the same object can occupy incompatible coordinates across databases. Directly taking the union of two vector stores does not create a searchable shared space, and the original objects or embedding models may be unavailable for backfilling.

The paper asks whether two vector databases can be integrated using only the vectors, plus reference pairs when available, so that top-k search can run across the combined collection.

## Design

The paper first tests a global isometry hypothesis: vectors for the same objects under two embedding models might be alignable by a single distance-preserving transformation. Experiments reject this as a general rule.

The main proposal is localized align-to-merge, or LA2M.

- Use reference vector pairs across two vector databases, where each pair encodes the same object under two embedding models.
- Cluster the reference vectors into local neighborhoods.
- Fit a separate Procrustes-style isometry for each local cluster.
- For a non-reference source vector, find the nearest reference-cluster centroid and map it with that cluster's isometry.
- Return the transformed source database plus the target database as the integrated vector database.

The key hypothesis is local isometry: global embedding spaces can disagree, but nearby regions that matter for top-k search are often approximately isometric.

## Evaluation Facts

- Evaluates five text retrieval benchmarks: SciFact, NFCorpus, ArguAna, SciDocs, and FiQA-2018.
- Evaluates six embedding models: GloVe, FastText, NV-Embed-V2, GTE-Qwen2, OpenAI-Ada, and Mistral.
- Compares Union, global A2M, MLP-based global alignment, CCA, GW, LA2M, and MLP-based local alignment.
- Reports LA2M as the best method across the reported benchmark/model-pair settings under recall@100, recall@100 over source-only answers, relative NDCG, and integration error.
- Reports that global A2M can be no better than Union because a single global isometry does not fit real embedding spaces.
- Reports that LA2M can recover source-side answers that Union cannot retrieve; for example, when integrating NV-Embed-V2 into OpenAI-Ada, recall@100 over source-side answers reaches 90.69% on SciFact.
- Reports that isometry is important: local MLP alignment can have lower reference alignment error but worse retrieval behavior because it does not preserve neighborhood distances.

## Why It Matters

This paper adds a vector-database interoperability branch to the vault. It is not about making a single ANN index faster; it is about making separate vector databases searchable together when they were produced by different embedding models.

For ANNS and vector DB papers, it clarifies a distinct production problem: embedding model migration, backfilling, privacy-preserving federation, and cloud-edge search can require integration across embedding spaces rather than only faster nearest-neighbor operators.

## Limits And Open Questions

- LA2M needs reference pairs or a way to generate them. If references are weak, sparse, or not locally representative, integration quality can degrade.
- Absolute recall remains bounded by the native quality of the embedding models and benchmark difficulty.
- The method integrates vector spaces; it does not solve index maintenance, concurrency, filtering, or transactional vector DB behavior.
- The paper's strongest evidence is text retrieval; image and other modalities need separate checks before broad claims.
- A useful follow-up is whether LA2M-transformed IVF or HNSW indexes retain practical search performance and update behavior in a full vector DBMS.

## Related Pages

- [Vector Database Integration](../entities/vector-database-integration.md)
- [Milvus](../entities/milvus.md)
- [VBASE](../entities/vbase.md)
- [Approximate Nearest Neighbor Search](../topics/approximate-nearest-neighbor-search.md)
