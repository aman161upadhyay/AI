# Evaluation resources

Define failure classes before optimizing prompts or training weights. Use the repository's [eval framework](../../05-evals/README.md) for shared scoring and run records.

| Rank | Resource | As-of 2026-10-25 status | Why and limit |
|---|---|---|---|
| P1 | [Anthropic cookbook](https://github.com/anthropics/anthropic-cookbook) | Active first-party repository | `tool_evaluation`, `evals/agentic_search`; public alternative to paid study |
| P1 | [OpenAI cookbook](https://github.com/openai/openai-cookbook) | Active first-party repository | Eval examples and tool-use tasks; recheck model/API versions |
| P1 | [Writing effective tools](https://www.anthropic.com/engineering/writing-tools-for-agents), Anthropic, 2025-09-11 | Fetched first-party article | Trace-based failure analysis and held-out tool tests |
| P1 | [Skill output evaluation](https://agentskills.io/skill-creation/evaluating-skills) | Living first-party specification guidance | With/without skill comparison and reviewable evidence |
| P2 | [verifiers](https://github.com/PrimeIntellect-ai/verifiers) | Active first-party repository | Independent functional environment checks before RL |

Start with 50 cases as a project milestone, not a statistical sufficiency claim. Label a sample with a human. Calibrate an LLM judge against those labels. Keep deterministic safety gates separate from weighted quality scores.

Track task success, unsupported claims, tenant leaks, unauthorized effects, tool failures, tokens, and elapsed time. Use fixed versions and held-out splits. A training-set improvement or one successful run does not establish a stable gain.

## Pending: not yet inspected

These links are not admitted recommendations as of 2026-10-25.

- [AI Evals for Engineers & PMs](https://maven.com/parlance-labs/evals), Hamel Husain/Shreya Shankar: course existence and authors search-verified; substantive paid syllabus requires login and was not inspected.
- [Ragas paper](https://arxiv.org/abs/2309.15217): search-verified only; full paper not inspected. The repository's maintenance failure is recorded separately in [superseded.md](superseded.md).
