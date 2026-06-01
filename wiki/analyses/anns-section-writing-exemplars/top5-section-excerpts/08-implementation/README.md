# Implementation

Local boundary-cropped PDFs for the current Top 5 section-writing exemplars. Each excerpt starts on the physical PDF page where the designated section appears and stops at the minimal page boundary that preserves the target section tail. If the next heading shares the same physical page, that page is kept; if the next section starts on a fresh page, it is not included.

Page ranges are physical PDF pages, not necessarily paper-stamped page numbers. Some excerpts intentionally include adjacent material at the beginning or end because the source PDF uses two-column layout.

Ranking source: [Implementation](../../implementation.md).

| Rank | Paper | Boundary-cropped designated section | Physical pages | Excerpt PDF | Source PDF | Source note |
|---|---|---|---|---|---|---|
| 1 | SPFresh | Section 4 Design and Implementation; stops on page shared with Section 5 opening | 7-10 | [01-spfresh.pdf](01-spfresh.pdf) | [raw/sources/papers/spfresh-2023.pdf](../../../../../raw/sources/papers/spfresh-2023.pdf) | [../../source-notes/spfresh-2023.md](../../../../source-notes/spfresh-2023.md) |
| 2 | Chameleon | Section 5 Implementation; one page containing the Section 6 opening | 6 | [02-chameleon.pdf](02-chameleon.pdf) | [raw/inbox/chameleon-ralm-vector-search-vldb-best-scalable-data-science-2025.pdf](../../../../../raw/inbox/chameleon-ralm-vector-search-vldb-best-scalable-data-science-2025.pdf) | [../../source-notes/chameleon-ralm-vector-search-2024.md](../../../../source-notes/chameleon-ralm-vector-search-2024.md) |
| 3 | OdinANN | Section 3 Design and Implementation; stops on page shared with Section 4 opening | 5-9 | [03-odinann.pdf](03-odinann.pdf) | [raw/sources/papers/odinann-2026.pdf](../../../../../raw/sources/papers/odinann-2026.pdf) | [../../source-notes/odinann-2026.md](../../../../source-notes/odinann-2026.md) |
| 4 | GustANN | Section 4 Design and implementation details; stops on page shared with Section 5 opening | 8-15 | [04-gustann.pdf](04-gustann.pdf) | [raw/sources/papers/gustann-2025.pdf](../../../../../raw/sources/papers/gustann-2025.pdf) | [../../source-notes/gustann-2025.md](../../../../source-notes/gustann-2025.md) |
| 5 | Milvus | Sections 2-5 implementation-oriented system details; trimmed before the Applications page | 3-8 | [05-milvus.pdf](05-milvus.pdf) | [raw/sources/papers/milvus-2021.pdf](../../../../../raw/sources/papers/milvus-2021.pdf) | [../../source-notes/milvus-2021.md](../../../../source-notes/milvus-2021.md) |
