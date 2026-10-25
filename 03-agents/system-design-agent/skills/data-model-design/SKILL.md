---
name: data-model-design
description: Designs tenant-aware application schemas, constraints, indexes, authorization strategy, and migration rollouts. Use for new entities or changes to ownership, lifecycle, query shape, or schema compatibility. Does not execute production migrations.
---

# Design a data model from requirements

## Inputs

Request current schema/migrations, actors and membership policy, critical operations, named queries, scale assumptions, retention/deletion requirements, runtime/pool configuration, and allowed commands. Ask for sanitized fixtures, not customer records or credentials.

## Procedure

1. State requirements, observed implementation, assumptions, and blocked decisions. Choose the current repository's schema language.
2. Define tenant strategy and principals. Resolve membership server-side. Model human identities separately from service/API/integration credentials.
3. Define entity ownership, IDs, relationships, lifecycle, non-null/check constraints, tenant-scoped uniqueness, and deletion rules.
4. Prevent cross-tenant references explicitly. Use tenant-aware relationship constraints or a tested equivalent; an application filter alone is not evidence of complete isolation.
5. Define atomic operations and concurrency conflicts. Map named filter/join/sort queries to indexes and bounded pagination.
6. Specify roles/grants and RLS where applicable. Review owner/service-role bypass and privileged functions. Do not assume ORM types supply authorization.
7. Specify connection budgets and transaction-local request context. Test alternating tenants on reused pooled connections.
8. Write versioned expand/backfill/switch/contract steps for incompatible changes. Bound locks, serialize migration execution, and make backfills resumable.
9. Specify clean replay and previous-release upgrade tests, concurrent-index failure repair, old/new code compatibility, and restore limits.
10. Complete [database checks](../../checklists/database.md) and [data-model contract](../../templates/data-model.md). Hand unresolved access risks to the security agent.

## Output

Return schema, ownership/access matrix, query/index map, transaction rules, migration/backfill plan, retention plan, and executable acceptance-test specifications. Label plans that were not executed. Include negative read/write/export/search/job/storage cases for two tenants and membership revocation.

## Stop rules

Do not execute schema changes without explicit scoped approval. Do not use production ORM push as an unreviewed release strategy. Stop when tenant or deletion semantics are unresolved. Never broaden credentials or weaken tests to finish.
