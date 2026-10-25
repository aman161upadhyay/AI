# Twenty-three named patterns

Choose a pattern because it addresses a measured failure. The definitions below are original summaries from the research, observed 2026-10-25. Names 22 and 23 are local synthesis, not a vendor taxonomy.

| # | Pattern | Mechanism and appropriate use | Failure control | Evidence |
|---|---|---|---|---|
| 1 | Augmented LLM | Give a model retrieval, tools, and memory behind interfaces | Bound scope and verify evidence | Anthropic effective agents |
| 2 | Prompt chaining | Pass a validated artifact through predefined stages | Reject bad intermediates before propagation | Anthropic effective agents |
| 3 | Routing | Select a specialized path by task class | Test ambiguity and unsupported classes | Anthropic effective agents |
| 4 | Plan-then-execute | Form a plan before expensive actions, then revise it from observations | Tie steps to acceptance checks and change the plan when evidence invalidates it | Anthropic effective agents; Claude Code practices |
| 5 | Orchestrator-workers | Let a lead dynamically decompose independent work | Explicit contracts and central integration | Anthropic research; Cognition |
| 6 | Parallel sectioning | Run different independent parts concurrently | Prevent duplicate work and cap fan-out | Anthropic effective agents/research |
| 7 | Parallel voting | Generate independent attempts, then adjudicate | Agreement is not proof; use external checks | Anthropic effective agents |
| 8 | Evaluator-optimizer | Iterate candidate and actionable critique | Bound revisions; prevent evaluator drift | Anthropic effective agents |
| 9 | Progressive disclosure | Index, selected procedure, selected resources | Test activation and near-miss cases | Anthropic context; Hermes |
| 10 | Just-in-time context | Retrieve exact evidence from lightweight pointers | Retain searchable originals and provenance | Anthropic context |
| 11 | Compaction | Replace long history with operational state | Preserve failures, tool IDs, approvals, raw evidence | Anthropic context; Codex; Manus |
| 12 | Sub-agent context isolation | Workers return bounded evidence-backed findings | Share source truth without full scratchpads | Anthropic research/context; Cognition |
| 13 | Filesystem-as-memory | Persist artifacts outside prompts and reopen by path | Index files and enforce access/retention | Manus; Anthropic; Hermes |
| 14 | Todo.md recitation | Refresh current objective near the working context | Remove stale or invalidated steps | Manus |
| 15 | Keep failures in context | Preserve causal error and attempted remedy | Compress duplicate logs without erasing failures | Manus |
| 16 | Stable-prefix caching | Keep reusable instructions/tool schemas deterministic | Relevance still needs evaluation | Manus; Codex |
| 17 | Tool masking | Restrict tool choice without rebuilding definitions | Use supported allowed-tool mechanisms; ordinary APIs may lack logit control | Manus |
| 18 | Initializer plus incremental executor | Initialize durable state, then make recoverable increments | Validate existing state at every session | Anthropic long-running harnesses, search-only |
| 19 | Fresh-context autonomous loop | Controller starts a fresh worker on a bounded task | External budgets, independent checks, no-progress exit | Huntley search evidence; plugin comparison |
| 20 | Durable execution and human interrupt | Persist state at pause/resume boundaries | Idempotency and receipts for side effects | LangGraph persistence |
| 21 | Procedural learning | Convert successful procedures and caveats into skills | Version and evaluate; do not claim weight training | Hermes |
| 22 | Shared decision ledger | Keep accepted constraints and integration decisions common | Serialize coupled decisions; isolate scratchpads | Local synthesis from Cognition/research |
| 23 | Evidence-gated promotion | Stage prompt/skill/memory changes and evaluate before approval | Generator cannot weaken permissions or acceptance tests | Local synthesis from Hermes approval and tool eval guidance |

Source URLs and evidence limits: [sources](../sources.md). Do not confuse the same-session Ralph Stop-hook variant with the original fresh-process pattern.
