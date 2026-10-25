# Context and memory anti-patterns

| Anti-pattern | Observable failure | Correction |
|---|---|---|
| Whole-repository injection | Unrelated files displace the active constraint. | Load a small map and retrieve relevant symbols. |
| Cache-first bloat | High cache-hit rate but repeated mistakes and long prompts. | Remove irrelevant core content and evaluate task quality. |
| Memory as policy | A retrieved note instructs the agent to reveal secrets. | Keep trust labels; enforce policy outside writable memory. |
| Fact without provenance | Conflicting records cannot be dated or attributed. | Require source, time, owner and supersession. |
| Retention without scope | Another user's preference appears in the answer. | Enforce tenant-aware authorization in storage and retrieval. |
| Transcript as core memory | Every old event is replayed on every task. | Separate bounded facts from searchable episodes. |
| Endless session | Repeated compaction costs grow and facts remain stale. | End at task boundaries with a recoverable handoff. |
| Summary as evidence | A claim survives although its original source contradicts it. | Reopen raw artifacts for consequential decisions. |
| Omitted failure | Agent repeats the same unsuccessful command. | Preserve the causal error and attempted remedy. |
| Unverified write | Agent says “remembered” without a write receipt. | Inspect the actual tool call, staged status and live store. |
| Retrieval miss as deletion | A fact remains in indexes or backups. | Test the declared deletion/retention path explicitly. |
| Shared scratchpad flood | Workers pay for each other's irrelevant exploration. | Share accepted decisions and evidence pointers only. |
| Autonomous policy learning | Agent broadens its permissions after a successful task. | Stage proposals; protect scope and verifier configuration. |

Treat stale memory as a correctness issue and poisoned memory as a security issue. Escalate suspected secret exposure or cross-user retrieval before continuing.
