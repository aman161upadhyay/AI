# Diagnose context and control failures

Choose an intervention from an observed symptom. Adding another paragraph to the system prompt does not fix a missing permission boundary.

| Failure | Observable symptom | Mitigation | Acceptance check |
|---|---|---|---|
| Context rot | Earlier constraints vanish or distractors dominate | Retrieve targeted spans; rebuild a bounded task context; retain original artifact pointers | Add irrelevant documents and test retention of a critical constraint |
| Tool sprawl | Wrong tool choice or duplicate operations | Remove overlap; use task-level tools; discover relevant groups | Evaluate tool choice on near-miss tasks |
| Runaway loop | Same error repeats without measured progress | External call/time/spend limits; record attempt count; escalate without new evidence | Force a deterministic failure and verify termination |
| Cost blowup | Broad fan-out, repeated huge prompts, frequent compaction | Shared global budget; stable prefix; deliberate task boundaries | Report total worker and lead cost, not only final-call cost |
| False completion | Claimed save/test has no receipt | Inspect persisted files; use independent acceptance checks | A missing receipt must produce “unverified,” not success |
| Memory poisoning | Retrieved instructions become policy | Label trust; quarantine candidate facts; review durable mutations | An injected page must not change tools or approved domains |
| Compaction loss | Next session repeats failed work or drops approval | Save causal failures and pending authorization explicitly | Resume from a clean session with no conversation |
| Parallel conflict | Incompatible schemas or assumptions | Shared decision record; serialized integration | Reject worker output that contradicts an accepted decision |
| Duplicate side effect | Retry repeats a payment or publication | Durable receipt and idempotency key; reconcile uncertain outcomes | Simulate timeout after remote success |
| Evaluator gaming | Acceptance rules weaken during repair | Separate evaluator write access and held-out cases | Agent cannot modify its own hidden tests |

Suggested initial no-progress rule: stop after two unsuccessful attempts at the same step unless the next attempt has new evidence or a changed approach. This is a repository recommendation, not a vendor default.

Evidence: Anthropic effective agents/context/tools/research; Manus; Hermes memory; OpenClaw security; LangGraph persistence. See [sources](../sources.md). No local runtime evaluation has certified these mitigations.
