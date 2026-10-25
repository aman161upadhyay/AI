# Prompting principles ranked by evidence

Prioritize task definition and evaluation before elaborate prompting methods. This ordering is editorial priority, not a universal ranking of effect sizes.

A means convergent first-party guidance or testable API behavior. B means bounded empirical evidence or consistent practitioner guidance. C means a heuristic that needs local evaluation. First-party guidance can still fail on another model.

| Rank | Principle | Evidence | Use and failure condition |
|---|---|---|---|
| 1 | Define task, success criteria, and cases | A: OpenAI guide; DSPy | Improves testability; proxy metrics can miss the real goal. |
| 2 | Remove contradictions and state clear instructions | A: OpenAI, Anthropic, Google | Reduces ambiguity; overlapping rules can make it worse. |
| 3 | Supply relevant evidence and permit abstention | A: provider grounding guidance | Supports factual work; stale or malicious sources remain unsafe. |
| 4 | Enforce supported output schemas | A: OpenAI and Anthropic | Supports machine consumers; syntax validity is not truth. |
| 5 | Respect priority and separate data | A: provider roles/structure | Prevents accidental mixing; delimiters alone do not block injection. |
| 6 | Add representative demonstrations when needed | A/B: providers, Weng | Helps boundary labels and voice; inconsistent examples teach errors. |
| 7 | Use native reasoning controls | A: OpenAI reasoning/GPT guides | Trades quality against latency; maximum effort wastes trivial-task budgets. |
| 8 | Put long evidence before the specific query | A: Google, Anthropic | Helps long-document work; keep durable policy in its higher-priority message. |
| 9 | Specify tools, budgets, and stop conditions | A: GPT-5, context guidance | Bounds autonomy; a rigid quota must permit a blocked outcome. |
| 10 | Make small revisions from failed traces | A/B: GPT-5.1, DSPy | Repairs recurring failures; selection on test data overfits. |
| 11 | Decompose at tool or verification boundaries | B: Yan, provider workflows | Improves control; handoffs add loss and overhead. |
| 12 | State desired behavior positively | B: provider guidance | Clarifies style; retain explicit safety prohibitions. |
| 13 | Use roles for responsibility and audience | B: persona study, providers | Helps tone; prestige does not establish expertise. |
| 14 | Request evidence and concise checks, not visible chain of thought | A: reasoning guidance | Supports inspection; explanations alone do not prove correctness. |
| 15 | Use repeated sampling, debate, or tree search selectively | C on a new task/model | Can help with external verification; shared errors and cost can dominate. |

The persona study tested 162 roles and 2,410 factual questions across four open-model families. Its result does not establish the effect of roles on all current models or writing tasks.

Run prompt optimization as a search experiment. Keep training, selection, and untouched test sets separate. Compare manual fixes with MIPROv2 or GEPA only when the metric is defensible. Inspect cost and unsafe actions as well as the main score.

Source URLs, authors, and dates: [foundation sources](../sources.md). The Prompt Report, https://arxiv.org/abs/2406.06608, Schulhoff et al., 2024 with 2025 revision, Tier 1, supplies a historical taxonomy rather than a current effectiveness league table.
