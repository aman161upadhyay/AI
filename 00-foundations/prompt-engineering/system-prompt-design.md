# Structure a production system prompt around actual actions

Write an original prompt for the available tools and authorization model. Production reference prompts are useful for inspection, not as a permission grant or a default template.

Use [02-prompts/system-prompts-of-production-tools](../../02-prompts/system-prompts-of-production-tools/README.md) for the reference index. The collection of leaked prompts is not authenticated current production behavior. Anthropic's official releases are authentic app snapshots, but no blanket permissive redistribution grant was established.

| Section | Required content | Failure to prevent |
|---|---|---|
| Responsibility and stance | Audience, deliverable, scope, honest uncertainty | Invented expertise or irrelevant persona |
| Environment | Actual tools, paths, user-visible surfaces, runtime limits | Imagined APIs or files |
| Input contract | Required evidence, missing-input questions, trust labels | Acting on absent requirements |
| Operating procedure | Inspect, plan when needed, perform bounded work, verify | Endless exploration or premature edits |
| Tool contracts | Selection rule, arguments, errors, receipts, side effects | Wrong operations and false completion |
| Permissions | Reads allowed, actions requiring approval, refusals | Treating task intent as production authorization |
| Output contract | Artifact schema, evidence, blocked checks, handoff | Unusable prose or omitted failures |
| Termination | Success checks, budget stop, no-progress escalation | Runaway retries |

Keep action modes explicit: explain, propose, implement, and publish have different permissions. Parallelize independent reads, not state-dependent writes. Make communication short enough that it does not replace verification.

Put hard controls in the controller and tool dispatcher. Do not rely on system-prompt prose to enforce spend, tenant access, egress, or credential scope.

Test missing inputs, tool failures, injected documents, unauthorized actions, and false-completion traps before promotion. Version the prompt and retain a rollback candidate.

Evidence: official Claude prompt release index, provider prompting guidance, and context engineering in [sources](../sources.md). Observed reference themes are design hypotheses, not comparative effectiveness results.
