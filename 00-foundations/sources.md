# Foundation sources

Snapshot: 2026-10-25. These annotations are original summaries. No upstream prose or implementation is vendored. Tier 1 identifies first-party authority for its own system, not independent proof of general effectiveness.

| Title and URL | Author / organization | Date | Tier | Contribution and limit |
|---|---|---|---|---|
| [Building effective agents](https://www.anthropic.com/engineering/building-effective-agents) | Erik S., Barry Zhang / Anthropic | December 2024, living revision | 1 | Workflow taxonomy and simpler-system baseline. |
| [Effective context engineering](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) | Anthropic Applied AI | 2025-09-29 | 1 | Attention budget, retrieval, compaction, context isolation. |
| [Lessons from building Manus](https://manus.im/blog/Context-Engineering-for-AI-Agents-Lessons-from-Building-Manus) | Yichao Ji / Manus | 2025-07-18 | 1 | Stable prefix, files, retained failures; implementation-specific masking. |
| [Writing effective tools](https://www.anthropic.com/engineering/writing-tools-for-agents) | Ken Aizawa / Anthropic | 2025-09-11 | 1 | Tool interfaces, bounded responses, held-out evaluation. |
| [Multi-agent research system](https://www.anthropic.com/engineering/multi-agent-research-system) | Jeremy Hadfield et al. / Anthropic | 2025-06-13 | 1 | Worker contracts and budgets; vendor research results are task-specific. |
| [Don't Build Multi-Agents](https://cognition.com/blog/dont-build-multi-agents) | Walden Yan / Cognition | 2025-06-12 | 1 | Coupled decisions and missing shared context. |
| [Multi-Agents: What's Actually Working](https://cognition.com/blog/multi-agents-working) | Walden Yan / Cognition | 2026-04-22 | 1, search-only | Qualifies the earlier warning; full capture unavailable. |
| [Advanced context engineering](https://www.humanlayer.dev/blog/advanced-context-engineering) | Dex Horthy / HumanLayer | 2025-08-29 | 2 | Intentional compaction and human review of research/plans. Practitioner experience, not a controlled causal study. |
| [Unrolling the Codex agent loop](https://openai.com/index/unrolling-the-codex-agent-loop) | Michael Bolin / OpenAI | 2026-01-23 | 1 | Prompt assembly, tool loop, sandbox scope. |
| [Best practices for Claude Code](https://code.claude.com/docs/en/best-practices) | Anthropic | Living docs | 1 | Verification and session hygiene. |
| [Agent Skills specification](https://agentskills.io/specification) | Agent Skills maintainers | Living specification | 1 | Portable frontmatter and disclosure. |
| [Skill authoring best practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices) | Anthropic | Living docs | 1 | Description writing, evaluation-first authoring, reference layout. |
| [Equipping agents with skills](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) | Zhang, Lazuka, Murag / Anthropic | October 2025; December 18 update | 1 | Skills as on-demand procedures; trust risks. |
| [Evaluating skills](https://agentskills.io/skill-creation/evaluating-skills) | Agent Skills maintainers | Living docs | 1 | With/without comparisons and activation checks. |
| [Prompt engineering](https://developers.openai.com/api/docs/guides/prompt-engineering) | OpenAI | Living docs | 1 | Instruction hierarchy, schemas, evals. |
| [Reasoning best practices](https://platform.openai.com/docs/guides/reasoning-best-practices) | OpenAI | Living docs | 1 | Clear zero-shot tasks, concise explanations rather than requested chain of thought. |
| [GPT-5 prompting guide](https://cookbook.openai.com/examples/gpt-5/gpt-5_prompting_guide) | OpenAI | GPT-5 era, exact day unverified | 1 | Eagerness, effort, contradictions. |
| [GPT-5.1 prompting guide](https://developers.openai.com/cookbook/examples/gpt-5/gpt-5-1_prompting_guide) | OpenAI | GPT-5.1 era, exact day unverified | 1 | Diagnosis-then-patch prompt revision. |
| [Claude prompting best practices](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/claude-4-best-practices) | Anthropic | Living docs | 1 | Grounding, examples, prefill compatibility. |
| [Gemini prompt strategies](https://ai.google.dev/docs/prompt_best_practices) | Google | Living docs | 1 | Long evidence placement and internal reasoning. |
| [Prompt Engineering](https://lilianweng.github.io/posts/2023-03-15-prompt-engineering/) | Lilian Weng | 2023-03-15 | 2 | Historical technique synthesis and limits. |
| [Prompting Fundamentals](https://eugeneyan.com/writing/prompting/) | Eugene Yan | May 2024 | 2 | Examples and decomposition. |
| [Persona study](https://arxiv.org/html/2311.10054v3) | Zheng et al. | EMNLP Findings 2024 | 1 | No overall factual benefit in tested open models; not a claim about every model or writing task. |
| [MIPROv2](https://dspy.ai/3.0.4/api/optimizers/MIPROv2) and [optimizer guidance](https://dspy.ai/learn/optimization/optimizers/) | DSPy | Version 3.0.4 / living docs | 1 | Metric-driven instruction/example search and reflective optimization. |
| [Official system prompts](https://platform.claude.com/docs/en/release-notes/system-prompts/overview) | Anthropic | Living release index | 1 | Authentic app snapshots, link only. |
| [OpenClaw architecture](https://docs.openclaw.ai/concepts/architecture), [skills](https://docs.openclaw.ai/tools/skills), [security](https://docs.openclaw.ai/gateway/security), [memory source](https://raw.githubusercontent.com/openclaw/openclaw/main/docs/concepts/memory.md) | OpenClaw | Living docs | 1 | Gateway trust boundary, skill execution, curated memory. |
| [Hermes architecture](https://hermes-agent.nousresearch.com/docs/developer-guide/architecture), [skills](https://hermes-agent.nousresearch.com/docs/user-guide/features/skills), [memory](https://hermes-agent.nousresearch.com/docs/user-guide/features/memory) | Nous Research | Living docs | 1 | Procedural learning, staged writes, session snapshots. |
| [Codex](https://github.com/openai/codex), [Claude Code](https://github.com/anthropics/claude-code), [Hermes](https://github.com/NousResearch/hermes-agent), [OpenClaw](https://github.com/openclaw/openclaw) | Respective maintainers | October 2026 snapshot | 1 | Comparison fields verified in research through docs and local source/license inspection. Features vary by version. |
| [LangGraph persistence](https://docs.langchain.com/oss/python/langgraph/durable-execution) | LangChain | Living docs | 1 | Checkpoints; side-effect idempotency still requires application design. |
| [Memory blocks](https://docs.letta.com/guides/core-concepts/memory/memory-blocks) | Letta | Living docs | 1 | Bounded core facts and read-only memory. |
| [Effective long-running harnesses](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents) | Anthropic | 2025-11-26 | 1, search-only | Initializer and executor; full capture unavailable. |
| [Ralph](https://ghuntley.com/ralph) and [loop](https://ghuntley.com/loop) | Geoffrey Huntley | 2025-07-14; 2026-01-17 | 1, search-only | Fresh-process loop origin; distinguish same-session plugin variants. |

Learning resources carry URLs and status in learning-path. System implementation and exemplar sources are recorded in [the system-design agent](../03-agents/system-design-agent/sources.md).
