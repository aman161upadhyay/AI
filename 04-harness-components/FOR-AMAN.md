# Aman, how to use the harness components

These folders are for the moments when you are building or changing the machinery rather than prompting an agent. Three situations come up repeatedly.

## You are wiring a new agent

Read, in this order: `memory-and-context/context-engineering-principles.md` (decide what the agent always sees and what it retrieves), `tool-design/tool-description-template.md` (write every tool description against it before writing code), `security-guardrails/guardrail-config-examples.md` (copy the closest configuration and tighten it), and `evals-framework/how-to-write-evals.md` (write five cases before the first run). Budget half a day for the four; the agents in `03-agents/` already did this work for their own cases, so start from the nearest one.

Give the implementing agent (usually the coding agent) these folders as read-only context, not the whole repository. Point it at the specific files above.

## An agent is misbehaving

Match the symptom to the folder. Forgetting instructions mid-task, repeating itself, or confidently using stale facts: `memory-and-context/anti-patterns.md`. Choosing the wrong tool or calling the right one with the wrong arguments: `tool-design/writing-tools-for-agents.md`, section on descriptions and selection evals. Doing something it should not have been able to do: `security-guardrails/principles.md`, and treat it as a guardrail bug, never as a prompt bug. Getting worse after a prompt change: `evals-framework/regression-tracking.md`.

## You want numbers instead of impressions

`evals-framework/eval-case-schema.md` is the schema every `03-agents/*/evals/*.yaml` file follows. `runners.md` explains how to run them with Inspect and what to log. Record results in `05-evals/results/` using the format there, with the model, the date, and the prompt version. Do not compare runs across different models or prompt versions without saying so in the record.

## Access and guardrails

Nothing in these folders needs credentials to read. When you implement a guardrail configuration, test it with the method in `security-guardrails/testing-guardrails.md` before trusting it: a guardrail that has never been attacked is a guess. Keep policy enforcement outside the model (sandbox, proxy, permission layer); a sentence in the system prompt is a request, not a control.
