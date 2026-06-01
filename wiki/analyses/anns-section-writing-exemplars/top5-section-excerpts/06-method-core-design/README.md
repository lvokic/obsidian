# Method / Core Design

Local boundary-cropped PDFs for the current Top 5 section-writing exemplars. Each excerpt starts on the physical PDF page where the designated section appears and stops at the minimal page boundary that preserves the target section tail. If the next heading shares the same physical page, that page is kept; if the next section starts on a fresh page, it is not included.

Page ranges are physical PDF pages, not necessarily paper-stamped page numbers. Some excerpts intentionally include adjacent material at the beginning or end because the source PDF uses two-column layout.

Ranking source: [Method / Core Design](../../core-design-algorithms.md).

| Rank | Paper | Boundary-cropped designated section | Physical pages | Excerpt PDF | Source PDF | Source note |
|---|---|---|---|---|---|---|
| 1 | Starling | Sections 3-5 Design Philosophy, Data Layout, and Search Strategy; stops on page shared with Section 6 opening | 6-15 | [01-starling.pdf](01-starling.pdf) | [raw/sources/papers/starling-2024.pdf](../../../../../raw/sources/papers/starling-2024.pdf) | [../../source-notes/starling-2024.md](../../../../source-notes/starling-2024.md) |
| 2 | WARP | Section 4 WARP; stops on page shared with Section 5 opening | 3-6 | [02-warp.pdf](02-warp.pdf) | [raw/inbox/warp-multi-vector-retrieval-sigir-best-paper-2025.pdf](../../../../../raw/inbox/warp-multi-vector-retrieval-sigir-best-paper-2025.pdf) | [../../source-notes/warp-multi-vector-retrieval-2025.md](../../../../source-notes/warp-multi-vector-retrieval-2025.md) |
| 3 | SPFresh | Sections 3-4 LIRE Protocol and Design/Implementation; stops on page shared with Section 5 opening | 5-10 | [03-spfresh.pdf](03-spfresh.pdf) | [raw/sources/papers/spfresh-2023.pdf](../../../../../raw/sources/papers/spfresh-2023.pdf) | [../../source-notes/spfresh-2023.md](../../../../source-notes/spfresh-2023.md) |
| 4 | OdinANN | Section 3 Design and Implementation; stops on page shared with Section 4 opening | 5-9 | [04-odinann.pdf](04-odinann.pdf) | [raw/sources/papers/odinann-2026.pdf](../../../../../raw/sources/papers/odinann-2026.pdf) | [../../source-notes/odinann-2026.md](../../../../source-notes/odinann-2026.md) |
| 5 | Integrating Vector DBs | Sections 4-6 method and framework design; stops on page shared with Section 7 opening | 10-18 | [05-integrating-vector-dbs.pdf](05-integrating-vector-dbs.pdf) | [raw/inbox/integrating-vector-databases-across-embedding-models-sigmod-hm-2026.pdf](../../../../../raw/inbox/integrating-vector-databases-across-embedding-models-sigmod-hm-2026.pdf) | [../../source-notes/integrating-vector-databases-embedding-models-2026.md](../../../../source-notes/integrating-vector-databases-embedding-models-2026.md) |
