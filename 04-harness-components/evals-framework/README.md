# Portable eval framework

Keep cases independent of the execution framework. Inspect is the canonical runner recommendation for tool-using agents; this folder specifies the adapter contract without shipping executable adapters.

| File | Purpose |
|---|---|
| `FOR-AMAN.md` | Inputs, permissions and rollout decisions. |
| `how-to-write-evals.md` | Trace-led error analysis and binary acceptance criteria. |
| `eval-case-schema.md` | Canonical YAML fields and a complete case. |
| `runners.md` | Inspect mapping and optional framework choices. |
| `regression-tracking.md` | Baselines, versioned changes and release gates. |
| `llm-judge-setup.md` | Blinding, calibration and pairwise controls. |
| `sources.md` | Evidence behind this framework. |

Cases live in `03-agents/*/evals/`, one YAML file per case. Public cases are development material. Hidden gold, private traces and test credentials live outside the agent checkout. Sanitized run reports belong in `05-evals/results/`; actual release review belongs in `07-council/logs/`.

## Known gaps

No runner adapter, model account or labeled production corpus is included. Manual execution is available through the documented procedure. Automatic execution requires an inspected adapter and external budget enforcement; these documents do not pretend otherwise.
