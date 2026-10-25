# System-design sources

Research access date: 2026-10-25. This pack contains original summaries, checklists, prompts, and synthetic eval cases. No source implementation or upstream skill was vendored. Tier 1 means first-party docs or an original author's work; Tier 2 means an adopted implementation. Neither tier certifies complete security.

| Title and URL | Author/org | Date | Tier | Contribution / evidence limit |
|---|---|---|---|---|
| [Designing Data-Intensive Applications](https://dataintensive.net/) | Martin Kleppmann; second edition with Chris Riccomini | 2017 first edition; 2026 edition search evidence | 1 | Transactions, replication, recovery trade-offs; fetched homepage does not establish edition-specific chapters |
| [Well-Architected pillars](https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html) | AWS | Living docs | 1 | Requirements, reliability, cost, security; six pillars |
| [Monitoring](https://sre.google/workbook/monitoring/) | Google SRE | Workbook 2018 | 1 | Journey metrics, percentiles, alert quality |
| [Observability primer](https://opentelemetry.io/docs/concepts/observability-primer/) | OpenTelemetry | Modified 2026-04-23 | 1 | Traces/logs/metrics and correlation |
| [Row Level Security](https://supabase.com/docs/guides/database/postgres/row-level-security) | Supabase | Living docs | 1 | Grants, policies, bypass roles, real-role tests; tenant evals |
| [Database migrations](https://supabase.com/docs/guides/deployment/database-migrations) | Supabase | Living docs | 1 | Versioned replay and drift prevention |
| [Connection pooling](https://neon.com/docs/connect/connection-pooling) | Neon | Living docs | 1 | Transaction/session semantics and direct-connection exceptions |
| [CREATE INDEX](https://www.postgresql.org/docs/current/sql-createindex.html) | PostgreSQL | Version 18 docs observed | 1 | Concurrent index transactions, invalid indexes, failure repair |
| [Indexes](https://www.postgresql.org/docs/current/indexes.html) | PostgreSQL | Version 18 docs observed | 1 | Query/index selection and operational cost |
| [Production checklist](https://vercel.com/docs/production-checklist) | Vercel | Updated 2026-08-11 | 1 | Release, regions, cost, security, plan restrictions |
| [Environments](https://vercel.com/docs/deployments/environments) | Vercel | Updated 2026-09-17 | 1 | Preview isolation and first-deployment target caveat |
| [Caching](https://vercel.com/docs/caching) | Vercel | Updated 2026-06-23 | 1 | CDN/ISR/runtime cache ownership |
| [Receive Stripe events](https://docs.stripe.com/webhooks) | Stripe | Living docs | 1 | Raw-body signatures, deduplicated intake, event ordering; payment eval |
| [Idempotent requests](https://docs.stripe.com/api/idempotent_requests) | Stripe | Living docs, search-only | 1 | Retry/idempotency reference; full-page evidence unavailable |
| [AIP-158 Pagination](https://google.aip.dev/158) | Google | Changelog through 2025-07-08 | 1 | Opaque tokens and bounded lists |
| [API-first guidelines](https://raw.githubusercontent.com/zalando/restful-api-guidelines/main/chapters/general-guidelines.adoc) | Zalando | Living source | 1 | Contract review before implementation |
| [Immich architecture](https://docs.immich.app/developer/architecture) | Immich | Living docs | 1 | Worker/web/mobile/ML boundaries and incomplete migration caveat |
| [Documenso deployment](https://docs.documenso.com/docs/self-hosting/deployment) | Documenso | Living docs | 1 | Actual supported deployment forms |
| [Agent Skills specification](https://agentskills.io/specification) | Agent Skills maintainers | Living spec | 1 | Skill frontmatter, portable disclosure |
| [Skill authoring](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices) | Anthropic | Living docs | 1 | Procedure scope, direct references, evaluation-first authoring |

## Implementation sources

Each record below is first-party evidence for its own dependencies and paths. The wider quality assessment uses adoption/activity, not a claim that every access path was audited.

| Title / URL | Author/org | Date | Tier | Contribution |
|---|---|---|---|---|
| [Supabase](https://github.com/supabase/supabase) | Supabase/contributors | 2026-10-25 snapshot | 1 | SQL/auth/infrastructure composition |
| [Payload](https://github.com/payloadcms/payload) | Payload/contributors | 2026-10-25 snapshot | 2 | `packages/db-postgres` manifest, Drizzle adapter, access-function study |
| [Trigger.dev](https://github.com/triggerdotdev/trigger.dev) | Trigger.dev/contributors | 2026-10-25 snapshot | 2 | `internal-packages/database/prisma/schema.prisma`, webapp manifest, durable job study |
| [Documenso](https://github.com/documenso/documenso) | Documenso/contributors | 2026-10-25 snapshot | 2 | `packages/prisma/schema.prisma`, `apps/remix/package.json`, `packages/auth` |
| [Immich](https://github.com/immich-app/immich) | Immich/contributors | 2026-10-25 snapshot | 2 | `server/package.json`, mobile/server/job boundaries |
| [Twenty](https://github.com/twentyhq/twenty) | Twenty/contributors | 2026-10-25 snapshot | 2 | `packages/twenty-server/package.json`, TypeORM/workspace study; full isolation unverified |
| [PostHog](https://github.com/PostHog/posthog) | PostHog/contributors | 2026-10-25 snapshot | 2 | `pyproject.toml`, transactional/analytics split |

License boundaries for these implementations appear in [exemplar patterns](reference/exemplar-patterns.md) and [the production catalogue](../../06-reference-library/production-exemplars/sources.md). Skill procedure and task contract design also derive from [foundation sources](../../00-foundations/sources.md).

Research inputs were `work/research/09-systems-exemplars-and-learning.md` and `01-skills-and-harness-repos.md`. Source captures live outside the public pack under `work/sources/09-systems/` and `01-skills/`. The pack does not rely on access to those workspace paths at runtime.

## Limits

No project was run or deployed. Proposed eval thresholds and scoring weights are local recommendations. ORM dependencies, tenant schema fields, and star counts are not security proof. Match exact runtime/package versions before implementation and record executed checks separately from proposed tests.
