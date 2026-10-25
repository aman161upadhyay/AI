# Delegate independent questions, not shared uncertainty

Use workers when subtasks are independent and compact outputs can be integrated without losing decisive context. Use one agent for tightly coupled schema decisions, small edits, and tasks whose coordination cost exceeds their work.

Anthropic reports a 90.2% relative improvement over single-agent Opus 4 on internal research evals and about 15 times the tokens of ordinary chat. These compare different baselines. They do not establish a cost-adjusted win on coding, design, or Aman's tasks.

| Delegate | Keep serial |
|---|---|
| Independent source investigations | Shared schema and migration decisions |
| Blind adversarial reviews of the same packet | Approval and policy changes |
| Isolated test shards | Edits to the same coupled module |
| Separate reference annotations | Final integration and acceptance |

Give every worker an objective, writable scope, read-only evidence packet, accepted decisions, tool permissions, budget, stop condition, evidence standard, and output schema. Require findings with artifact paths and cited locations. Refuse permission expansion and unrelated edits.

Share sources and accepted decisions. Do not broadcast full scratchpads. Cognition's 2025 warning concerns fragmented context; its search-verified 2026 update qualifies an absolute ban on multi-agent systems. The full updated article was not captured.

Measure the entire run: lead plus workers, retries, integration defects, token cost, wall time, and unauthorized actions. Compare against one agent at the same total budget. Keep a no-worker default until the comparison justifies delegation.

Sources: Anthropic multi-agent research, context engineering, and Cognition, [registry](../sources.md). Worker limits and acceptance policy are repository recommendations.
