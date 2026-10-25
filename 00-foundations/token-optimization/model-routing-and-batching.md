# Routing and batching

Choose the configuration with the lowest total cost that meets acceptance and safety gates. A cheaper first answer is insufficient evidence.

## Routing

Use a narrow classifier to route low-risk tasks with checkable outputs, such as labeling a failure category or summarizing an already-selected source. Use a capable model for uncertain planning, security-sensitive review or repeated repair when the baseline supports it.

Freeze router criteria and hold out tasks. Measure wrong-route rate, escalation frequency and human correction time by bucket. Do not let the agent route around approval gates or protected checks.

Illustrative arithmetic: if a cheaper model costs 0.25x and handles 40% of otherwise identical token spend, the theoretical reduction is `0.40 × (1 - 0.25) = 30%`. This excludes router cost, changed output length and retries. It is not a measured saving.

Anthropic's published team tips favor stronger models when they reduce rework. That is a practitioner workflow, not proof that inexpensive models never win. Compare both approaches on paired tasks.

## Batching

Both providers document a 50% token-price discount for applicable asynchronous Batch APIs in the 2026-10-25 research snapshot. OpenAI documents a 24-hour completion window. Confirm eligibility and current provider rules before submission.

Batch independent offline eval judgments, classification jobs or fixed artifact transformations. Do not batch sequential coding actions that require the previous tool result. Use request IDs and reconcile partial completion, refusals and expired requests.

Do not automatically resubmit uncertain side effects. Batch generation should produce staged artifacts, not deployments, external messages or payments. Account for failed requests, retries and storage. Keep privacy controls identical to the interactive path.
