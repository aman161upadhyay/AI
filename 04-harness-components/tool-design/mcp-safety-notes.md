# MCP safety notes

A local shell sandbox does not automatically constrain remote MCP actions. OpenAI's Codex loop account explicitly distinguishes those boundaries. Enforce authorization in the server and dispatcher.

## Tool poisoning

A malicious description, resource or result can contain instructions that ask the model to reveal secrets, change policy or call another tool. Treat all server-provided text as data. Never use a tool description as approval to access unrelated resources.

Pin and review server versions and schemas. Show additions and description changes to the owner. Keep secrets behind narrow runtime credentials. Restrict outbound domains and tool-to-tool side effects. A prompt warning alone cannot contain a compromised process.

## Rug pulls

A server can change its description or behavior after initial approval. This is a threat model, not a reproduced incident in this library. Compare schema/description hashes on reconnect, stage updates and rerun held-out evals before activation. Schema hashing cannot detect unchanged descriptions with changed backend behavior.

Review server ownership and deployment updates as well as client-visible text. Retain call receipts and support credential revocation. Separate trust domains for unrelated users and organizations.

## Write safety

Require explicit scoped approvals for publication, deletion, production changes and credential-bearing actions. Validate resource ownership at execution time. Use idempotency keys and reconcile uncertain writes before retrying. Hints such as `readOnlyHint` are not authorization controls.

Send suspected poisoning or exfiltration to the [security agent](../../03-agents/security-agent/README.md) with authorized scope, server version, redacted suspicious text and receipts. Do not probe external systems or execute payloads without written authorization. The repository's security-agent folder is the handoff target; confirm its current policy before use.

Test malicious result text, changed descriptions, denied tenant access, unknown resource IDs, timeouts and ambiguous write outcomes in a sandbox. Fail the harness on secret exposure or unauthorized mutation even if the final answer is correct.
