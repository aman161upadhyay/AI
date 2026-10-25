# Database checks

Test using actual application roles and representative data. Table ownership or service-role access can bypass an otherwise plausible policy.

- [ ] Choose shared tables, schema-per-tenant, or database-per-tenant; state isolation, migrations, routing, backup, residency, and connection consequences.
- [ ] Put tenant ownership on private entities; define tenant-scoped uniqueness and constraints that prevent cross-tenant relationships.
- [ ] Define lifecycle/check constraints, foreign keys, delete rules, audit needs, retention, and erasure.
- [ ] Separate application, worker, migration, read-only, and admin roles. Ordinary requests must not run as owner/superuser.
- [ ] Restrict grants and enable RLS on browser-exposed tables; cover reads and writes. Review views, functions, storage, and realtime separately.
- [ ] Test anonymous, member, nonmember, suspended member, and admin against two tenants. Test insert/update `WITH CHECK` and tenant reassignment.
- [ ] Review owner/service-role bypass. Give `SECURITY DEFINER` functions a safe explicit search path and schema-qualified objects.
- [ ] In transaction pooling, establish request claims transaction-locally through an audited mechanism. Do not depend on a previous request's session state or untrusted `search_path`.
- [ ] Budget connections across instances/workers/previews; separate appropriate admin/migration connections; test pooled reuse under alternating tenants.
- [ ] Index actual filters/joins/sorts and RLS predicates. Inspect `EXPLAIN (ANALYZE, BUFFERS)` safely on representative row counts; account for writes/storage.
- [ ] Bound page sizes and statement/lock waits. Prevent N+1 and unbounded exports; move large exports to scoped jobs.
- [ ] Version schema/policy changes; test clean replay and previous-release upgrade; prevent unreviewed production ORM `push`.
- [ ] Use expand/backfill/switch/contract for breaking changes. Serialize migrations; cap lock waits and make backfills resumable.
- [ ] Put concurrent index creation outside transaction blocks. Check for invalid indexes and define repair after failure.
- [ ] Encrypt connections, rotate secrets, keep privileged keys server-only, redact SQL parameters.
- [ ] Isolate preview data/credentials; confirm that migrations and test cleanup cannot target production.
- [ ] Set backup/PITR requirements and retention; time a restore drill; reconcile deletion with backups and derived stores.
- [ ] Monitor connections, lock waits, long transactions, query latency, pool waits, storage, and replication lag when applicable.
- [ ] Set noisy-neighbor limits and measured triggers before partitioning, replicas, or sharding.

Sources: Supabase RLS/migrations, Neon pooling, PostgreSQL CREATE INDEX, inspected application schemas in [sources](../sources.md). Snapshot 2026-10-25. No local database validation was executed for this pack.
