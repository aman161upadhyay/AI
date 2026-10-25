# Load procedures only when relevant

Expose a skill's name and description first. Read its SKILL.md when the task matches. Read supporting files only for the current step. Anthropic and the Agent Skills specification describe this three-level disclosure.

## Choose the right component

| Need | Component |
|---|---|
| One task and its acceptance criteria | Task prompt |
| Stable repository commands and boundaries | Repository instructions such as AGENTS.md, with host-tested precedence |
| Reusable domain procedure | Skill |
| Typed authenticated operation | Tool or MCP server |
| Lifecycle automation | Hook, with separate platform enforcement |
| Separate context for independent work | Worker/agent definition |
| Installation bundle | Plugin or extension |

A skill teaches a procedure. It does not grant credentials or sandbox an operation.

## Portable authoring rules

1. Put case-sensitive `SKILL.md` in a directory whose name matches frontmatter `name`.
2. Use a name of 1 to 64 lowercase letters, digits, and hyphens. Do not use leading, trailing, or repeated hyphens.
3. Supply `description` of 1 to 1,024 characters. State capability and invocation conditions in third person. Include real task vocabulary and discriminating boundaries.
4. Apply host-specific restrictions separately. Anthropic's restrictions on XML tags and reserved names are not the entire portable schema.
5. Keep the body under about 500 lines. Prefer activation instructions under 5,000 tokens. These are guidance, unlike required metadata limits.
6. Add knowledge that the model needs: local procedures, exact checks, tool limitations, output contracts, and failure handling. Remove generic explanations.
7. Link references directly from SKILL.md. Add a contents list to a long reference file, especially above 100 lines.
8. Give one default approach and the condition that justifies an alternative.
9. Use precise sequences for brittle or risky transformations. Use judgment-oriented guidance for design trade-offs.
10. Put repeated deterministic transformations in reviewed scripts only when the runtime permits them. State inputs, dependencies, outputs, and error behavior.
11. Treat `allowed-tools` as experimental metadata. Enforce actual access in the harness. Optional `compatibility` is limited to 500 characters; `metadata` maps strings to strings.
12. Inspect nested licenses, scripts, network calls, deletion, and credential access before admission. Do not fetch and execute arbitrary dependencies during activation.

Description example: “Reviews tenant-aware SQL schemas and migrations. Use for a new data model or a change to tenant ownership, indexes, or deletion behavior. Does not run production migrations.”

## Author from observed failures

Write at least three scenarios before expanding the skill: a task that needs the missing behavior, an explicit invocation, and a near-miss that should not activate. Compare clean sessions with and without the skill. Record task outcomes, activation accuracy, latency, and tokens. Keep held-out cases and test intended model families.

Prefer an instruction for judgment and a reviewed script for repeated brittle work. OpenAI and Anthropic differ in emphasis on scripts; this selection rule is a local synthesis that requires measurement.

Evidence: [Agent Skills specification](https://agentskills.io/specification), [Anthropic authoring](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices), [skill evaluation](https://agentskills.io/skill-creation/evaluating-skills). Status: living docs observed 2026-10-25. See [source registry](../sources.md).
