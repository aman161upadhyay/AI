# Put the controls in the runtime

Ask your coding or system-design agent: “Implement the policy in these documents for this tool inventory. Demonstrate denial and permitted behavior with independent traces.” Supply user/tenant scopes, destinations, writable roots, data labels, tool schemas and budgets. Name a human approver and incident owner.

Start with read-only repository access and synthetic fixtures. Grant short-lived tool-specific credentials through a broker. Refuse production-admin shell, host credential mounts, unrestricted network, self-approval and worker writes to policy, hooks, prompts or MCP configuration.

Approve each external send, destructive operation, deployment, new connector, permission expansion and sensitive export with exact arguments and destination. Keep approval keys outside the agent process. Do not make a model-generated confirmation sufficient.

Use `testing-guardrails.md` and the linked security-agent evals before you grant broader tools. Inspect actual filesystem, network and database effects. A refusal sentence is not evidence that a tool was blocked.

Have the implementer show the policy decision path, then ask an independent reviewer to test bypasses and benign tasks. You decide residual risk with an expiry. Re-run the suite after model, tool, skill, schema or policy changes.
