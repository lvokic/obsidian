# Learnings

Corrections, insights, and knowledge gaps captured during development.

**Categories**: correction | insight | knowledge_gap | best_practice

---
## [LRN-20260601-001] correction

**Logged**: 2026-06-01T12:32:40+08:00
**Priority**: high
**Status**: pending
**Area**: docs

### Summary
When cropping research-paper section PDFs, use boundary pages rather than estimated body pages.

### Details
I initially generated ANNS section excerpt PDFs using manually estimated page ranges. The user corrected that this cut off incomplete introductions in `wiki/analyses/anns-section-writing-exemplars/top4-section-excerpts/02-introduction`. For two-column papers, a section tail often shares the same physical page as the next chapter heading, so the correct excerpt range is from the target section's heading page through the next chapter/subsection heading page.

### Suggested Action
For future PDF excerpt folders, define and document the cropping rule before generation: `start_page = physical page containing target section heading`; `end_page = physical page containing next chapter/subsection heading`. Verify at least one sample per folder by searching extracted text for both the target heading and the next heading.

### Metadata
- Source: user_feedback
- Related Files: wiki/analyses/anns-section-writing-exemplars/top4-section-excerpts/
- Tags: pdf, excerpts, research-wiki, section-boundaries

---

## [LRN-20260408-001] correction

**Logged**: 2026-04-08T19:20:00+08:00
**Priority**: medium
**Status**: pending
**Area**: docs

### Summary
Do not use external-paper reproduction docs as evidence when reviewing the user's own CXL-HNSW project document.

### Details
I incorrectly cited `CXL_ANNS_REPRODUCTION.md` to challenge the maturity of a baseline in `raw/CXL_HNSW_CODE_ARCHITECTURE_ANALYSIS copy.md`. The user clarified that this reproduction doc belongs to another paper's reproduction track, while the current project framing is already captured in the vault knowledge graph. For project review, evidence should be restricted to the project's own knowledge-graph pages and the relevant implementation path.

### Suggested Action
When reviewing thesis/project documents in this vault, separate three evidence classes explicitly: current project docs in the knowledge graph, current implementation, and external reproduction/material for other papers. Do not mix them unless the user asks for cross-project comparison.

### Metadata
- Source: user_feedback
- Related Files: raw/CXL_HNSW_CODE_ARCHITECTURE_ANALYSIS copy.md, wiki/overview/cxl-vector-project-overview.md, wiki/analyses/cxl-vector-thesis-positioning.md
- Tags: review-scope, evidence-boundary, thesis

---
## [LRN-20260601-001] correction

**Logged**: 2026-06-01T20:22:00+08:00
**Priority**: medium
**Status**: pending
**Area**: docs

### Summary
For ANNS section excerpt packages, do not include ranked candidates beyond the requested Top N.

### Details
The user corrected the Background & Motivation excerpt work: the package should collect only the Top 5 examples and the directory name should match `top5-section-excerpts`, not keep an old `top4-section-excerpts` name or include extra rank-6/rank-7 examples.

### Suggested Action
When generating exemplar folders from a ranked card, enforce the requested cutoff in both generated artifacts and navigation metadata. If the folder name encodes a rank cutoff, rename it rather than preserving a stale compatibility path.

### Metadata
- Source: user_feedback
- Related Files: wiki/analyses/anns-section-writing-exemplars/top5-section-excerpts/, wiki/analyses/anns-section-writing-exemplars/agent-writing-map/03-background-cards.md
- Tags: obsidian, paper-writing, excerpt-boundaries, top-n

---
## [LRN-20260508-001] correction

**Logged**: 2026-05-08T11:52:27+08:00
**Priority**: medium
**Status**: pending
**Area**: docs

### Summary
When maintaining the Obsidian wiki, stale pages and broken local references must be removed from the graph after sources or project direction changes.

### Details
The user pointed out that CXL-Vector content should be removed before a full rewrite, and that stale relationships such as TurboQuant figure links can remain visible even when the referenced files are no longer in the repository.

### Suggested Action
For wiki maintenance/refactor tasks, run both a CXL/topic mention audit and a local-reference existence audit across markdown links, image links, and YAML `sources` paths before finalizing.

### Metadata
- Source: user_feedback
- Related Files: index.md, wiki/
- Tags: obsidian, wiki-maintenance, stale-links

---
