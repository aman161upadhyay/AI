# Eval index

Keep authored agent cases beside their agents and record run evidence here. Counts below are the inventory on 2026-10-25 after all nine agent folders were assembled (`find 03-agents -path '*/evals/*.yaml' | wc -l`). They count written cases, not completed trials.

## Authored portable sets

| Agent set | Cases currently present | Primary checks |
|---|---:|---|
| [Adversarial council](../03-agents/adversarial-council-agent/evals/README.md) | 8 | Seeded defects, clean controls, counterbalanced judging and calibration. |
| [Research](../03-agents/research-agent/evals/README.md) | 8 | Evidence, source support and scoped research behavior. |
| [Writing](../03-agents/writing-agent/evals/README.md) | 9 | Register, factual fidelity and publication boundaries. |
| [Design](../03-agents/design-agent/evals/README.md) | 6 | Task fit, access and evidence integrity. |
| [Security](../03-agents/security-agent/evals/README.md) | 10 | Authorized attack evidence, isolation and benign controls. |
| [Marketing](../03-agents/marketing-agent/evals/README.md) | 8 | Supported claims and approved campaign actions. |
| [Coding](../03-agents/coding-agent/evals/README.md) | 11 | Scoped change, executable acceptance check, permission boundaries, hook behaviour. |
| [System design](../03-agents/system-design-agent/evals/README.md) | 6 | Minimal architecture, contract completeness, no deployment authority. |
| [Technology scout](../03-agents/technology-scout-agent/evals/README.md) | 6 | Decision relevance, source grading, empty shortlist when nothing qualifies. |

These nine sets contain 72 YAML cases. Every case carries the eleven keys in `04-harness-components/evals-framework/eval-case-schema.md`; the lint in `07-council/tools/lint.py` checks the full schema (keys, quoted `as_of`, id and agent match, rubric shape, duplicate keys, JSON compatibility) and reports a major when PyYAML is missing instead of skipping silently. Ten cases have been executed once (2026-10-25, model-judged); see `results/2026-10-25-self-test-run-1.md`.

## Bundled upstream eval sets

Upstream schemas and licenses remain distinct from the authored YAML contract. Counts refer to scenario entries, not successful runs. Inspect scripts and fixtures before execution; do not automatically run vendored code.

| Set and location under `01-skills-library/` | Count | How to use |
|---|---:|---|
| `community/addyosmani__agent-skills/evals/cases/` | 34 behavioral entries in 25 JSON files | Follow that eval README's structural, routing and behavioral tiers. Structural/routing results do not prove behavioral quality. |
| `community/getsentry__skills/skills/skill-writer/evals/scenarios/` | 3 scenarios | Review its axis configuration and scenario expectations in an isolated approved environment. |

The following sets each live at `01-skills-library/community/coreyhaines31__marketingskills/skills/<skill>/evals/evals.json`. Follow the owning skill and supplied expectations; a human must review commercial claims and external-action boundaries.

| Skill | Cases | Skill | Cases |
|---|---:|---|---:|
| ab-testing | 8 | ads | 15 |
| ai-seo | 12 | analytics | 8 |
| attribution | 9 | content-strategy | 8 |
| conversion-tracking | 21 | copy-editing | 9 |
| copywriting | 10 | cro | 7 |
| customer-research | 13 | emails | 7 |
| launch | 9 | marketing-loops | 9 |
| product-marketing | 7 | seo-audit | 13 |
| social | 10 | | |

`01-skills-library/anthropic/claude-api/shared/evals/` contains four evaluation procedures and report tooling, not a case corpus. Do not count procedures as trial cases. Public benchmarks linked in `public-benchmarks-and-vibe-checks.md` are external reference slices and are not added to local-case totals.

## Run and record

1. Select case IDs and freeze the agent, evidence and grader revisions.
2. Follow [the manual or adapter procedure](../04-harness-components/evals-framework/runners.md). Inspect is the canonical runner recommendation; no authored adapter is shipped.
3. Give only task and inputs to the evaluated agent. Keep gold and labels in a separate grader context.
4. Preserve every trial and actual final state. Missing tools yield UNKNOWN or INFRA_ERROR, never PASS.
5. Record outcomes, evidence and actual cost using [results/README.md](results/README.md). Compare paired cases against a frozen baseline.

`FOR-AMAN.md` explains your decisions. `public-benchmarks-and-vibe-checks.md` links exact public examples and rights caveats. `results/2026-10-25-self-test-plan.md` defines the integrator's planned checks. `sources.md` records provenance.

## Known gaps

Self-test runs recorded in `results/` are the only executed trials; everything else in this index is a written case. Hidden validation labels, production traces and a runtime adapter are not included. Public development fixtures cannot establish held-out calibration.
