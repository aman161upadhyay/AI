# Harness components

The parts of an agent system that sit around the model: how context is assembled, how tools are described, what the agent is allowed to do, and how its behaviour is measured. Each folder is reference material with a concrete contract an engineer can implement, not a library. Token optimisation lives next door in `00-foundations/token-optimization/` because it is as much a way of thinking as a component.

| Folder | What it covers | Start with |
|---|---|---|
| [memory-and-context](memory-and-context/) | Keep a small always-visible core and retrieve evidence per task; architectures for persistent memory (files, summaries, retrieval), named patterns, and the failure modes (context rot, poisoning, lost-in-the-middle) | `context-engineering-principles.md`, then `anti-patterns.md` |
| [tool-design](tool-design/) | Build tools around the tasks agents actually do; a description contract for every tool; MCP safety notes with the handoff to the security agent | `writing-tools-for-agents.md`, then `tool-description-template.md` |
| [security-guardrails](security-guardrails/) | Enforce permissions and network policy outside the model; runtime guardrails; configuration examples for sandboxes, allow-lists, and approval gates; how to test the guardrails themselves | `principles.md`, then `guardrail-config-examples.md` |
| [evals-framework](evals-framework/) | A portable eval-case schema shared by every agent in `03-agents/`, a runner contract (Inspect is the recommended runner), LLM-judge setup, error analysis, calibration, and regression tracking | `eval-case-schema.md`, then `how-to-write-evals.md` |

Each folder has its own `sources.md`. Where a recommendation rests on one vendor's documentation (prompt caching, hook semantics, MCP transport details), the as-of date is next to it, because those pages change.

The agents in `03-agents/` depend on all four components. Their `FOR-AMAN.md` files link to the implementation guidance here.
