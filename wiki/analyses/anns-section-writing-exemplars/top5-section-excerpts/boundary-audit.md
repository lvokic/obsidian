# Top 5 Section Excerpt Boundary Audit

Audit date: 2026-06-01.

Scope: all 50 PDFs under `top5-section-excerpts`.

Audit rule: each excerpt should start on the physical PDF page where the target section begins and stop at the minimal physical page boundary that preserves the target section tail. If the next heading shares the same page, the page is kept. If the next section begins on a fresh page, that fresh page is not included.

Automated checks passed: 50 README entries, 50 PDF files, expected page counts match all declared page ranges, and no generated PDF remains oversized.

## Corrections Made

- Renamed the excerpt package from `top4-section-excerpts` to `top5-section-excerpts` so the directory name matches the actual Top 5 scope.
- Removed the old `03-background-preliminaries` and `04-motivation-characterization` folders because they split background/motivation incorrectly and pulled in preliminary-style examples.
- Added `03-background-motivation` as the only Background & Motivation excerpt folder.
- Limited `03-background-motivation` to the Top 5 papers from the canonical card: OdinANN, FusionANNS, Chameleon, RUMMY, and Flash Graph Indexing.
- Removed the generated SmartANNS and AQR-HNSW background/motivation excerpts from the package because the user requested Top 5 only.
- Corrected `03-background-motivation/04-rummy.pdf` from pages `2-5` to `3-5` after rendering showed page 2 contained only title/abstract/introduction content before the target section page.
- Kept prior excerpt-boundary corrections for Starling, Integrating Vector DBs, and Milvus where the earlier Top 5 regeneration had carried too much adjacent content.

## Per-PDF Audit Table

| Folder | Rank | Paper | Physical pages | PDF | Audit result |
|---|---:|---|---|---|---|
| 01-abstract | 1 | SPFresh | `1` | `01-spfresh.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 01-abstract | 2 | WARP | `1` | `02-warp.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 01-abstract | 3 | OdinANN | `2` | `03-odinann.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 01-abstract | 4 | Chameleon | `1` | `04-chameleon.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 01-abstract | 5 | Starling | `1` | `05-starling.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 02-introduction | 1 | Starling | `2-4` | `01-starling.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 02-introduction | 2 | Integrating Vector DBs | `2-5` | `02-integrating-vector-dbs.pdf` | Pass: recompressed after regeneration; boundary unchanged. |
| 02-introduction | 3 | Chameleon | `1-2` | `03-chameleon.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 02-introduction | 4 | OdinANN | `2-3` | `04-odinann.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 02-introduction | 5 | VBASE | `2-3` | `05-vbase.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 03-background-motivation | 1 | OdinANN | `3-5` | `01-odinann.pdf` | Pass: combined Section 2 is preserved through the Section 3 opening on the same physical page. |
| 03-background-motivation | 2 | FusionANNS | `4-6` | `02-fusionanns.pdf` | Pass: combined Section 2 challenge analysis is preserved through the minimal physical-page boundary. |
| 03-background-motivation | 3 | Chameleon | `2-3` | `03-chameleon.pdf` | Pass: Section 2 background plus motivation is preserved; Section 3 opening shares the last physical page. |
| 03-background-motivation | 4 | RUMMY | `3-5` | `04-rummy.pdf` | Pass: corrected after visual inspection; the excerpt now starts on the physical page where Section 2 begins and ends on the page shared with Section 3. |
| 03-background-motivation | 5 | Flash Graph Indexing | `2-4` | `05-flash-graph-indexing.pdf` | Pass: Section 2 problem analysis is preserved through the page shared with Section 3. |
| 05-system-overview-architecture | 1 | Milvus | `3-4` | `01-milvus.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 05-system-overview-architecture | 2 | Chameleon | `3-4` | `02-chameleon.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 05-system-overview-architecture | 3 | SPFresh | `7-8` | `03-spfresh.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 05-system-overview-architecture | 4 | FusionANNS | `6-9` | `04-fusionanns.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 05-system-overview-architecture | 5 | Starling | `7` | `05-starling.pdf` | Pass: keeps only the framework overview page, not the later data-layout section. |
| 06-method-core-design | 1 | Starling | `6-15` | `01-starling.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 06-method-core-design | 2 | WARP | `3-6` | `02-warp.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 06-method-core-design | 3 | SPFresh | `5-10` | `03-spfresh.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 06-method-core-design | 4 | OdinANN | `5-9` | `04-odinann.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 06-method-core-design | 5 | Integrating Vector DBs | `10-18` | `05-integrating-vector-dbs.pdf` | Pass: stops at the page where Section 7 opens, not the following experiment pages. |
| 07-optimization-execution-layer | 1 | PQ Fast Scan | `1-5` | `01-pq-fast-scan.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 07-optimization-execution-layer | 2 | WARP | `3-6` | `02-warp.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 07-optimization-execution-layer | 3 | Chameleon | `4-6` | `03-chameleon.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 07-optimization-execution-layer | 4 | Milvus | `4-6` | `04-milvus.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 07-optimization-execution-layer | 5 | Flash Graph Indexing | `4-9` | `05-flash-graph-indexing.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 08-implementation | 1 | SPFresh | `7-10` | `01-spfresh.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 08-implementation | 2 | Chameleon | `6` | `02-chameleon.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 08-implementation | 3 | OdinANN | `5-9` | `03-odinann.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 08-implementation | 4 | GustANN | `8-15` | `04-gustann.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 08-implementation | 5 | Milvus | `3-8` | `05-milvus.pdf` | Pass: trimmed the page that carried Applications content; the excerpt now stops before that unrelated section. |
| 09-evaluation | 1 | SPFresh | `10-14` | `01-spfresh.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 09-evaluation | 2 | OdinANN | `9-14` | `02-odinann.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 09-evaluation | 3 | WARP | `6-8` | `03-warp.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 09-evaluation | 4 | Starling | `15-23` | `04-starling.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 09-evaluation | 5 | Chameleon | `6-8` | `05-chameleon.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 10-related-work | 1 | VBASE | `15` | `01-vbase.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 10-related-work | 2 | Chameleon | `8` | `02-chameleon.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 10-related-work | 3 | OdinANN | `14` | `03-odinann.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 10-related-work | 4 | GustANN | `23-24` | `04-gustann.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 10-related-work | 5 | WARP | `2` | `05-warp.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 11-discussion-conclusion | 1 | Starling | `23-24` | `01-starling.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 11-discussion-conclusion | 2 | GustANN | `14-15, 24` | `02-gustann.pdf` | Pass: page range is intentionally non-contiguous to preserve discussion plus conclusion without carrying unrelated middle sections. |
| 11-discussion-conclusion | 3 | Chameleon | `8` | `03-chameleon.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
| 11-discussion-conclusion | 4 | OdinANN | `8-9, 14` | `04-odinann.pdf` | Pass: page range is intentionally non-contiguous to preserve discussion plus conclusion without carrying unrelated middle sections. |
| 11-discussion-conclusion | 5 | WARP | `8` | `05-warp.pdf` | Pass: page range is limited to the designated section boundary; any adjacent text is from a shared physical page. |
