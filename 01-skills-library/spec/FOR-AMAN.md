# Start with a repeated failure

Ask: "Write a skill for this recurring task. Use these three examples and this near miss. Follow specification.md and authoring-guide.md. Return acceptance checks before expanding the procedure."

Supply the task vocabulary, one successful artifact, a failure trace and the actual host tools. Request name/description validation separately from host-specific metadata checks. You do not need network access or credentials to write the first procedure.

Refuse automatic dependency installation and production writes. Treat any bundled executable as a separate code review. Keep the documentation's attribution if you adapt it; its CC-BY licence differs from the upstream code licence.

Run clean with-skill and without-skill sessions on the same tasks. Review activation, factual correctness and unsafe-action behavior. Add a held-out case after revising the draft. You approve the skill only after the result meets the stated acceptance checks, not because the frontmatter parses.
