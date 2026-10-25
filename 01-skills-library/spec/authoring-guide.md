# Write skills for decisions that recur

A skill is a directory with case-sensitive SKILL.md. Use a skill for a reusable domain procedure. Use a task prompt for one request. Use repository rules for stable commands and scope. Use a tool for authenticated operations and enforceable access. A plugin packages components but does not make them safe.

## Frontmatter

Required fields are `name` and `description`. A name has 1 to 64 lowercase letters, numbers or hyphens. It matches its directory and has no leading, trailing or consecutive hyphens. A description has 1 to 1,024 characters.
Optional shared fields are `license`, `compatibility`, `metadata` and experimental `allowed-tools`. Compatibility has at most 500 characters. Metadata maps strings to strings. Allowed tools is a space-delimited string; enforcement depends on the harness. Keep host-specific fields in adapters where possible.

Write descriptions in third person. Name the task and its invocation context. Distinguish near misses: landing-copy review differs from writing an email. Discovery sees the description before the procedure. Do not hide invocation conditions in the body.

## Disclosure and scripts

Load metadata for routing, the body after activation, and resources only when required. Keep SKILL.md below about 500 lines. Link long references directly from SKILL.md. Give references above 100 lines a table of contents. Put required tools and runtime limits in compatibility notes.

Use prose for judgement. Bundle deterministic code for brittle repeated transformations only after review. Document explicit inputs, errors and help output. Inspect network access, shell commands, deletion, credential use and remote execution. Do not download and run arbitrary remote code. Tool declarations do not replace sandbox permissions.

## Evaluate before expanding

Write at least three scenarios before filling the procedure. Include intended activation, explicit invocation and a near miss that should stay inactive. Add a missing-input case. State observable acceptance criteria.

Run clean sessions with and without the skill on identical inputs and tool budgets. Compare evidence-backed task correctness, unsafe actions, human preference, tokens and elapsed time. Repeat on intended models and preserve variance rather than choosing a single favorable run. Separate development cases from held-out tests.

Save model and harness versions, prompt, source commit, outputs and actual judge evidence. Use benchmark artifacts such as with_skill/, without_skill/, timing.json and grading.json if the host supports them. A valid file is not evidence of improved outcomes. Promote only after review and keep the previous revision for rollback.

Sources: https://agentskills.io/specification; https://agentskills.io/skill-creation/evaluating-skills; https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices. Original synthesis from the verified research snapshot, 2026-10-25.
