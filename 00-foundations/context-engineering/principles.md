# Context rules with evidence

Use the smallest sufficient context for the next action. Anthropic describes finite attention and degraded retrieval as context grows. This does not justify removing evidence needed for correctness.

| Rule | Implementation | Evidence | Caveat / check |
|---|---|---|---|
| Keep stable instructions separate from task evidence | Prefix contains role, policy, approved tools, and concise project constraints. Put retrieved text in labeled data blocks. | Anthropic context engineering; Codex loop | Delimiters do not enforce trust. Test an injected document. |
| Retrieve by pointer | Keep source IDs, paths, and query handles. Open the relevant span before using it. | Anthropic context engineering | Files that are never retrieved do not supply memory. Test a fact outside the initial context. |
| Preserve a deterministic prefix | Keep tool ordering stable. Avoid changing timestamps in static instructions. | Manus; Codex loop | Cache efficiency does not establish relevance. Measure both selection accuracy and cache use. |
| Return bounded tool results | Support filters and paging. Return reusable IDs and actionable errors. | Anthropic writing tools | Do not truncate away the evidence needed to diagnose failure. |
| Preserve failed approaches | Record the failed action, causal error, changed assumption, and next check. Keep raw logs on disk. | Manus | Remove repetitive noise, not negative evidence. |
| Compact operational state | Save objective, decisions, completed checks, failures, pending approvals, and artifact paths before restarting. | Anthropic context engineering; HumanLayer | Summaries can be wrong. Reopen originals for consequential claims. |
| Isolate worker scratchpads | Give workers bounded questions and shared evidence pointers. Collect findings with source locations. | Anthropic multi-agent research; Cognition | Isolation must not fragment shared decisions. |
| Review research before implementation | Approve the map of relevant files and constraints, then approve the plan for coupled changes. | HumanLayer practitioner account | Its reported successes are not controlled comparative results. |
| Separate durable facts from observations | Store accepted preferences and decisions apart from scraped text and temporary traces. | Hermes; OpenClaw memory | A memory write needs provenance, scope, approval status, and deletion policy. |
| Refresh at task boundaries | Save a handoff and start a new session after an independently verified increment. | Hermes frozen session snapshot; HumanLayer | Exact session behavior depends on the harness. |

## Handoff contract

Record the task version, remaining budget, active branch, changed paths, accepted decisions, failed attempts, raw evidence paths, exact checks and results, pending approvals, and next action. Distinguish “proposed” from “executed.” A fresh agent must be able to verify these statements without the previous conversation.

HumanLayer's suggested 40-60% context utilization is a practitioner heuristic. It is not a model limit or an automatic compaction trigger. Choose a local threshold from failure traces, output reserves, and measured recovery quality.

Sources: [source registry](../sources.md), especially Anthropic, Manus, Cognition, HumanLayer, and the Codex loop. Snapshot 2026-10-25.
