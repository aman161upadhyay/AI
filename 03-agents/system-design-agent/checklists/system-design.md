# Application system-design checklist

Use the categories below before implementation. Evidence comes from the first-party docs and exemplar inspection in [sources](../sources.md). This checklist is original synthesis.

- [ ] Product: actors, critical journeys, acceptance tests, sensitivity, tenants/users/requests, latency/availability, RPO/RTO, cost ceiling, non-goals; unconfirmed values labeled.
- [ ] Data model: ownership, IDs, relationships, constraints, lifecycle, retention, deletion, audits, query/index map, transaction boundaries, migration plan.
- [ ] Authentication: identity provider/session mechanism, account linking, expiry/revocation, recovery, MFA; separate humans, service accounts, API keys, integration OAuth.
- [ ] Authorization: principal/action/resource matrix; server-derived membership; read/write/export/search/jobs/storage checks; admin bypass; two-tenant negative tests.
- [ ] API: typed/OpenAPI contract, input validation, errors, pagination, idempotency, deadlines, rate limits, compatibility, webhook behavior.
- [ ] Jobs: queue/schedule, tenant scope, attempt limits, retry classification/backoff, concurrency, cancellation, terminal failures, reconciliation.
- [ ] Caching: key, owner scope, TTL/staleness, invalidation, outage behavior; personalized content excluded from shared public caches.
- [ ] Files: object storage, signed permissions, key ownership, size/type limits, quarantine when relevant, retention/deletion and metadata consistency.
- [ ] Email: verified sender/domain, authentication DNS, transactional versus marketing consent, bounces/rate limits, captured nonproduction mail.
- [ ] Payments: entitlement source, checkout/portal, raw-body webhook signature, deduplication, event ordering, reconciliation/refunds, sandbox nonproduction.
- [ ] Observability: redacted structured logs, traces through jobs/providers, journey metrics and alerts, low-cardinality metric labels.
- [ ] Deployment: frontend/API/worker/database regions, runtime, preview isolation, secret references, health gates, migrations, staged release, DNS/TLS, rollback.
- [ ] Recovery: backup retention, timed restore, code/schema compatibility, provider-side effects, feature disable, named operator.
- [ ] Cost: baseline/peak compute, database/storage, egress, queues, logs, APIs; quota/spend alerts, tenant limits, degradation behavior.
- [ ] Security handoff: assets/boundaries/endpoints, privileged actions, external inputs, threat assumptions, unresolved risks and review requests.
- [ ] Restraint: modular monolith/managed baseline; a named measured trigger for each proposed future split.
