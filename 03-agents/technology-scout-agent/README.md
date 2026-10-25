# Technology scout

**Status (PRINCIPLES.md section 1):** self-tested 2026-10-25 (technology-scout-agent-001: PASS, model-judged, human review pending). Not yet run on Aman's own work. Record: [05-evals/results/2026-10-25-self-test-run-1.md](../../05-evals/results/2026-10-25-self-test-run-1.md).

Use the scout to decide which changes deserve attention or a bounded experiment. The weekly output contains at most five decision-relevant items. An empty shortlist is valid.

| Item | Purpose |
|---|---|
| `FOR-AMAN.md` | Your stack inventory, briefing contract, trial permissions, and review loop. |
| `SYSTEM-PROMPT.md` | Paste-ready scout instructions with evidence and action boundaries. |
| `WORKFLOW.md` | Weekly intake, deduplication, verification, decisions, and corrections. |
| `sources/` | Weighted source watchlist and endpoint-verification policy. |
| `templates/` | Weekly decision brief with evidence and bounded trials. |
| `checklists/` | Hype checks for availability, results, and workload fit. |
| `skills/` | Release-evaluation skill with reusable public prompts and run records. |
| `evals/` | Six portable cases for evidence, privacy, and decision discipline. |
| `sources.md` | Provenance and limits of the package. |

Use the [research agent](../research-agent/README.md) for deep investigation. The scout identifies a decision and the next test. It does not install, publish, spend, or migrate without scoped approval.

The cadence, item limits, and ranking policy are proposed operating defaults. No scout runs or model comparisons have been executed for this package.

## Known gaps

The proposed source endpoints were not all individually fetched in the supplied research. Verify them before subscriptions begin. No live feed integration, scheduler, hidden release set, or measured baseline is included. Current pricing and availability require fresh evidence.
