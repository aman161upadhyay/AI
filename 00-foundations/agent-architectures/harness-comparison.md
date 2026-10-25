# Compare harnesses by purpose and boundary

Snapshot: 2026-10-25. Fields below were established through first-party docs and repository/license inspection in the research. Capability can vary by installed version and surface. No runtime compatibility test was performed.

| Field | OpenClaw | Hermes Agent | Claude Code | Codex |
|---|---|---|---|---|
| Purpose | Always-on assistant across channels/devices | Persistent general agent with CLI/channels and procedural learning | Interactive development agent | Coding harness, CLI/SDK and related hosted surfaces |
| Provider support | Configurable providers/models; depth varies | Multiple provider modes; exact parity unverified | Primarily Claude; hosting provider choice is not arbitrary-model support | Configurable providers/local OSS endpoint; optimized for Codex models |
| Skills | SKILL.md with frontmatter; layered roots and runtime metadata | Agent Skills-compatible packages and progressive discovery | `.claude/skills/`, plugins, host-specific fields | SKILL.md skills; repository instructions separately in AGENTS.md |
| Memory | USER.md, MEMORY.md, daily notes, optional DREAMS.md and consolidation | Bounded MEMORY.md/USER.md, SQLite/FTS5 recall, frozen session bootstrap | CLAUDE.md, product memory, compaction and artifacts; no weight-learning claim | AGENTS.md, workspace/session artifacts, compaction; not a semantic memory service by itself |
| Tools/MCP | Native policies and plugins; MCP parity is version/plugin-dependent and unverified | Native tools, terminal backends, MCP client | Shell/edit/search and supported MCP integrations/hooks | Shell/edit/search, MCP schemas, Responses loop |
| Delegation | Routing and isolated subagent sessions | `delegate_tool.py` and scoped subagents | Custom agents/subagents and documented fan-out | Delegation/agent communication in current source; surface availability varies |
| Security | One personal trust boundary per gateway; pairing, policies, approvals, sandbox options | Tool approvals, backend isolation, profiles, project-skill trust, staged skill edits | Permissions, sandboxing, hooks; version-dependent modes | Sandbox, approvals, command rules; remote MCP needs separate controls |
| Self-hosting | Gateway/runtime yes; model hosting separate | Runtime yes; model hosting separate | Local proprietary client, not an open service/model stack | Open CLI/harness yes; hosted service separate |
| Root license | MIT | MIT | Commercial Terms, not a permissive core | Apache-2.0 |
| Study first | Gateway/session/device boundaries | Loop, procedural learning, memory economics | Verification and human workflow | Loop, compaction, instructions, sandbox |

Exact cross-model performance, cost per comparable task, and tenant-isolation audits are unverified for all four. They must not be inferred from this table.

Popularity is not needed for selection. Research had conflicting Hermes snapshots and secondary-only Codex/Claude Code counts, so this comparison does not present precise stars.

Primary sources: [OpenClaw](https://github.com/openclaw/openclaw), [Hermes](https://github.com/NousResearch/hermes-agent), [Claude Code](https://github.com/anthropics/claude-code), [Codex](https://github.com/openai/codex), with linked first-party docs in [sources](../sources.md). Inspect nested licenses before copying any artifact.
