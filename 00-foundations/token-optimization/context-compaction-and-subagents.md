# Context boundaries

Preserve operational state before reducing context. Anthropic's context-engineering article supports compaction, structured notes and subagent isolation. It does not give one universally correct compaction threshold.

## Handoff contract

Save the objective, acceptance criteria and non-goals. Record approved scope, pending approvals and budget remaining. Include baseline and current candidate identities, changed files, accepted decisions, failed approaches, unresolved errors, evidence paths and exact next command.

Keep full evidence outside the prompt under the task's access policy. Redact secrets. A summary must link to the original source for a disputed claim. After restart, inspect actual files and status rather than trusting the handoff alone.

Use fresh sessions between unrelated tasks. Compact within a task only when necessary or at a safe phase boundary. `/clear` discards context; `/compact` is lossy and has its own cost. HumanLayer's 40-60% working-context target is practitioner guidance. It is not a provider automatic trigger.

## Worker contract

Give each worker one bounded question, readable/writable paths, relevant evidence, forbidden actions, expected result schema, token share and deadline. Return conclusions, evidence pointers, unresolved issues and actual checks. Do not return the entire scratchpad.

Parallelize independent investigation or review. Serialize coupled interface decisions. For edits, assign disjoint paths or worktrees and test the integrated tree. A worker cap and global budget must include every child, compaction and retry.

Anthropic describes workers returning roughly 1,000-2,000-token summaries after larger exploration. This is an example of a context boundary, not a guaranteed compression ratio or a target for every task.

## Measure both costs

Compare parent input and total provider usage separately. A short parent summary can hide expensive child searches. Track repeated source reads across workers, duplicated questions and failed integration.

Use a single agent as the baseline. Add a worker only when it improves accepted-task quality or necessary latency enough to justify the extra cost. Never infer a coding benefit from a research-system benchmark.
