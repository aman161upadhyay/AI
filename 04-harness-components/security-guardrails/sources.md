# Guardrail provenance

Research snapshot and local inspection date: 2026-10-25. Tier 1 denotes first-party guidance or implementation; tier 2 denotes practitioner interpretation. Examples and thresholds are local proposals, not vendor guarantees. Primary research inputs were `work/research/06-security.md` and `work/research/02-agent-architectures.md`.

| Source | Author/org | Date | Tier | Contribution |
|---|---|---|---|---|
| [MCP Security Best Practices](https://modelcontextprotocol.io/docs/tutorials/security/security_best_practices) | MCP maintainers | Living, observed 2026-10-25 | 1 | Token passthrough, consent, SSRF and confused deputy |
| [Defeating Prompt Injections by Design](https://arxiv.org/abs/2503.18813) | Debenedetti et al., including Google DeepMind researchers | 2025-03-24; revised 2025-06-24 | 1 | Capabilities and control/data separation |
| [Prompt-injection design patterns](https://simonwillison.net/2025/Jun/13/prompt-injection-design-patterns/) | Simon Willison | 2025-06-13 | 2 | Lethal trifecta and architecture tradeoffs |
| [Unrolling the Codex agent loop](https://openai.com/index/unrolling-the-codex-agent-loop) | Michael Bolin, OpenAI | 2026-01-23 | 1 | Execution loop and permission boundaries |
| [Claude Code best practices](https://code.claude.com/docs/en/best-practices.md) | Anthropic | Living, observed 2026-10-25 | 1 | Permissions, sandboxing and verification |
| [OpenClaw security](https://docs.openclaw.ai/gateway/security) | OpenClaw | Living, observed 2026-10-25 | 1 | Trust domains and runtime isolation |
| [OpenClaw skills](https://docs.openclaw.ai/tools/skills) | OpenClaw | Living, observed 2026-10-25 | 1 | Skills as supply chain; host-process secret injection |
| [Cursor advisory](https://github.com/cursor/cursor/security/advisories/GHSA-4cxx-hrm3-49rm) | Cursor | 2025-08 | 1 | Absent control-file creation regression |
| [OpenClaw gateway advisory](https://github.com/openclaw/openclaw/security/advisories/GHSA-g8p2-7wf7-98mq) | OpenClaw | 2026-01 | 1 | Token destination binding |
| [GitHub injection investigations](https://github.blog/security/vulnerability-research/safeguarding-vs-code-against-prompt-injections/) | GitHub Security | 2025-08-25; updated 2026-07-06 | 1 | Workspace and tool-boundary regression tests |
| [Claude Code strict settings](https://github.com/anthropics/claude-code/blob/2eff7a8d21c80be48904f62ebdea36d945d7b504/examples/settings/settings-strict.json) | Anthropic | Local inspection 2026-10-25 | 1 | Permission and managed-policy key names |
| [Claude Code hook example](https://github.com/anthropics/claude-code/blob/2eff7a8d21c80be48904f62ebdea36d945d7b504/examples/hooks/bash_command_validator_example.py) | Anthropic | Local inspection 2026-10-25 | 1 | PreToolUse shape and blocking exit code; implementation not copied |
| [Codex config schema](https://github.com/openai/codex/blob/970111f6cb62cc02fe36a82ea7d71b37a2889c97/codex-rs/core/config.schema.json) | OpenAI | Local inspection 2026-10-25 | 1 | Sandbox modes and workspace network/temp settings |
| [Codex config tests](https://github.com/openai/codex/blob/970111f6cb62cc02fe36a82ea7d71b37a2889c97/codex-rs/config/src/state_tests.rs) | OpenAI | Local inspection 2026-10-25 | 1 | `on-request` approval setting |

The last four sources were opened in the local supplied clones during this build. No product configuration was executed. Broader taxonomy/tool provenance is in `../../03-agents/security-agent/sources.md`.
