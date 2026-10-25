# Requirements to security handoff

Run this loop on a pinned repository revision. Keep design output separate from production changes.

| Phase | Work | Gate / artifact |
|---|---|---|
| 1. Requirements | Inspect existing implementation. Ask up to eight blocking questions. Record actors, journeys, scope, sensitive data, SLO/RPO/RTO, budget, non-goals | Owner confirms requirements or explicitly accepts labeled assumptions |
| 2. Data model | Define tenancy, principals, membership, constraints, lifecycle, transactions, retention, named queries, indexes, rollout | Data model and principal/action/resource matrix; negative tests for two tenants |
| 3. API contract | Define typed/OpenAPI requests, policy references, errors, pagination, idempotency, webhooks, limits | Every private operation traces to an ownership rule |
| 4. Deployment plan | Place compute/database/workers; isolate previews; inventory secret references; plan migration/rollback/restore and spend alerts | No production credential in previews; bounded connection and side-effect budgets |
| 5. ADR | Record consequential choices and rejected simpler options after cross-checking artifacts | Tenancy/auth/database/jobs/hosting decisions have evidence and reversal triggers |
| 6. Threat model | Map assets, boundaries, attacker capabilities, abuse paths, controls, residual risks | Explicit security-agent review packet; unresolved risks have owner and test |
| 7. Coding handoff | Order bounded tasks and map each to acceptance criteria and approvals | Implementation plan preserves code/schema compatibility |
| 8. Verify and deliver | Review artifact consistency and run only authorized checks | Results distinguish observed, proposed, executed, passed, failed, and blocked |

ADRs may begin during earlier phases. Finalize them after checking that the API and deployment plan implement the same tenancy and failure model.

## Stop and recovery rules

Stop a dependent decision when tenant scope, sensitive-data handling, or a recovery target is unknown. Ask the owner to answer or explicitly accept an assumption. Do not quietly choose a permissive default.

Stop before paid resources, production changes, or destructive actions without scoped approval. If a tool fails, record the error and remedy. Retry only with a changed approach or new evidence. Suggested local limit: two unsuccessful attempts at the same step.

On budget exhaustion, save requirements version, accepted decisions, unresolved contradictions, evidence paths, pending approvals, and exact next checks. Resume from these artifacts in a clean context.

## Threat-model handoff contract

Provide the security agent with the pinned commit, diagrams, entry points, data classifications, principal/action/resource matrix, privileged roles, policy/function definitions, provider integrations, deployment boundaries, and negative tests. Ask for located findings with safe reproductions and separate confidence/impact.

Request specific review of authentication/session lifecycle, tenant isolation through caches/jobs/search/storage, upload quarantine, SSRF, input injection, signed webhook replay, dependency/skill supply chain, and secret scopes. The system-design agent does not perform active attacks by inference from this handoff.
