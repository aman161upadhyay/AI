# Decision memo

Recommend one researcher initially, with clarification, a research brief, selected-collection read-only retrieval, evidence notes, synthesis, and a separate citation-verification pass. This is a conservative proposal, not a demonstrated performance winner. Optimize for supported answers, privacy compliance, and measured total cost before latency. The scenario ceiling is USD 50 monthly; it is not evidence of Aman's actual budget. [S3; scenario]

The baseline is one researcher doing those stages sequentially. The candidate is a supervisor dispatching two workers on independent subquestions, then deduplicating evidence, synthesizing, and verifying citations centrally. Both must use identical collection permissions, evidence requirements, and evaluation criteria. Neither design receives permission to export private text merely because read access exists.

The packet attributes an orchestrator-worker design, separate CitationAgent, and approximately fifteen times ordinary-chat token consumption to Anthropic's own system. This is an attributed system-specific observation, not a multiplier for our baseline, dollar cost, or expected accuracy. [S1] The packet describes LangChain stages covering clarification, brief, supervisor, researcher compression, and writing; those stages inform workflow options, not proof that parallel workers improve this workload. [S2]

The strongest alternative is bounded parallel research for genuinely separable questions. It could reduce elapsed time or broaden coverage; neither advantage is established here. Its strongest case would be repeated broad requests with independent evidence branches and valuable latency savings. Conversely, a single researcher may miss perspectives or become a bottleneck. Parallel workers may duplicate retrieval, lose caveats during compression, or complicate permission enforcement. These are design risks to test, not observed failures.

Start with a shared evidence ledger containing source locators, atomic claims, uncertainty, and access scope. Preserve original pointers through compression. Use an independent verification pass rather than requiring another concurrent agent. Deny writes and unapproved export; keep private retrieval inside an approved processing boundary. If that boundary is unspecified, use only the supplied packet until clarified.

Do not infer affordability from the cap. Prices, query volume, and traces are absent, so neither architecture has a defensible monthly estimate. [S3] Instrument aggregate tokens, cost, latency, citation support, and permission violations across all workers and retries. Enforce one global ceiling outside prompts.

Run the bounded comparison below only after pricing and processing approval. Prefer the baseline unless the candidate clears preregistered quality, latency, privacy, and cost gates. Reverse toward parallelism on repeatable gains within the monthly envelope; reverse immediately toward restricted sequential operation after an export violation, unsupported critical citation, or unenforceable spend control.

## Questions and scope

1. What representative workloads and monthly query volume should this support?
2. Which model prices and enforceable spending controls apply?
3. Is private-data export approved, and to which processing boundary?

Proceeding without answers: internal engineering decision-makers are the audience; this is an initial architecture recommendation, not implementation authorization. As-of basis: the supplied undated packet, not current documentation.

## Bounded experiment — proposal, not performed

After approval, select six representative questions, including separable and tightly dependent questions, using authorized evidence only. Run each once under **baseline: one researcher** and **candidate: supervisor plus two workers**. Use the same model configuration, corpus, answer requirements, and citation pass. Freeze scoring before runs; blind the reviewer to architecture.

Suggested gates, explicitly proposed rather than empirical: no permission violations or unsupported critical claims; at least equal supported-answer quality; at least 20% lower median elapsed time; and projected monthly cost within USD 50 using supplied volume plus a stated contingency. Record retrieval duplication and compression losses. Six pairs are a screening exercise, not a reliable estimate of population performance; repeat borderline findings before expansion.

Reserve at most USD 5 total for this experiment **within**, not in addition to, the monthly ceiling, subject to explicit approval. Before dispatch, partition that shared allowance among supervision, workers, synthesis, verification, and retries, with a token ceiling calculated from approved prices. Stop before any call whose maximum charge exceeds remaining allowance. If prices or enforcement are unavailable, do not run. No paid calls were made here.

## Evidence limits and citation audit

| ID | Packet locator and claim | Audit result |
|---|---|---|
| S1 | `candidate.json`, inputs, paragraph beginning “S1 Anthropic reports” | Memo matches supplied attribution; original unread. No independent corroboration or transferable cost benchmark. |
| S2 | Same inputs, paragraph beginning “S2 LangChain” | Workflow description matches packet; original repository/version unread. No comparative outcome evidence. |
| S3 | Same inputs, paragraph beginning “S3 No workload traces” and preceding scenario/access lines | Establishes missing inputs and scenario restrictions, not actual workload economics. |

Supplied destination URLs, not fetched: [Anthropic](https://www.anthropic.com/engineering/multi-agent-research-system); [LangChain](https://github.com/langchain-ai/open_deep_research).

Methods: one researcher; packet-only comparison and contrary-case review; no workers, network calls, retries, private retrieval, tests, or paid calls. Incremental paid-tool spend: USD 0; execution/model billing and elapsed research time were not measured. All external factual claims were checked against the packet after drafting; original-source identity, dates, versions, passages, corrections, and performance remain unaudited. Coverage is bounded, not complete. Stop reason: packet-only authorization and unavailable runtime evidence, not saturation or budget exhaustion.
