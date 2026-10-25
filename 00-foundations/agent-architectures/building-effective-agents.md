# Start with a workflow when the steps are known

A workflow uses predefined code paths to arrange model calls and tools. An agent dynamically chooses its process and tool use. Anthropic's distinction concerns control flow, not the number of model calls.

Try a single well-specified call with retrieval first. Add a workflow when separate stages improve reliability or verification. Use an agent when the required steps cannot be enumerated reliably beforehand and the environment supplies usable feedback.

| Pattern | Fit | Necessary control |
|---|---|---|
| Prompt chaining | Predictable dependent transformations | Validate the intermediate artifact before continuing |
| Routing | Distinct task classes need different tools or prompts | Test ambiguous and out-of-scope inputs |
| Parallelization by section | Independent parts of a result | Bound fan-out and reject overlapping scopes |
| Parallelization by vote | Independent attempts can be adjudicated | Use an external oracle; agreement is not proof |
| Orchestrator-workers | Subtasks depend on discoveries | Give each worker a contract and integrate centrally |
| Evaluator-optimizer | Explicit criteria yield actionable feedback | Cap revisions and keep evaluator criteria fixed |
| Autonomous tool loop | Uncertain path with observable feedback | External permission, budget, and no-progress checks |

Design the agent-computer interface as carefully as the prompt. Tool schemas need explicit inputs, useful identifiers, concise observations, and recoverable errors. Test tool selection against realistic tasks instead of assuming that endpoint coverage equals usefulness.

Stop on verified success, cancellation, exhausted budget, missing authorization, or unrecoverable failure. A completion message is a proposal that still needs verification.

Evidence: Anthropic [Building effective agents](https://www.anthropic.com/engineering/building-effective-agents), December 2024 with living revision; [Writing effective tools](https://www.anthropic.com/engineering/writing-tools-for-agents), 2025-09-11. First-party architectural guidance, not a guarantee for every domain.
