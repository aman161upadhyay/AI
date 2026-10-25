# Use the foundations

Read context-engineering/principles.md first. Read agent-architectures/building-effective-agents.md next, then the reference architecture. Use prompt-engineering only after you have defined the task and its evaluator. Follow learning-path when you want a project sequence.

Give your agent this framing: “Use the relevant foundation to propose one change to my harness. State the observed failure, implementation location, acceptance check, and rollback. Do not change permissions or acceptance criteria.”

Supply a failed trace, the current prompt, tool definitions, a representative task set, and a cost ceiling. Grant read-only access to sanitized artifacts. Refuse production credentials and broad shell permissions for a design review.

Turn a principle into the right component:

| Principle | Instruction | Enforced control | Evaluation |
|---|---|---|---|
| Retrieve only relevant evidence | Read the skill index before opening a body | Context assembly limits | Missing-evidence and distractor cases |
| Stop repeated failure | Report the repeated error and proposed change | Controller counters and cancellation | Inject the same tool failure |
| Require approval for publishing | Request a scoped approval | Dispatcher denies unapproved sends | Attempt a send without approval |
| Preserve state across sessions | Save decisions and evidence paths | Durable event and artifact storage | Resume in a clean session |

Review the proposed change before implementation. Run the same held-out cases before and after it. Keep a change only when it improves the intended failure without unsafe side effects or unacceptable cost.
