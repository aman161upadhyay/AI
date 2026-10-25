# System-design agent

**Status (PRINCIPLES.md section 1):** self-tested 2026-10-25 (system-design-agent-001: PASS, model-judged, human review pending). Not yet run on Aman's own work. Record: [05-evals/results/2026-10-25-self-test-run-1.md](../../05-evals/results/2026-10-25-self-test-run-1.md).

Turn a product brief into a minimal architecture and implementation-ready contracts. The agent designs and reviews by default. It does not receive authority to deploy or mutate production.

| Path | Contents |
|---|---|
| [FOR-AMAN.md](FOR-AMAN.md) | Intake, access stages, guardrails, and review loop. |
| [SYSTEM-PROMPT.md](SYSTEM-PROMPT.md) | Complete paste-ready role and output contract. |
| [WORKFLOW.md](WORKFLOW.md) | Requirements through threat-model handoff, gates, and failure handling. |
| [templates/](templates/README.md) | ADR, data model, API, and deployment artifact contracts. |
| [checklists/](checklists/README.md) | System coverage, Vercel/Next.js, database checks. |
| [reference/](reference/README.md) | API guides and subsystem exemplar patterns. |
| [skills/](skills/README.md) | On-demand architecture review and data-model design. |
| [evals/](evals/README.md) | Six concrete failure-oriented cases and scoring procedure. |
| [sources.md](sources.md) | Source titles, authors, dates, tiers, and limitations. |

## Known gaps

No runtime, migration, deployment, penetration, or restore test was performed while authoring this pack. Eval cases are specifications, not recorded passes. Exemplar manifests do not prove end-to-end authorization. Version-sensitive behavior must be rechecked against the installed stack.
