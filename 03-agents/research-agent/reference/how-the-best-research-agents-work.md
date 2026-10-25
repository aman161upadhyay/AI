# Documented research-agent designs

An evidence-preserving lead researcher is the starting design here. Parallel discovery is optional. This recommendation is repository judgement based on the architectures below, not an independently measured product ranking.

Snapshot: 2026-10-25. Vendor accounts establish their published design claims. They do not establish comparative quality for Aman's workload.

| System | Documented architecture | What to borrow | Failure mode or limit |
|---|---|---|---|
| Anthropic multi-agent research | Lead orchestrator delegates to workers with separate context, then synthesizes. A separate CitationAgent handles attribution. | Give bounded assignments and return evidence artifacts. Separate discovery from citation review. | Vague delegation produces overlap and gaps. Anthropic reports much higher token use than chat, about 15 times in its account. Internal evaluations do not predict local ROI. [A1] |
| OpenAI deep research | End-to-end reinforcement learning for iterative browsing and reasoning. The system can change direction after reading. | Let findings revise the plan. Make progress and correction possible. | OpenAI acknowledges hallucinations and authority-assessment limits. Its public description does not establish an orchestrator-worker graph or a separate citation agent. [A2] |
| Gemini Deep Research | Plan, search, read, iterate, and synthesize. The documented API supports collaborative planning and background work. | Offer plan approval and interruption. Keep permissions separate from research instructions. | Capabilities depend on endpoint and revision. The 2026-10-13 docs warn about malicious pages and data exfiltration. Verify current tool and output restrictions before integration. [A3] |
| Perplexity | The 2025 description uses iterative search/read/reason. The 2026 Computer account describes Search as Code with sandboxed parallel retrieval, scoring, and deduplication. | Inspect retrieval orchestration and retain origin lineage. | Retrieval scale and claim-level citation claims are vendor assertions. They do not establish citation entailment accuracy. Do not merge the two dated architectures into one timeless description. [A4, A5] |
| GPT Researcher | Planner proposes questions, executors collect material, context selection filters it, and a writer prepares the report. | Separate query generation, selection, and report generation. | A product target such as 20+ sources does not establish independence or completeness. The local wrapper still needs per-claim evidence checks. [A6, R2] |
| STORM and Co-STORM | Perspective-guided, source-grounded conversations precede outline and article generation. Co-STORM adds collaborative discussion. | Discover perspectives before freezing the outline. | The project reports source-bias transfer and unrelated-fact association. Perspective variety does not guarantee evidence independence. The inspected default branch fails the maintenance gate. [A7, R3] |
| LangChain Open Deep Research | Clarify, write brief, supervise bounded research, compress findings, and generate the final report. | Explicit state transitions and configurable budgets provide testable interfaces. | Current and legacy graphs differ. Do not infer that compression preserves claim support without a local audit. [R1] |
| Hugging Face smolagents example | A code-agent manager uses a managed browser researcher, file inspection, and visual tools. GAIA scripts provide an evaluation path. | Inspect the browser and document-tool contracts and scoring scripts. | Code execution needs isolation. The inspected example permits all additional imports, which is not an appropriate default for a secrets-bearing environment. [R4] |
| dzhng deep-research | Generate queries, collect learnings and URLs, recursively reduce breadth/depth, then write. | A compact baseline for learning recursive search. | `writeFinalReport` appends visited URLs after prose generation. A URL set does not preserve atomic support. The inspected head fails the maintenance gate. [R5] |

## Inspected implementation links

No source code is copied. These references pin the local snapshots that were inspected.

| ID | Repository, commit, license | Paths to study |
|---|---|---|
| R1 | [LangChain](https://github.com/langchain-ai/open_deep_research/tree/1b7d2e80db9faa586165c60e09096dbbfd483a64), MIT | `src/open_deep_research/deep_researcher.py` for clarification and supervision; `prompts.py` for task contracts; `tests/evaluators.py` for evidence checks. |
| R2 | [GPT Researcher](https://github.com/assafelovic/gpt-researcher/tree/3582a6841fe7dc801e2a34e34ee408641aea9bce), Apache-2.0 | `gpt_researcher/actions/query_processing.py` for query normalization and retrieval; `context/` for selection and compression; `actions/report_generation.py` for writing. |
| R3 | [STORM](https://github.com/stanford-oval/storm/tree/fb951af7744dab086e34962e9bc6fe878e145f83), MIT | `knowledge_storm/storm_wiki/modules/persona_generator.py` for perspective generation; `knowledge_curation.py` and `outline_generation.py` for prewriting. |
| R4 | [smolagents](https://github.com/huggingface/smolagents/tree/96f33faaf028479119ec8d34507b47694cf14e34), Apache-2.0 | `examples/open_deep_research/run.py`, `run_gaia.py`, and `scripts/text_web_browser.py`. |
| R5 | [dzhng](https://github.com/dzhng/deep-research/tree/1f8f3e285bbc23e80b98a66a64effab9069f3ad4), MIT | `src/deep-research.ts` for recursion and final source-list construction; `src/feedback.ts` for clarification. |

STORM's head is dated 2025-09-30. dzhng's head is dated 2026-04-11. Both precede the 2026-04-25 maintenance cutoff. Their research value does not justify recommending them as current dependencies without another audit.

## Sources

A1: Anthropic, [How we built our multi-agent research system](https://www.anthropic.com/engineering/multi-agent-research-system), 2025-06-13 in research metadata.

A2: OpenAI, [Introducing deep research](https://openai.com/index/introducing-deep-research), 2025-02-02, update 2026-02-10.

A3: Google, [Deep Research agent](https://ai.google.dev/gemini-api/docs/interactions/deep-research?hl=en), updated 2026-10-13 in saved docs.

A4: Perplexity, [Introducing Perplexity Deep Research](https://www.perplexity.ai/hub/blog/introducing-perplexity-deep-research), 2025-02-14 in research metadata.

A5: Perplexity, [Deep Research, now in Computer](https://www.perplexity.ai/hub/blog/deep-research-now-in-computer), 2026-06-11 in search metadata, not the extracted body.

A6: GPT Researcher maintainers, [Introduction](https://docs.gptr.dev/docs/gpt-researcher/getting-started/introduction), undated, accessed 2026-10-25.

A7: Stanford OVAL, [STORM research](https://storm-project.stanford.edu/research/storm), NAACL 2024.
