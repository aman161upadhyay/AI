# Enforce authority outside the model

1. Separate the two gates. Application tests check the code being built. Execution tests check what the builder or reviewer can do with its own tools. Passing one does not satisfy the other.
2. Make the trusted dispatcher decide permissions. Validate principal, tenant, operation, resource and expiry before each action. Prompt text cannot grant a capability.
3. Constrain egress independently. Validate destination origins, resolved addresses and redirects in the execution layer. A browser or MCP tool must not evade shell-network policy.
4. Require independent human approval for destructive or externally visible sensitive actions. Bind approval to the exact operation and arguments. No worker can approve itself.
5. Apply least privilege per role and task. Use short-lived credentials with narrow scopes. Do not combine hostile-content readers, private-data access and arbitrary outbound communication.
6. Treat skills as supply-chain code. Review instructions and referenced downloads, pin artifacts and retain licenses. A marketplace scan or signature does not establish harmless behavior.
7. Separate control-plane state from worker artifacts. Protect skills, prompts, CI, hooks, tool registries and policy against edits, creation, rename and indirect writes.
8. Preserve trust across delegation and memory. Peer summaries remain attributed evidence. Memory facts need provenance and retention; they cannot silently become policy.
9. Fail closed on uncertain authorization. Stop on malformed policy, changed schemas or permission-service failure. Do not retry with a stronger identity.
10. Verify effects. Record redacted decisions and receipts outside worker control. Keep valid-task completion in the evaluation so universal refusal cannot pass.

These are proposed implementation requirements derived from MCP guidance, CaMeL, first-party harness documentation and incident lessons. No prompt or single guardrail library enforces all of them.
