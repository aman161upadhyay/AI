# Study one subsystem per exemplar

Read implementation paths, not just framework names. Snapshot 2026-10-25. These observations establish dependencies and study targets, not complete authorization audits.

| Exemplar | Database and auth evidence | Deployment lesson | Start reading | License caveat |
|---|---|---|---|---|
| [Supabase](https://github.com/supabase/supabase) | SQL policies/grants and GoTrue JWT integration; not one ORM | Studio deployment is not the complete backend | `docker`, `apps/docs`, `examples` | Apache root; component repositories and assets separate |
| [Payload](https://github.com/payloadcms/payload) | Postgres adapter uses Drizzle; collection access functions; RLS not assumed | Node/Next host still needs database/files | `packages/db-postgres`, `packages/payload`, `test` | MIT root; inspect dependencies/assets |
| [Trigger.dev](https://github.com/triggerdotdev/trigger.dev) | Prisma schema with organization/project/environment; environment tokens separate from web auth | Job compute is not a Vercel request | `internal-packages/database/prisma/schema.prisma`, `apps/webapp`, `packages` | Apache root; inspect file notices |
| [Documenso](https://github.com/documenso/documenso) | Postgres/Prisma, generated Kysely types, teams/organizations; `packages/auth`; current sessions not audited | Docker/Compose/Railway/Kubernetes plus signing and email | `packages/prisma/schema.prisma`, `packages/auth`, `apps/remix` | AGPL; link/study, no permissive import |
| [Immich](https://github.com/immich-app/immich) | Postgres/Kysely, Redis/BullMQ; per-user ownership, RLS not audited | Persistent originals/database and separate ML workers | `server`, `mobile`, `machine-learning`, `e2e` | AGPL; link/study |
| [PostHog](https://github.com/PostHog/posthog) | Django transactional models versus ClickHouse events; org/project auth requires path review | Hobby Docker is not evidence of supported scaled production | `posthog`, `products`, `rust` | MIT core; `ee/` separate |
| [Twenty](https://github.com/twentyhq/twenty) | Postgres/TypeORM; workspace schema design not fully traced; Passport/JWT | Separate server/worker/Postgres/Redis | `packages/twenty-server`, `packages/twenty-front` | AGPL plus commercial/other exceptions |

Inspect a path that implements the behavior and a test that exercises its failure. Record SHA, versions, license, and observation date before deriving an eval. Do not copy AGPL/commercial patches into a permissive training or prompt corpus.

Use the [full web catalogue](../../../06-reference-library/production-exemplars/web-apps.md) for remaining apps, uncertainty, and deployment scope.
