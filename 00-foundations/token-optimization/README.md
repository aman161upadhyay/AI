# Token optimization

Optimize cost per accepted task, not tokens per first answer. Shorter context can reduce irrelevant input, but lost requirements can increase retries and human repair.

| File | Use |
|---|---|
| [FOR-AMAN.md](FOR-AMAN.md) | Inputs, access and paired experiments to run. |
| [principles.md](principles.md) | Mechanisms, expected effects, evidence and failure conditions. |
| [prompt-caching.md](prompt-caching.md) | Provider semantics from the 2026-10-25 research snapshot. |
| [context-compaction-and-subagents.md](context-compaction-and-subagents.md) | Handoffs and parent-versus-total cost. |
| [model-routing-and-batching.md](model-routing-and-batching.md) | Route selection and asynchronous work. |
| [measuring-cost.md](measuring-cost.md) | Accounting fields, formulas and experimental protocol. |
| [checklist.md](checklist.md) | Run-level operating checks. |
| [sources.md](sources.md) | Source records and limits. |

## Known gaps

These are source-backed mechanisms and proposed experiments, not measured savings on Aman's tasks. Prices and API fields require a live model/SDK check before use. No universal compaction percentage or cheapest routing policy was established.
