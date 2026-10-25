# Export architecture and authorization review

## Decision and evidence
**Reject the proposed authorization boundary; block release pending isolation verification.**

Facts supplied by `candidate.json` (`inputs.brief`, `inputs.proposed_control`): a user belongs to tenant A; `POST /exports` accepts `organizationId` and `documentIds`; a worker reads documents by ID; exports use `exports/latest.zip`; CDN downloads are cached by path; the route checks login only. The team claims Prisma types prove isolation.

Authentication establishes identity, not permission to export a particular organization's documents. Prisma types do not establish runtime membership, document ownership, worker scope, object access, or cache isolation. No implementation, schema, revision, versions, or tests were supplied. Findings concern the described design, not a demonstrated production exploit.

## Blocking questions
1. Is an organization the tenant boundary, and who may export which documents? Are document-level restrictions or delegated admins involved?
2. What establishes current membership, suspension and revocation, including behavior during an in-progress download?
3. What are data classification, residency, export retention, deletion and audit requirements?
4. What are the pinned revision, schema/migrations, exact Prisma/database/runtime versions, hosting, queue, storage, CDN and connection-pooling configuration?
5. What are maximum document count/bytes, concurrency, completion SLO, availability target and spending ceiling?
6. What are RPO/RTO, backup rules and the operator responsible for restoration?
7. Who owns product/security approval, and which local checks and implementation changes are authorized?
8. Must exports represent a consistent snapshot, and what happens when documents change or access is revoked mid-job?

These questions remain unanswered. The design below is a conditional proposal, not accepted assumptions or permission to implement. Final tenancy mapping, revocation semantics, retention, recovery and infrastructure decisions remain blocked.

## Requirements and trust boundaries
Required journeys: authorized creation, asynchronous generation, status, authorized download, cancellation/expiry. Non-goals: cross-tenant sharing, new hosting services, email/payment integration, and deployment.

```text
Untrusted client → authenticated API → policy + tenant-scoped database
                                  → durable export intent → worker
Worker → scoped document reads → private immutable object
Client → download authorization gateway → private object stream
                     (no shared public cache)
```

Client identifiers are selectors, never authority. Queue messages and object paths are not authorization grants. The worker is a privileged principal with narrowly scoped access; storage and CDN are separate enforcement boundaries.

## Findings and corrections
| Severity/location | Evidence and impact | Correction and validation |
|---|---|---|
| Critical design gap: route | Login-only control accepts caller-selected organization/documents. No resource permission check is described; tenant A could request B's identifiers. High confidence in missing boundary; actual disclosure unverified. | Resolve active membership server-side; enforce export permission and every document's ownership/access. API owner; security approval; two-tenant mixed-ID tests. |
| High: worker | Reads by ID lack stated tenant or principal scope. Queue processing can become a confused deputy. High confidence in insufficient described control. | Load authoritative export intent; constrain all reads by tenant and authorized document set; revalidate revocation. Worker owner; forged-message/revocation tests. |
| High: storage/CDN | Shared `exports/latest.zip` and path-only cache provide no stated tenant/user separation. Overwrites, stale downloads and cross-user disclosure are plausible; actual cache configuration unknown. | Private immutable per-export keys; authorize every download; bypass shared cache. Platform owner; warm-cache A/B and direct-origin tests. |

All three require security review before release. Tenant-prefixed keys alone do not authorize access, and an unguessable export ID is not an access policy.

## Ownership, schema and transactions
Proposed relational contract, conditional on organization equaling tenant:

```text
Membership(tenant_id, user_id, status, export_permission)
  PRIMARY KEY(tenant_id, user_id)
Document(tenant_id, id, ...)
  UNIQUE(tenant_id, id)
Export(tenant_id, id, requester_id, status, object_key,
       idempotency_key, request_hash, expires_at, ...)
  UNIQUE(tenant_id, id)
  UNIQUE(tenant_id, requester_id, idempotency_key)
ExportItem(tenant_id, export_id, document_id)
  PRIMARY KEY(tenant_id, export_id, document_id)
  FK(tenant_id, export_id) → Export(tenant_id, id)
  FK(tenant_id, document_id) → Document(tenant_id, id)
```

Ownership keys are non-null and immutable; foreign keys prevent cross-tenant links. Status transitions are constrained: queued → running → ready/failed/cancelled; expiry denies delivery independently of cleanup. Deletion actions await retention policy; do not cascade-delete audit evidence blindly.

Policy matrix: humans create only with current export permission; status/download/cancel require current permission plus requester ownership unless an explicit sharing policy is approved. Workers claim/update scoped jobs only; migration/admin privileges never serve ordinary requests.

Creation transaction checks active membership, selects all requested documents with tenant and document permissions, rejects the entire request on any mismatch, persists items plus durable dispatch intent atomically. An outbox is one implementation option; no uncommitted job publication. Claim jobs atomically with bounded leases; duplicate execution must not overwrite another export.

Indexes: membership primary key for authorization; document tenant/ID key for selection; export tenant/requester/creation index for bounded listing; status/next-attempt index for dispatch. Verify actual plans and write overhead before finalizing. Database RLS is defense-in-depth if supported, not assumed: review grants, owner/service-role bypass and functions; use transaction-local context under pooling.

## API and worker contract
`POST /exports`: authenticated JSON `{organizationId, documentIds}`; mandatory idempotency key. Validate identifier formats, nonempty unique IDs, configured count/body/byte quotas and rate/concurrency limits. Exact limits await budget answers. Same key/body returns the same export; conflicting body returns 409. Return 202 with opaque export ID and status URL.

`GET /exports/{id}` returns scoped status; `GET /exports/{id}/download` checks current policy and readiness before streaming; cancellation is similarly scoped. Optional listing uses tenant-scoped cursor pagination with a hard cap. Consistent errors: 401 unauthenticated, 404 inaccessible/missing resource without ownership disclosure, 400 invalid input, 409 conflict/not-ready, 429 quota, sanitized 5xx with request ID.

Queue payload identifies the persisted intent, not an arbitrary document list. Worker rechecks policy before reading and publishing, uses tenant-scoped queries, enforces byte/time/concurrency budgets and safe archive entry names, and fails closed on ownership changes. Retry transient failures with bounded attempts/backoff; permanent authorization failures terminate. Lease recovery/reconciliation handles worker death and orphan objects.

Use private keys such as `tenants/{tenant}/exports/{export}/{attempt}.zip`, publish metadata only after successful upload, and deny direct public origin access. Gateway-streamed responses use `Cache-Control: private, no-store`; CDN bypass must be verified. Signed URLs are deferred because bearer access until expiry complicates immediate revocation. Revocation during streaming needs an explicit policy before implementation.

## Decision record, operations and rollout
ADR proposal: retain the existing application/worker boundary; add no service without measured need. Reject login-only checks and global “latest” objects because they fail tenant isolation. Reject synchronous large exports pending evidence they meet bounded latency/size requirements. Evidence is the supplied brief; versions/date/revision unavailable. Consequences: policy checks and private streaming cost more; reconsider delivery architecture only after measured egress/latency pressure and equivalent authorization proof. Rollback disables exports, not restores unsafe behavior.

Expand tenant metadata/constraints, quarantine unverifiable legacy rows, backfill resumably, validate ownership, switch readers/writers, then contract only after compatibility tests. Disable legacy download paths; review existing objects/cache entries for exposure and approved purge. No destructive actions executed.

Checklist disposition: **required** product, data, authentication, authorization, API, jobs, caching, files, observability, deployment, recovery, cost, security handoff and simplicity; details blocked by questions above. **Not applicable** email, payments, webhooks, user uploads, search. Archive creation still requires injection/path-traversal review. Hosting-specific decisions are deferred because no stack was supplied.

## Acceptance and handoff
Proposed, not executed: A cannot create/read/cancel/download B's exports; mixed A/B documents fail atomically; forged queue scope fails; revoked/suspended users fail at enqueue, execution and download; warm A cache followed by B request cannot disclose bytes; direct-origin requests fail; pooled alternating tenants remain isolated. Test idempotency conflicts, duplicate jobs, timeout-after-success, worker death, partial upload, expiry, old/new migration compatibility, quota/performance bounds and restore against agreed targets.

Ordered owners: product answers policy questions; API/data owner implements scoped schema and transactions; worker/platform owners implement durable private delivery; QA executes acceptance checks; security reviewer approves boundaries before staged rollout. Monitor redacted authorization failures, queue age, job failures, orphan objects, egress and quota saturation; never log document contents or download tokens.

Security handoff requests authentication/session lifecycle, tenant isolation, privileged worker/tools, archive injection, SSRF if remote fetch exists, secret scopes and dependency/supply-chain review. Upload quarantine and webhook replay are not applicable unless those inputs are introduced. Provide pinned revision, actual policies and deployment diagram when available.

Only supplied documents and relevant agent instructions/skills/checklists were inspected. No network, application execution, tests or production changes occurred. Release is blocked; no production-readiness claim is made. This output consolidates design artifacts; implementation-ready SQL/OpenAPI and deployment/recovery plans require the missing evidence.
