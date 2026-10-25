# Repository self-test plan

Status: planned, not executed. The integrator runs these checks after all builders finish. No pass rate or model execution is claimed.

## Freeze and permissions

Freeze the complete repository tree and enumerate every `03-agents/*/evals/*.yaml` case. Reconcile counts with `../README.md`. Validate the common schema and local paths. Record all agent system-prompt and skill hashes.

Use fresh sessions, no production credentials and no write tools for documentation review. Case-specific execution requires an approved disposable sandbox. Keep gold and anti-patterns in the grader context, not the evaluated agent session. Set total dollars and wall time before paid calls; stop as INCONCLUSIVE if access or budget is missing.

## Required self-test matrix

| Agent | Cases | Judge and evidence |
|---|---|---|
| Adversarial council | `adversarial-council-agent-001` through `008`, all eight. | Human checks seeded defects, clean-control precision and static evidence. Coordinator runs two real orders for 007. |
| Writing | All YAML cases in `writing-agent/evals/`, across available registers. | Aman judges voice and facts; deterministic checks cover explicit length and forbidden output. |
| Design | All YAML cases in `design-agent/evals/`. | Browser/state checks when required, plus human accessibility and brief-fit review. Missing rendering is UNKNOWN, not an imagined pass. |
| Research | All YAML cases in `research-agent/evals/` present in the frozen tree. | Source-verifier persona plus human entailment audit; check citations against supplied evidence. |
| Coding | All YAML cases in `coding-agent/evals/` present in the frozen tree. | Independent script tests where an environment exists; human checks scope and honest reporting. |
| Security | All YAML cases in `security-agent/evals/` present in the frozen tree. | Independent authorized state checks and human security review; include benign controls. |
| System design | All YAML cases in `system-design-agent/evals/` present in the frozen tree. | Domain-expert review plus script checks where executable fixtures exist; inspect tenant and migration assumptions. |
| Marketing and technology scout | Every case in their agent eval folders present in the frozen tree. | Human claim/provenance checks under each case's rubric; do not invent external campaign results. |

The integrator must resolve any expected agent folder missing from the final inventory before declaring repository-wide coverage. Exact case IDs from the frozen manifest, not guessed IDs, determine execution.

## Trials and recording

Run one smoke trial per case first. Repeat the council set and changed-agent regression sets for three total trials when the approved budget permits. If only one trial is run, state that limit. Use human judges as the authoritative self-test labels; LLM judgments are secondary until calibrated.

Test the eval machinery with a seeded failure, clean artifact and missing-tool condition. Validate finding-schema examples and skill frontmatter. Check Markdown links and the writing lint. These static checks do not substitute for agent trials.

Save actual results in a new immutable run file using this folder's README. Include failed cases, missing prerequisites and actual costs. Run the independent repository council under `07-council/PROTOCOL.md`; commit its actual logs. Zero open blockers and majors plus the follow-up diminishing-return check are mandatory before push.
