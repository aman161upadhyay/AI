# Data-model contract

Document the schema and the rules that protect each access path.

| Section | Required content |
|---|---|
| Ownership | Principal types, tenants, membership/revocation, tenancy strategy and rationale |
| Entities | IDs, tenant keys, attributes/types, relationships, lifecycle states |
| Invariants | Non-null, foreign keys, tenant-scoped uniqueness, checks, deletion behavior |
| Transactions | Atomic business operations, concurrency conflicts, isolation/locking needs |
| Authorization | Principal/action/resource matrix; server-derived scope; grants/RLS/functions/bypass roles |
| Queries | Named filters, joins, sorts, bounded pagination, expected row counts |
| Indexes | Query-to-index map, write/storage trade-off, representative plan verification |
| Retention | Sensitive fields, audit needs, erasure, backups, object/search copies |
| Migration | Clean replay, old-data upgrade, expand/backfill/switch/contract, locks and resumability |
| Connections | App/worker/admin/migration roles, pool budget, transaction-local context |
| Tests | Two-tenant read/write/export/search/job/storage negatives, tenant reassignment, revoked membership |

Attach SQL or the repository's actual schema language. A diagram alone is insufficient. Never claim that an ORM's generated types enforce tenancy.
