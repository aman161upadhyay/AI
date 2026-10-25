# Twelve-week plan

Use 8 to 12 hours weekly on one tenant-aware research assistant. This is a proposed curriculum, not a claim that production readiness takes twelve weeks. Resource URLs, ranks, and evidence status are in the linked resource pages.

| Week | Study in priority order | Build artifact | Exit criterion |
|---|---|---|---|
| 1 | P1 Claude API course; P1 Chip Huyen's AI Engineering; P2 selected Hands-On LLMs chapters | Hand-built bounded loop and provider adapter with tool/error/usage traces | Fixed tool-use cases are reproducible; every action has a receipt |
| 2 | P1 eval resources; paid Hamel/Shreya course optional | Initial 50-case corpus, human rubric, failure taxonomy, baseline report | Human labels calibrate the judge; splits and cost/latency are recorded |
| 3 | P1 HF Agents course/smolagents; P2 Anthropic patterns or OpenAI SDK; P2 Andrew Ng | Sandboxed tool executor with timeouts, cancellation, permissions | Malformed arguments, provider failure, and unauthorized writes fail safely |
| 4 | P1 Supabase RLS/migrations, Neon pooling, Vercel checklist; P1 Payload/Trigger.dev study | Authenticated two-tenant app, durable job, object storage, deployment plan | Cross-tenant negatives pass; old-data migration and killed-job replay are safe |
| 5 | P1 Seven Failure Points/RAG survey; P1 retrieval cookbook; P2 advanced RAG course | Versioned ingestion, lexical/dense baselines, citations, ACL filters | Measure retrieval recall separately from correctness and unsupported answers |
| 6 | P1 contextual retrieval; P2 Chroma chunking and hybrid/reranking docs | Ablations for chunking, fusion, reranking, context packing; adversarial documents | Held-out gain justifies cost; deletion, missing answers, and ACLs pass |
| 7 | P1 MCP introduction/advanced course and pinned specification; P2 official servers | Read-only corpus-search MCP server/client with Inspector tests and threat model | Test schemas, negotiation, cancellation, auth, consent, and malicious descriptions |
| 8 | P1 SRE monitoring, OpenTelemetry, Trigger.dev; P2 LangGraph if needed; P3 A2A | Durable checkpoints, replay, trace correlation | Worker kill/restart, retry exhaustion, and mid-job membership revocation are safe |
| 9 | P1 DSPy and repeated failure analysis | Equal-budget comparison of manual prompts, optimized prompts, and tool/retrieval fixes | Select on validation only; report once on held-out test with regressions |
| 10 | P1 TRL SFT; P2 Unsloth and HF tool-calling unit | Small approved SFT/LoRA experiment with dataset/model cards | Beat a strong prompt-only baseline on task success and OOD cases; no split leakage |
| 11 | P1 verifiers and TRL GRPO; P2 ART, ReTool, SWE-RL | Bounded verifiable environment, reward tests, controlled RL run or study | Independent functional tests detect reward exploits; compute spend remains capped |
| 12 | P1 accumulated evidence; P2 AWS pillars and exemplars; prime-rl only if justified | Capstone ADRs, threat model, benchmark, restore runbook, cost model | Independent reproduction of evals/recovery; explicit go/no-go risks |

Use [infrastructure resources](resources-agentic-infrastructure.md), [RAG resources](resources-rag.md), [training resources](resources-training-agents.md), [protocol resources](resources-mcp-and-protocols.md), and [eval resources](resources-evals.md). All rank and currency decisions are dated 2026-10-25.

Retain a fixed corpus version and test split throughout the project. Do not train on private traces without explicit rights and retention approval. Record exact hardware and model requirements from current docs rather than assuming a universal one-GPU setup.
