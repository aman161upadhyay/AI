# Vercel and Next.js deployment

Verify the installed Next.js/runtime version. Do not apply old caching or rendering defaults by memory. Sources: Vercel production/environments/caching, Neon, Supabase, Stripe in [sources](../sources.md). Snapshot 2026-10-25.

- [ ] Pin Node, package manager, Next.js, adapters, and lockfile; set monorepo root/build/output; CI runs type/lint/tests and production build.
- [ ] Classify static, ISR, authenticated dynamic, streaming, webhook, and upload routes. Record cache/render behavior and inspect deployed headers.
- [ ] Verify runtime dependency compatibility before Edge selection; account for database access, regions, and APIs.
- [ ] Place compute near database and dominant providers; record data residency and cross-region latency.
- [ ] Separate Local/Preview/Production credentials; validate required variables; no secrets in `NEXT_PUBLIC_*`; redeploy when required.
- [ ] Confirm target before the first deployment. Observed environment docs warn that the first project deployment is Production.
- [ ] Use isolated preview databases/branches or synthetic isolated tenants. Protect previews; never grant production service-role/database credentials.
- [ ] Use sandbox payments, captured email, nonproduction OAuth callbacks; disable preview cron/external writes by default.
- [ ] Budget pooled clients across functions, previews, and workers. Use a controlled appropriate migration connection.
- [ ] Run migrations through one release job; require destructive-change approval; keep rollback-compatible schema windows.
- [ ] Explicitly test CDN/ISR/runtime/browser cache ownership, tenant isolation, invalidation, stale reads, and revalidation failure.
- [ ] Put durable jobs, persistent sockets, and long agent loops on suitable durable infrastructure. Do not assume work survives an HTTP response.
- [ ] Use signed object uploads for large files. Verify exact-plan body/duration/memory limits; ephemeral function storage is not durable user storage.
- [ ] Verify CSP/headers, cookies, rate limits, abuse controls, and raw-body webhook signature handling.
- [ ] Connect traces/errors/uptime and critical-journey probes; audit logs for secret leakage.
- [ ] Set spend, egress, logging, image, and retention budgets; identify features that require paid plans.
- [ ] Verify domain/TLS, preview protection, OAuth allowlists, sender DNS; smoke-test login, tenant switch, upload, webhook, durable job on target.
- [ ] Rehearse promotion, rollback, feature disable, restore, and provider outage. Code rollback cannot undo data/provider changes.
