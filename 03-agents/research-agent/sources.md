# Research-agent provenance

Built from `work/research/03-research-agent.md` and the research-judge guidance in `work/research/08-council-and-evals.md`. The technology-scout handoff also uses `work/research/10-prompts-and-marketing.md`. Those are internal synthesis inputs dated 2026-10-25, not independent evidence. Saved pages remain outside this distributable folder.

T1 means original evidence or authoritative documentation for the particular claim. T2 means accountable explanation. T3 means discovery only. Vendor material is T1 for the vendor's description, not for superiority. All sources below were captured or inspected in the supplied research. Repository paths were additionally inspected during the build.

| Title and URL | Author / organization | Date | Tier | Contribution |
|---|---|---|---|---|
| [How we built our multi-agent research system](https://www.anthropic.com/engineering/multi-agent-research-system) | Anthropic | 2025-06-13, research metadata | T1 | Delegation, separate contexts, CitationAgent, token-cost caution. |
| [Introducing deep research](https://openai.com/index/introducing-deep-research) | OpenAI | 2025-02-02; update 2026-02-10 | T1 | Iterative browsing, progress controls, acknowledged uncertainty failures. |
| [Gemini Deep Research agent](https://ai.google.dev/gemini-api/docs/interactions/deep-research?hl=en) | Google | Updated 2026-10-13 | T1 | Planning, API constraints, prompt-injection and exfiltration warnings. |
| [Introducing Perplexity Deep Research](https://www.perplexity.ai/hub/blog/introducing-perplexity-deep-research) | Perplexity | 2025-02-14, research metadata | T1 | Original iterative retrieval account. |
| [Deep Research, now in Computer](https://www.perplexity.ai/hub/blog/deep-research-now-in-computer) | Perplexity | 2026-06-11, search metadata only | T1 | Search as Code and deduplication as vendor-described design. |
| [Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) | Anthropic | 2025, exact day unverified | T1 | Compaction, external notes, context isolation. |
| [GPT Researcher introduction](https://docs.gptr.dev/docs/gpt-researcher/getting-started/introduction) | GPT Researcher maintainers | Undated; accessed 2026-10-25 | T1 | Planner/executor and source-count limits. |
| [STORM research](https://storm-project.stanford.edu/research/storm) | Stanford OVAL | NAACL 2024 | T1 | Perspective-guided research and documented failure modes. |
| [BrowseComp paper](https://arxiv.org/html/2504.12516v1) | OpenAI authors | 2025-04 | T1 | Difficult retrieval and confidence limitations. |
| [DeepResearch Bench project](https://deepresearch-bench.github.io/) | Du, Xu, Zhu, Wang, Mao; USTC and Metastone | Paper 2025-06-13 | T1 | Report quality and citation-support evaluation. Full paper fetch failed in research; claims here use the project account. |
| [GAIA paper](https://arxiv.org/html/2311.12983v1) | Mialon et al. | 2023-11 | T1 | Tool and multimodal evaluation, trace limitation. |
| [Humanity's Last Exam](https://lastexam.ai/) | CAIS, Scale AI, academic contributors | 2025 set; site updates through 2026-09 | T1 | Closed-answer expertise, calibration, version cautions. |
| [A Tradecraft Primer](https://www.cia.gov/resources/csi/static/Tradecraft-Primer-apr09.pdf) | CIA Center for the Study of Intelligence | 2009 | T1 | Alternative hypotheses, assumptions, contrary analysis. |
| [The SIFT Method](https://guides.lib.uchicago.edu/c.php?g=1241077&p=9082322) | University of Chicago Library, crediting Mike Caulfield | Undated | T2 | Trace assertions to original context. Original Caulfield fetch failed. |
| [Applying the CRAAP Test](https://library.csuchico.edu/sites/default/files/craap-test.pdf) | CSU Chico Meriam Library | 2010-09-17 | T1 | Source-evaluation dimensions. |
| [Fact checkers outperform historians](https://news.stanford.edu/stories/2017/10/fact-checkers-outperform-historians-evaluating-online-information) | Stanford Report, covering Wineburg and McGrew | 2017-10-24 | T2 | Lateral reading and superficial credibility risks. |
| [PRISMA 2020 checklist](https://www.prisma-statement.org/s/PRISMA_2020_checklist-ab3g.pdf) | PRISMA group | Statement published 2021 | T1 | Eligibility, selection counts, extraction, and bias disclosure. |
| [Performing a Project Premortem](https://hbr.org/2007/09/performing-a-project-premortem) | Gary Klein | 2007-09 | T1, partial capture | Failure framing and dissent. Exact agent procedure is local policy. |
| [Identifying and Cultivating Superforecasters](https://web.stanford.edu/~knutson/jdm/mellers15.pdf) | Mellers et al., including Tetlock | 2015 | T1 | Resolvable forecasts and calibration, with human-to-agent transfer limits. |
| [Demystifying evals for AI agents](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents) | Anthropic | 2026-01-09 | T1 | Trials, outcomes, deterministic checks, capability versus regression. |
| [Using LLM-as-a-Judge For Evaluation](https://hamel.dev/blog/posts/llm-judge/) | Hamel Husain | Living; accessed 2026-10-25 | T2 | Expert labels, binary gates, calibration by failure mode. |
| [Judging LLM-as-a-Judge](https://proceedings.neurips.cc/paper_files/paper/2023/hash/91f18a1287b398d378ef22505bf41832-Abstract-Datasets_and_Benchmarks.html) | Zheng et al. | 2023 | T1 | Position and verbosity bias, blinded review. |
| [Improving Factuality and Reasoning through Multiagent Debate](https://proceedings.mlr.press/v235/du24e.html) | Du et al. | ICML 2024 | T1 | Evidence used in the bounded literature eval. |
| [Large Language Models Cannot Self-Correct Reasoning Yet](https://openreview.net/forum?id=IkmD3fKBPQ) | Huang et al. | ICLR 2024 | T1 | Contrary evidence and baseline sensitivity in the literature eval. |
| [Self-Refine](https://selfrefine.info/) | Madaan et al. | 2023 | T1 | Feedback/revision mechanism in the literature eval. |
| [Inspect docs](https://inspect.aisi.org.uk/) | UK AISI | Living; accessed 2026-10-25 | T1 | Suggested runner interfaces, not a bundled runner. |
| [OpenAI deprecations](https://developers.openai.com/api/docs/deprecations) | OpenAI | Living; notice 2026-06-03 in research | T1 | Version/conflict eval and hosted-runner lifecycle caution. |
| [Archived LangSmith SDK](https://github.com/langchain-ai/langsmith-sdk/tree/main) | LangChain | Archived 2026-10-16 in research | T1 | Migration/conflict eval. |

## Inspected repositories, linked only

| Repository | Commit inspected | License | Contribution and caveat |
|---|---|---|---|
| [open_deep_research](https://github.com/langchain-ai/open_deep_research) | `1b7d2e80db9faa586165c60e09096dbbfd483a64` | MIT | Brief/supervisor/compression interfaces. Snapshot 2026-10-25, T1, LangChain. |
| [gpt-researcher](https://github.com/assafelovic/gpt-researcher) | `3582a6841fe7dc801e2a34e34ee408641aea9bce` | Apache-2.0 | Query processing and selection boundaries. Snapshot 2026-10-25, T1, Assaf Elovic and contributors. |
| [storm](https://github.com/stanford-oval/storm) | `fb951af7744dab086e34962e9bc6fe878e145f83` | MIT | Perspective generation. Head 2025-09-30 fails freshness gate. T1, Stanford OVAL. |
| [smolagents](https://github.com/huggingface/smolagents) | `96f33faaf028479119ec8d34507b47694cf14e34` | Apache-2.0 | Browser/manager example and GAIA paths. Broad code imports require isolation. Snapshot 2026-10-25, T1, Hugging Face. |
| [deep-research](https://github.com/dzhng/deep-research) | `1f8f3e285bbc23e80b98a66a64effab9069f3ad4` | MIT | Recursive discovery and URL-list attribution limitation. Head 2026-04-11 fails freshness gate. T1, David Zhang and contributors. |

No vendored artifacts are included, so no upstream license files are copied. The local source inspection is not a full security audit. Research source captures and benchmark data have separate rights.

The YAML cases are repository-authored adaptations of R1, R2, R4, R5, R6, R8, R9, and R10 in the research design. Synthetic trap text appears only in eval inputs and is labeled as such. None of the cases has a recorded execution result.
