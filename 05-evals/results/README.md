# Eval run records

This folder stores sanitized evidence from actual runs. `2026-10-25-self-test-plan.md` is the plan; `2026-10-25-self-test-run-1.md` is the first executed run (ten cases, model-judged, artifacts in `run-1/`), with the two failures, the prompt fixes they caused and the re-runs. `TEMPLATE-run-report.md` is the blank report. `FOR-AMAN.md` explains your review role.

Use `yyyy-mm-dd-agent-run-id.md` for a report and optional same-ID JSON for structured results. Never overwrite an earlier run. Record:

- Run ID, timestamp, operator, baseline run ID and execution mode.
- Case IDs/hashes and trial index; include every selected case.
- Agent code/prompt/skill revisions, model snapshot and generation settings.
- Tool permissions, environment image/version, reset method and evidence packet hash.
- Grader implementation/model and rubric versions; human adjudicator when used.
- Approved limits and actual tokens, cost, elapsed time, retries and human review time.
- Per-criterion PASS/FAIL/UNKNOWN with evidence references.
- Trial outcome PASS, FAIL, UNKNOWN, INFRA_ERROR or BUDGET_EXCEEDED.
- Final artifact/state references and redacted trace location.
- Baseline deltas, failure slices, uncertainty and release recommendation.

Keep safety, functional success and subjective preference separate. For pairwise trials record both orders, mapped candidate IDs, ties and abstentions. Record false-pass/false-fail counts against human labels with denominators.

Private traces stay outside Git with access controls and retention dates. Public evidence must be sanitized and rights-cleared. Do not record raw secrets, real customer records or hidden release answers in this folder.
