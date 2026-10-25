# Protocol resources

Pin a protocol version and test authorization at the server boundary. Tool descriptions and agent discovery do not grant trust. Status date: 2026-10-25.

| Rank | Resource | Status | Why and limit |
|---|---|---|---|
| P1 | [MCP specification](https://modelcontextprotocol.io/specification/latest), MCP project | Latest observed version 2026-07-28 | Normative capabilities/transports/trust obligations; resolve and pin a dated version before implementation |
| P1 | [Introduction to MCP](https://anthropic.skilljar.com/introduction-to-model-context-protocol), Anthropic | Current first-party course | Python servers/clients, tools/resources/prompts, Inspector |
| P1 | [MCP Advanced Topics](https://anthropic.skilljar.com/model-context-protocol-advanced-topics), Anthropic | Current first-party course | Sampling, roots, progress, stdio/Streamable HTTP trade-offs |
| P2 | [Official reference servers](https://github.com/modelcontextprotocol/servers) | Active repository | Study schemas and examples; not security-certified integrations; mixed MIT/Apache history and CC-BY docs |
| P3 | [A2A overview](https://a2a-protocol.org/latest/topics/what-is-a2a/) and [repository](https://github.com/a2aproject/A2A) | Living first-party docs, active repo | Agent/task interoperability after single-agent reliability; not an execution sandbox or replacement for MCP |

Build a read-only corpus-search server first. Test capability/version negotiation, invalid arguments, cancellation, consent, authentication, tenant filtering, and malicious descriptions. Keep credentials in the execution layer and refuse unauthorized remote writes even when the local shell is sandboxed.
