# Sources

Snapshot: 2026-10-25. Summaries are original; no third-party code is installed here.

| Title and URL | Author / date / tier | Contribution and limit |
|---|---|---|
| [Writing effective tools for agents](https://www.anthropic.com/engineering/writing-tools-for-agents) | Ken Aizawa / Anthropic; 2025-09-11; 1 | Tool selection, namespacing, bounded results and held-out evaluation. |
| [MCP-builder skill](https://github.com/anthropics/skills/tree/main/skills/mcp-builder) | Anthropic; local snapshot inspected 2026-10-25; 1 | Schemas, annotations, SDK workflow and ten read-only eval questions. SKILL.md and reference/mcp_best_practices.md were read locally. Linked, not vendored. |
| [Unrolling the Codex agent loop](https://openai.com/index/unrolling-the-codex-agent-loop) | Michael Bolin / OpenAI; 2026-01-23; 1 | Remote tools require their own controls. |
| [Building effective agents](https://www.anthropic.com/engineering/building-effective-agents) | Erik S. and Barry Zhang / Anthropic; Dec 2024, living revision; 1 | Simple interfaces and measurable stopping. |
| [OpenClaw security](https://docs.openclaw.ai/gateway/security) | OpenClaw; living; 1 | Trust boundaries, skills as code and isolation. |
| [Configure permissions](https://code.claude.com/docs/en/permissions.md) | Anthropic; living; 1 | Permissions differ by tool path and runtime. |

Research inputs: `work/research/02-agent-architectures.md` and `07-coding-harness-and-tokens.md`. Poisoning, rug-pull controls and idempotency policy are local threat-model synthesis from untrusted-tool and boundary principles. No specific MCP exploit was reproduced or claimed as verified.
