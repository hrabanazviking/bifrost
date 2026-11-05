# Bifrǫst Bridge: Optional Second Brain Provider

**Date:** 2026-11-04  
**Repository:** `hrabanazviking/bifrost`  
**Implementation status:** Roadmap only; no application code modified.

## Relationship to the master roadmap

- **Canonical roadmap:** https://github.com/hrabanazviking/bifrost-viewer/blob/main/docs/roadmaps/BIFROST_SECOND_BRAIN_MASTER_EXPANSION_ROADMAP_2026-11-04.md
- **Local full copy:** [BIFROST_SECOND_BRAIN_MASTER_EXPANSION_ROADMAP_2026-11-04.md](BIFROST_SECOND_BRAIN_MASTER_EXPANSION_ROADMAP_2026-11-04.md)
- **Status:** Proposed work, not existing functionality. Confirm actual current installed state and protect existing data before writing code.
- **Ownership:** Bifröst Viewer coordinates the Second Brain. Skein and Skry own their APIs. Integrations must use documented, authenticated contracts and cannot assume direct PostgreSQL access.
- **Security:** Public Markdown only. No actual keys, OAuth client secrets, vault values, database passwords, user documents, personal account identifiers, logs, private state paths or private URLs.
- **Compatibility:** Preserve existing code behavior, published interfaces, licenses and attribution. Changes should be opt-in, reversible and regression-tested.

## Goal

Connect the existing Mímir/Huginn/Muninn composite agent-memory bridge to Bifröst Viewer's authorized document intelligence API without confusing the two distinct projects.

## Repository-specific engineering responsibilities

1. **Naming boundary:** This repository is `bifrost`, the composite provider built around SQLite FTS5, Qdrant and associative memory. `bifrost-viewer` is a **different** project using PostgreSQL/pgvector, Skein and Skry.
2. Add a separate optional provider adapter that calls Bifröst Viewer's versioned HTTP or MCP read/search endpoints.
3. Normalize results across memory backends, preserving origin, retrieval score, evidence IDs, source age and access scope.
4. Do not silently import user chat history into the shared document corpus or double-count duplicate memories.
5. Keep existing Mímir/Huginn/Muninn operation fully functional without a Bifröst Viewer server.
6. Expose per-backend health and relevance in diagnostics, without projecting inferred entity relations as verified facts.
7. Never connect directly to the viewer's PostgreSQL owner role or ingest private credentials.

## Engineering and security gates

- [ ] Independent fallback when Bifröst Viewer is offline.
- [ ] User knows which backend each retrieved fact came from.
- [ ] No cross-memory export or privilege escalation without authorization.

## Delivery sequence

1. Read this repository's own architectural rules, domain boundaries and current source before editing.
2. Audit installed and unpublished development work; never assume a feature is absent simply because it is missing from the current public default branch.
3. Design a versioned optional integration through published API contracts; preserve baseline behavior.
4. Implement synthetic fixtures, unit tests, integration tests, timeouts and permission checks.
5. Test disconnection, false/stale results, recovery and security canaries.
6. Document capability level and deployment directions without secrets; require owner approval before live rollout.

**Canonical authority:** The primary Bifröst Viewer roadmap above resolves conflicts; individual source code and verified deployed evidence establish what is actually implemented.

