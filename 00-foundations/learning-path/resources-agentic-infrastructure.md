# Agentic infrastructure resources

Learn the loop before choosing an orchestration framework. All statuses below are as of 2026-10-25. Tier 1 denotes original authors or first-party docs; no course completion or runtime compatibility was tested.

| Rank | Resource | Status | Why and bounded use |
|---|---|---|---|
| P1 | [Building with the Claude API](https://anthropic.skilljar.com/claude-with-the-anthropic-api), Anthropic | Current first-party course | Tool schemas, streaming, errors, evals; implement a hand-built loop |
| P1 | [HF Agents course](https://huggingface.co/learn/agents-course/unit0/introduction), Hugging Face | Current course | Assignment and readable agent primitives; pin lesson dependencies |
| P1 | [smolagents](https://github.com/huggingface/smolagents), Hugging Face | Active repository | Inspect `src/smolagents`, examples, tests; code execution requires isolation |
| P1 | [Anthropic cookbook](https://github.com/anthropics/anthropic-cookbook), Anthropic | Active repository | `patterns/agents`, `tool_use`, `tool_evaluation`; first-party experiments |
| P1 | [Supabase RLS](https://supabase.com/docs/guides/database/postgres/row-level-security) and [migrations](https://supabase.com/docs/guides/deployment/database-migrations) | Living first-party docs | Real tenant tests and versioned rollout before deployment |
| P1 | [Neon pooling](https://neon.com/docs/connect/connection-pooling) | Living first-party docs | Connection budgets and transaction-local semantics |
| P1 | [Vercel production checklist](https://vercel.com/docs/production-checklist) | Updated 2026-08-11 | Preview isolation, regions, rollback, spend; plan restrictions apply |
| P1 | [SRE monitoring](https://sre.google/workbook/monitoring/), Google, 2018; [OpenTelemetry](https://opentelemetry.io/docs/concepts/observability-primer/) | Foundational workbook; living telemetry docs | Connect critical journeys to trace IDs and actionable alerts |
| P1 | [Trigger.dev](https://github.com/triggerdotdev/trigger.dev); [Payload](https://github.com/payloadcms/payload) | Active repositories | Durable job lifecycle and server-side access composition; adopted implementations, not security certification |
| P2 | [OpenAI Agents SDK](https://openai.github.io/openai-agents-python/) | Living first-party docs | Handoffs, sessions, tracing; add only a missing capability |
| P2 | [Agentic AI](https://www.deeplearning.ai/courses/agentic-ai/), Andrew Ng | Updated 2026-08-31 | Practical reflection/tools/planning supplement |
| P2 | [LangChain Academy](https://academy.langchain.com/) | Current first-party course directory | Specialize in durable graphs/tracing only when needed |

Use the [system-design agent](../../03-agents/system-design-agent/README.md) for architecture artifacts and [production exemplars](../../06-reference-library/production-exemplars/README.md) for subsystem study.

## Pending: not yet inspected

- [AI Engineering](https://huyenchip.com/books), Chip Huyen, 2025: the author-hosted book page was fetched, not the substantive book text. Not an admitted reading recommendation as of 2026-10-25; inspect an authorised copy first.
- [Hands-On LLMs](https://www.llm-book.com/), Jay Alammar and Maarten Grootendorst, 2024: the book website was inspected, not the substantive book text. Not an admitted reading recommendation as of 2026-10-25; inspect an authorised copy first.
