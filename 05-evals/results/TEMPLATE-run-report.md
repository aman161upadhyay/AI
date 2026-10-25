# Run report: <yyyy-mm-dd>-<agent>-<run-id>

Copy this file, fill every field, and never overwrite an earlier run. Fields marked (grader) stay out of the candidate agent's context.

| Field | Value |
|---|---|
| Run ID | |
| Date and time (UTC) | |
| Operator | |
| Baseline run ID (if a comparison) | |
| Execution mode | manual paste / SDK script / Inspect task |
| Cases | case IDs and file hashes, one line each |
| Agent revision | commit or file hash of SYSTEM-PROMPT.md and each loaded skill |
| Model and settings | model snapshot, temperature, reasoning effort, max tokens |
| Tool permissions | allow list, deny list, sandbox or environment image |
| Grader (grader) | model or person; rubric version |
| Limits | approved token and cost cap; actual tokens, cost, elapsed time, retries |

## Per-criterion results

| Case | Criterion | PASS / FAIL / UNKNOWN | Evidence (quote or file reference) |
|---|---|---|---|
| | | | |

## Trial outcome

One of PASS, FAIL, UNKNOWN, INFRA_ERROR, BUDGET_EXCEEDED per case, with one sentence of reason.

## What changed against the baseline

Deltas, failure slices, and the recommendation: keep, revise, or roll back the prompt or skill.

## Where the traces are

Redacted trace location. Private traces stay outside Git.
