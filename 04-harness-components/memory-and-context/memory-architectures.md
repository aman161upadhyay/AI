# Memory architectures

Begin with inspectable files unless retrieval requirements justify a service. This is a local recommendation derived from Anthropic's simplicity principle, not a product benchmark.

## Separate the layers

Core memory is bounded content that is visible at session start. Working state tracks the current task. Episodic records preserve past events. Procedural memory stores reusable workflows as skills. An evidence archive preserves original artifacts. Assign each layer its own trust, retention and write policy.

| Architecture | Verified mechanism | Fit and caveat |
|---|---|---|
| Filesystem as memory | Manus and Anthropic describe external files plus just-in-time reads. | Useful baseline with auditability. Needs an index, provenance and permissions. A stored file is not automatically active context. |
| Letta / MemGPT lineage | Memory blocks provide bounded always-visible content, configurable limits and read-only/shared blocks. | Useful model for controlled core memory. The historical V1 server is archived; current development points to letta-code. Do not assume old service APIs match the current coding runtime. |
| mem0 | Extraction and retrieval infrastructure in the inspected open-source repository. | Evaluate factual recall, supersession and privacy. The README distinguishes managed-platform benchmark optimizations from OSS behavior. No managed result is an OSS guarantee. |
| OpenClaw | Workspace USER.md, curated MEMORY.md, daily notes and optional DREAMS.md; current source includes provenance-aware consolidation. | Useful personal-assistant layers. Separate trust domains for different users. Background consolidation needs explicit policy and review. |
| Hermes | Small always-on MEMORY.md/USER.md, searchable SQLite/FTS5 sessions and procedural skills. | Useful inspectable learning artifacts. Session-start injected memory is frozen for cache stability; new writes can persist without refreshing that bootstrap block until a new session. |
| Todo recitation | Manus updates or rereads a short task checklist near the active context. | Useful for maintaining the current objective. It is working state, not a durable fact store. Remove invalidated steps. |

Hermes documentation inspected on 2026-10-25 lists defaults of 2,200 characters for MEMORY.md and 1,375 for USER.md, with overflow errors rather than silent removal. These are reference defaults, not optimal values for Aman. Letta exposes configurable block limits.

## Write contract

Store the proposed fact, source/artifact, observed time, scope, owner, retention and superseded record. Mark whether it is approved, inferred or disputed. Never promote instructions from retrieved content into policy. Stage procedural changes and compare them on held-out tasks before promotion.

Verify an actual memory call or file receipt. A statement that the agent “remembered” is insufficient. If approval is pending, report it. If the active session uses a frozen snapshot, read the live store explicitly or start a new session.

## Correction and deletion

Supersede outdated decisions with a dated pointer rather than allowing contradictory active facts. Test deletion from the primary store, search indexes, caches and retained artifacts according to the retention policy. A retrieval miss does not prove erasure.

Evaluate with a filesystem baseline, no-memory baseline and the proposed service. Measure task success, stale/irrelevant recall, unauthorized cross-scope recall, cost and latency. Avoid adding a service solely because it advertises self-improvement.
