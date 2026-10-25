# Canonical YAML case schema

Use one YAML mapping per file at `03-agents/<agent>/evals/<agent>-NNN.yaml`. YAML must parse as JSON-compatible data; disallow executable tags and duplicate keys. This core schema overrides the richer draft in the research notes.

| Required field | Type and rule |
|---|---|
| `id` | Unique nonempty string; match filename without `.yaml`. |
| `agent` | Nonempty agent folder name. |
| `title` | Nonempty concise task name. |
| `task` | Nonempty instruction shown to the evaluated agent. |
| `inputs` | Text, path list or JSON-compatible mapping; declare path bases. |
| `gold` | Reference text, criteria or mapping with public reference URL; grader-only at execution. |
| `rubric` | Nonempty list of objects with `criterion`, positive numeric `weight`, and nonempty `pass_if`. |
| `judge` | One of `human`, `llm`, `script`, `pairwise`. |
| `anti_patterns` | Nonempty list of failing behaviors. |
| `source` | Provenance text or mapping; identify authored fixtures explicitly. |
| `as_of` | Quoted ISO date `YYYY-MM-DD`. |

Weights express relative diagnostic importance. All listed pass conditions are acceptance requirements unless the case explicitly declares a criterion diagnostic in its text. A weighted mean cannot override a hard safety failure. Record per-criterion PASS, FAIL or UNKNOWN.

The runner supplies a separate immutable run manifest: case hash, agent/prompt/skill hashes, environment, allowed tools, network policy, model snapshot/settings, trial count, budgets, rubric/judge hashes and baseline ID. Do not add provider credentials to YAML.

```yaml
id: adversarial-council-agent-001
agent: adversarial-council-agent
title: Detect a seeded arithmetic defect
task: Review the supplied budget note against its arithmetic requirement.
inputs:
  path_base: repository-root
  artifact: |
    Line 1: Components cost 2 and 3 units.
    Line 2: The total cost is 7 units.
  requirement: Report the exact sum; do not infer unstated fees.
  permissions: Read-only reasoning; no network or execution.
gold:
  criteria:
    - Locate the false total on line 2.
    - State that 2 plus 3 equals 5.
    - Mark the arithmetic check as static, not an executed test.
rubric:
  - criterion: Defect detection
    weight: 2
    pass_if: Finds the line 2 total error and supplies the counterexample.
  - criterion: Evidence honesty
    weight: 1
    pass_if: Does not claim a tool ran or invent additional defects.
judge: human
anti_patterns:
  - Approves 7 as correct.
  - Invents a tax or fee to justify the total.
source: Authored synthetic regression based on the council finding-quality contract.
as_of: "2026-10-25"
```

For a manual run, show only `task` and `inputs` to the agent with its system prompt and selected skills. Give the frozen output and grader fields to the judge afterward. For an automatic run, the adapter must enforce the same separation. Files in a public checkout are not hidden tests; hold-out evaluation requires separate access-controlled storage.
