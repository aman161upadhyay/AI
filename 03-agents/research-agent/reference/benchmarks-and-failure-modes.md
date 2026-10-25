# Benchmark scope and research failures

Use separate tests for discovery, report quality, and citation support. No single benchmark below measures the full collaboration loop.

The counts describe the versions recorded in the research snapshot on 2026-10-25. They are not current leaderboard results.

| Benchmark | What it measures | Useful failure signal | What it cannot establish |
|---|---|---|---|
| [BrowseComp](https://arxiv.org/html/2504.12516v1), OpenAI, 2025-04 | 1,266 difficult browsing questions with short verifiable answers. | Query reformulation, persistent retrieval, entity disambiguation, and confidence when evidence is sparse. The paper reports increased confidence in some wrong answers after browsing. | Long report quality, ambiguity handling, or a useful recommendation. |
| [DeepResearch Bench](https://deepresearch-bench.github.io/), Du et al., 2025 paper | 100 expert-created report tasks across 22 fields, split between Chinese and English. RACE assesses reports; FACT assesses citations. | Fluent unsupported synthesis, poor citation support, and report coverage under reference-based criteria. | Complete discovery of all counterevidence or a judge free from reference bias. |
| [GAIA](https://arxiv.org/html/2311.12983v1), Mialon et al., 2023-11 | 466 human-authored questions that combine reasoning, web use, multimodality, and tools. | Failures in file inspection, cross-tool execution, and evidence chains. | Trace correctness from a correct final answer. The original benchmark does not evaluate the trace. Web decay affects reruns. |
| [Humanity's Last Exam](https://lastexam.ai/), CAIS, Scale AI, and contributors, 2025 | The finalized 2025 set has 2,500 difficult academic questions. Later rolling and Diamond variants differ. | Specialized correctness and overconfident closed-answer errors. | Open-ended research quality, creativity, or decision usefulness. Name version, subset, tool policy, and scoring setup in comparisons. |

## Local failure probes

| Risk | Observable check | Case |
|---|---|---|
| Invented or mismatched citations | Compare each sentence with its original passage, not only URL existence. | `research-agent-006.yaml` |
| Repeated commentary mistaken for corroboration | Count origin families and disclose dependencies. | `004` |
| Stale API facts | Compare dated docs and deprecated guidance. | `002`, `005` |
| Unsupported generalization across papers | Compare task, baseline, and feedback conditions before synthesis. | `003` |
| Premature convergence | Seek the strongest alternative and a discriminating observation. | `001`, `008` |
| Injection and private-data leakage | Inspect actual tool arguments and side effects with safe canaries. | `006` |
| Goal drift after clarification | Check the final decision against the revised brief. | `007` |
| Evidence loss during compression | Resume from notes and reopen originals; inspect preserved contradictions. | `007`, `008` |

These risks are proposed engineering probes, not measured prevalence estimates. OpenAI documents hallucination and uncertainty limits. STORM reports source-bias transfer and unrelated associations. Stanford's lateral-reading work addresses superficial credibility cues and search-ranking pitfalls. The four benchmarks do not jointly prove every failure listed here.

Keep public benchmark runs separate from private regressions because contamination is possible. Pin task snapshots, tools, model version, sampling budget, and scorer. Report failed tool runs and unknown grades. Compare one researcher with parallel variants at equal cost before claiming an architectural gain.
