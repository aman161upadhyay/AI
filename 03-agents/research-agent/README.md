# Research agent

**Status (PRINCIPLES.md section 1):** self-tested 2026-10-25 (research-agent-001: FAIL on matched budgets in run 1, PASS on the same-day re-run after the prompt fix; model-judged, human review pending). Not yet run on Aman's own work. Record: [05-evals/results/2026-10-25-self-test-run-1.md](../../05-evals/results/2026-10-25-self-test-run-1.md).

Use this agent to answer a question or support a decision with inspectable evidence. Start with one researcher. Add workers only for independent questions.

| Item | Purpose |
|---|---|
| `FOR-AMAN.md` | Request framing, access grants, spending controls, and review loop. |
| `SYSTEM-PROMPT.md` | Paste-ready instructions for the lead researcher. |
| `WORKFLOW.md` | Research phases, effort tiers, stop rules, and failure handling. |
| `skills/` | Source assessment, citation checks, decomposition, durable notes, and literature review. |
| `checklists/` | Final acceptance checks and origin-aware triangulation. |
| `reference/` | Architecture comparisons, benchmark limits, and methods from human research. |
| `evals/` | Eight portable cases and a protocol for grading evidence and behavior. |
| `sources.md` | Claim-relative provenance for this package. |

Load the system prompt first. Load only the skills that the request needs. Write run artifacts into a separate authorized workspace, not into this package.

The prompts, budgets, credibility scores, and acceptance thresholds are proposed harness policy. They have not been validated by agent runs. No upstream code or source-page archive is redistributed here.

## Known gaps

No head-to-head product evaluation was performed. STORM and dzhng are research references that failed the six-month maintenance gate at the 2026-10-25 snapshot. Source endpoints and API capabilities need a fresh check before integration. The eval cases are public development cases, not a hidden release set.
