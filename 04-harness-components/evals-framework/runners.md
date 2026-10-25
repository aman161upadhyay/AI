# Runner selection and execution contract

Use [Inspect](https://inspect.aisi.org.uk/) as the canonical runner for tool-using agents. This is a design choice, not a claim that an adapter has been installed or tested.

## Inspect adapter contract

Map `id` to sample identity, `task` plus public `inputs` to the input messages, and grader-only `gold` to the target or protected scorer context. Preserve source and case hash in metadata. The solver invokes the existing agent entrypoint under its actual tools and permissions; it must not replace an agent test with a plain completion.

The scorer reads final artifacts and tool effects before semantic judgment. Keep hidden tests and labels outside solver-readable paths. Reset the sandbox before every trial. Preserve raw outcomes PASS, FAIL, UNKNOWN, INFRA_ERROR and BUDGET_EXCEEDED. Inspect's native score representation can wrap these outcomes; do not silently map unknowns to success.

Before an adapter is accepted, verify one known pass, one known failure, one tool error and one budget stop. Pin the runner package and environment. Record its exact invocation in the run report after checking installed help. No command here claims to run nonexistent adapter files.

## Manual run now

1. Freeze the selected case files and agent prompt.
2. Start a clean session for each trial with only task and inputs.
3. Apply approved limits outside the model. Capture transcript and final artifacts.
4. Give the grader output plus gold, rubric and anti-patterns in a separate session.
5. Save per-criterion outcomes and evidence under `05-evals/results/`.

## Optional tools

| Tool | Use | Boundary |
|---|---|---|
| [promptfoo](https://www.promptfoo.dev/docs/intro/) | Quick provider/prompt matrices and authorized red-team comparisons. | Review telemetry and remote attack-generation settings; local CLI can still send prompts to providers. |
| [DeepEval](https://github.com/confident-ai/deepeval?tab=readme-ov-file) | Alternative primary runner when pytest-style application tests fit best. | Calibrate semantic metrics; do not maintain a second canonical score for the same run. |
| [Braintrust](https://www.braintrust.dev/docs/evaluate) | Optional datasets, experiments and human-review tracking. | SDK license does not establish hosted retention, access or data rights. |

OpenAI's [deprecation record](https://developers.openai.com/api/docs/deprecations), checked 2026-10-25, states that the Evals dashboard and API become read-only on 2026-10-31 and shut down on 2026-11-30. The notice was announced 2026-06-03. Do not adopt that hosted API as a new dependency. Export existing datasets/results and review its linked promptfoo migration. Recheck current status before migration.
