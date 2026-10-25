# Mechanisms and limits

The evidence supports reducing repeated input and unnecessary work. It does not establish one savings percentage across agent workloads. Source IDs refer to sources.md. Numeric examples below are arithmetic, not experiments.

| Principle | Mechanism | Expected effect | Evidence | When it backfires |
|---|---|---|---|---|
| Keep stable prefixes | Place reusable policy and schemas before changing task state; serialize deterministically. | Eligible prefix tokens use cache-read rates when a hit occurs. | C1, C2, M1. | Irrelevant stable context still costs tokens and attention; cold writes can cost more. |
| Search before reading | Locate a symbol and read relevant ranges. | A 200-line payload instead of 2,000 comparable lines removes about 90% of that read, not task cost. | A1, T1. | Overly narrow reads miss callers or invariants and cause repair. |
| Bound tool results | Filter, paginate and return concise evidence with full logs external. | A 2k-token summary instead of a 20k log removes 90% of that result's payload. | T1. | Missing exit codes or causal errors can conceal a failed check. |
| Load skills on demand | Expose name/description first, body second, references last. | Smaller startup context and less irrelevant instruction. | A1, H1. | Poor descriptions prevent discovery; repeated loading can offset savings. |
| Compact operational state | Replace obsolete conversation with decisions, constraints and artifact pointers. | Less replayed history; no established universal saving. | A1, M1, H2. | Summary cost, cache disruption and omitted criteria increase rework. |
| Separate unrelated tasks | Start a new session with approved durable state. | Removes irrelevant history from subsequent calls. | H2, H3. | A handoff without permissions or errors causes repeated work. |
| Isolate verbose exploration | Give workers bounded questions and collect evidence summaries. | Lower parent context; total tokens may rise. | A1, H4. | Duplicate exploration and per-worker bootstrap overwhelm the benefit. |
| Route routine work | Assign bounded low-risk classification to a cheaper model. | Lower unit cost if pass rates and retries remain comparable. | H3; local synthesis. | Routing errors or stronger-model repair make accepted-task cost higher. |
| Use strong models where needed | Avoid repeated failed planning or repair. | Fewer attempts can offset a higher token price. | H5, practitioner guidance. | Easy tasks receive expensive reasoning without quality gains. |
| Batch independent offline work | Use provider asynchronous APIs where latency permits. | Applicable Batch APIs document a 50% token-price discount. | B1, B2. | Dependent live turns cannot wait; expired jobs and retries reduce gains. |
| Use structured outputs | Validate machine-consumed shape and handle refusals/incomplete output. | Fewer formatting retries; semantic quality still needs evaluation. | O1. | Large schemas and retrying valid refusals waste work. |
| Stop no-progress loops | Enforce global caps and repeated-failure detection. | Reduces tail cost from ineffective retries. | H1; local threshold policy. | Caps set below a useful verification reserve create avoidable escalation. |

Measure each mechanism separately. Do not add percentages from payload examples to provider cache discounts. An input/output ratio reported by Manus describes Manus's workload, not a constant for coding agents.
