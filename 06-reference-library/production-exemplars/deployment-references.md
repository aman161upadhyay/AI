# Deployment references

Specify data and provider recovery as well as code rollback. All docs were observed on 2026-10-25; living URLs and installed runtime behavior can change.

| Reference | Source date/status | Apply to a release | Limit |
|---|---|---|---|
| [Vercel production checklist](https://vercel.com/docs/production-checklist) | Vercel, updated 2026-08-11 | Security, regions, monitoring, spend, release gates | Paid-plan features require explicit identification |
| [Vercel environments](https://vercel.com/docs/deployments/environments) | Vercel, updated 2026-09-17 | Local/Preview/Production credentials, protected previews, first-target confirmation | Observed docs warn first deployment is Production |
| [Vercel caching](https://vercel.com/docs/caching) | Vercel, updated 2026-06-23 | CDN/ISR/runtime/image cache separation and invalidation | Framework/route behavior must be tested at exact versions |
| [Supabase migrations](https://supabase.com/docs/guides/deployment/database-migrations) | Supabase, living docs | Versioned replay, drift checks, release ownership | A migration plan is not evidence that old-data upgrade passed |
| [Supabase RLS](https://supabase.com/docs/guides/database/postgres/row-level-security) | Supabase, living docs | Real application-role and two-tenant tests | Owner/service-role bypass and grants need separate review |
| [Neon pooling](https://neon.com/docs/connect/connection-pooling) | Neon, living docs | Connection budget, transaction-pool semantics, appropriate admin connection | Do not depend on arbitrary session state across requests |
| [PostgreSQL CREATE INDEX](https://www.postgresql.org/docs/current/sql-createindex.html) | PostgreSQL 18 docs observed | Concurrent indexes, invalid-index recovery, transaction restrictions | Match the installed database version |
| [Stripe webhooks](https://docs.stripe.com/webhooks) | Stripe, living docs | Raw-body signatures, durable intake, deduplication and reconciliation | Browser redirect is not payment truth |
| [Documenso deployment](https://docs.documenso.com/docs/self-hosting/deployment) | Documenso, living docs | Docker/Compose/Railway/Kubernetes, signing/email dependencies | Do not infer Vercel from a JS frontend |
| [Immich architecture](https://docs.immich.app/developer/architecture) | Immich, living docs | Persistent storage and separate web/API/mobile/ML/jobs | Product-specific topology is not a starter requirement |
| [OpenTelemetry primer](https://opentelemetry.io/docs/concepts/observability-primer/) | OpenTelemetry, modified 2026-04-23 | Correlate traces/logs/metrics across requests and workers | Redact secrets and control metric cardinality |

Use [the deployment checklist](../../03-agents/system-design-agent/checklists/vercel-and-nextjs-deployment.md) and [database checklist](../../03-agents/system-design-agent/checklists/database.md). Rehearse worker failure, provider outage, code/schema overlap, and restore before release approval.
