# Security guardrails

Enforce agent permissions and network policy outside the model. Application-security tests and agent-execution tests are separate release gates.

- `FOR-AMAN.md`: inputs, access and ownership for adoption.
- `principles.md`: boundaries that the runtime must preserve.
- `runtime-guardrails.md`: controls, limits and required negative tests.
- `guardrail-config-examples.md`: illustrative Claude Code, Codex and MCP policy fragments.
- `testing-guardrails.md`: effect-based tests and proposed release gates.
- `sources.md`: provenance and config-source pins.

## Known gaps

This folder specifies controls; it does not install a proxy, sandbox, approval service or policy hook. Configuration fragments have not been run. Platform behavior and remote MCP authorization require deployment-specific validation. The owner must implement the independent approval/hash and trace oracles before treating examples as enforced policy.
