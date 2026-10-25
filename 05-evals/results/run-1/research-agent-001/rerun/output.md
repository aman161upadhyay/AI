# Decision memo

**Status:** Provisional; as of the supplied, undated evidence packet. All architecture and experiment settings below are proposals, not measured results.

Start with one researcher, not parallel workers. For internal engineering assistance, prioritize traceable answers, enforceable cost limits, and private-data containment over unproven throughput. The USD 50 monthly cap is this evaluation scenario's constraint, not Aman's actual budget. Missing prices and query volume prevent any affordability or capacity guarantee. [S3]

Proposed baseline: clarify the question; create a brief; retrieve only approved, selected Drive/Notion collections; maintain source IDs and passage locators; synthesize; perform a separate citation-verification pass. Keep retrieval read-only and prohibit external writes. Collection access does not authorize exporting private content to a model provider: until processing boundaries are approved, use only approved nonsensitive fixtures. Separate verification is a stage, not necessarily another agent.

The packet attributes orchestrator-worker research and a separate CitationAgent to Anthropic, alongside approximately fifteen times ordinary-chat token use in its own system. This is neither a measured parallel-versus-single comparison here nor a transferable cost multiplier. [S1] The packet describes LangChain stages covering clarification, briefing, supervision, researcher compression, and writing; adopt useful workflow separation without assuming worker concurrency is necessary. [S2]

The strongest alternative is a supervisor with two workers assigned independent subquestions, followed by synthesis and citation checking. It could improve breadth or latency on decomposable questions; that is a hypothesis, not established performance. Shared context, duplicated retrieval, lost caveats during compression, and coordination overhead could erase those benefits.

Before adoption, propose twelve authorized questions, including decomposable and tightly coupled tasks. Freeze corpus, model, tools, and scoring rubric; randomize run order and blind reviewers. Baseline uses one researcher; candidate uses two workers. Give each arm the same per-question ceilings: USD 0.25 and 8,000 total tokens, whichever binds first, including planning, retrieval-model usage, supervision, compression, synthesis, verification, and retries. Stop that arm immediately at either ceiling; retain and score its partial answer, with incompleteness recorded, without top-ups.

The experiment's maximum metered spend is USD 6 across twenty-four runs; reserve the remaining USD 44, not assumed production capacity. Do not execute until prices, token accounting, and private-data processing approval are established. Measure rubric passes, unsupported claims, citation entailment, disclosure violations, latency, tokens, and total spend.

Reverse toward parallelism only if it produces at least two additional passing answers, no safety regression, and no worse median latency under matched limits. Otherwise retain one researcher; investigate ceiling hits before expanding scope.

## Evidence limits and audit

- **S1:** Packet `inputs`, paragraph beginning “S1 Anthropic reports”; attributed claims only. Linked original: https://www.anthropic.com/engineering/multi-agent-research-system
- **S2:** Packet `inputs`, paragraph beginning “S2 LangChain has”; attributed workflow description only. Linked original: https://github.com/langchain-ai/open_deep_research
- **S3:** Packet `inputs`, scenario/access statements and paragraph beginning “S3 No workload traces”; establishes supplied constraints and missing evidence, not real-world absence.
- Both original destinations remain unread: network use is prohibited. Publication dates, versions, methods, current prices, and benchmark applicability are unknown. These are distinct attributed origins, not independent corroboration of parallelism's superiority. No source credibility total is justified.
- Citation pass checked the S1–S3 assertions against the supplied packet after drafting. Original-source existence, passage entailment, corrections, and currency remain unaudited. Architecture, thresholds, and failure modes are explicitly proposals or hypotheses.
- Arithmetic: 12 questions × 2 arms × USD 0.25 = USD 6; USD 50 − USD 6 = USD 44. The proposed 8,000-token limit is not a price conversion.
- **Premortem:** Either architecture could produce convincing answers with invalid citations or exceed the processing authorization. Block release on any disclosure violation; keep unsupported/incomplete answers visible. Suspend even the single-researcher design if controls fail or measured monthly demand cannot fit the cap.
- Actual external calls, paid calls, retries, and private-collection reads: **0**. External spend: **USD 0**; local/model hosting costs are not supplied or estimated. No experiment was executed. Elapsed research time was not instrumented. Stop reason: packet-only scope, not saturation or exhausted budget.

## Questions and bounded assumptions

1. What monthly query volume and response-time target should this support?
2. What answer-acceptance rubric and reviewer will define a passing result?
3. Which processing environment, if any, is approved for private Drive/Notion content?

Pending answers, assume an engineering decision-maker, an initial pilot rather than production rollout, and no private-data export permission. Required comparison and a proposed test are covered; workload performance, economic feasibility, and original-source verification remain unresolved. No baseline or candidate execution results are implied.
