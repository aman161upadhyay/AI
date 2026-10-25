# Reduce accepted-task cost

Give your agent a representative task set, acceptance tests, current model IDs, harness version and provider usage exports. Ask: “Find the largest repeated-input cost, change one mechanism, and compare accepted-task quality and total cost on the same tasks.”

Load principles.md first. Load caching notes only when you control API calls or need to diagnose CLI-managed caching. Do not inject every optimization document into every coding task.

Grant read access to redacted usage records and task artifacts. Refuse billing credentials, unredacted transcripts and permission to change production model routing. Keep evaluator files read-only. Set dollar and time limits before fan-out.

Start with ten observed tasks to establish costs, then use paired held-out cases with at least three runs per variant. Include the coding agent's fake-test and blocked-verification cases. Reject a cheaper configuration if it fabricates evidence or weakens acceptance. Review quality failures with the agent before promoting a configuration. You approve the spending caps and model changes.
