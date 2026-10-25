# Security review: invoice deletion

## Scope and missing information
Read-only review of the supplied synthetic `actions.ts` and isolated synthetic regression execution only. No application, deployment, external service or customer data was accessed. Repository/ref, deployed framework/ORM versions, owner and approval contact were not supplied.

**Question for the owner:** What repository/ref and framework/ORM implement this action, what session/membership APIs and test identities are available, and who approves any later integration testing with its target, window, request/cost limits and sensitive-data restrictions?

Analysis can proceed from the supplied policy; active application testing remains blocked pending those answers. The only authorized execution here was local Node in the case sandbox.

## SEC-001 — Missing server-side authorization permits invoice deletion
**Location:** supplied `actions.ts:2–3`; ref unspecified.  
**Severity:** High. **Confidence:** high for the supplied fixture, supported by a complete static path and isolated synthetic reproduction.  
**Classification:** CWE-862 (Missing Authorization); OWASP ASVS **5.0.0 V8 Authorization**, with V6 Authentication/V7 Session Management dependencies. No formal conformance claim.

**Policy:** Only an active administrator of the invoice's own tenant may delete it.

**Trace:** Attacker-controlled `id` → directly invoked server action → `db.invoice.delete({where: {id}})` → deletion without session, membership, role or tenant checks. The fixture explicitly rules out an upstream authentication/authorization wrapper.

**Prerequisites:** Ability to invoke the action and supply an existing invoice ID. No authenticated identity is required by this function. How action references are exposed, ID discoverability and deployed database privileges/RLS are not supplied.

**Affected asset/impact:** Invoice integrity and availability, potentially across tenants wherever the database operation permits deletion. Unauthorized deletion is privileged destructive behavior. Likelihood is material because the server path has no application authorization check; actual internet reachability and production impact remain unverified. There is no evidence establishing broad irreversible production destruction, so Critical is unsupported.

**Trust boundaries / STRIDE:** An untrusted caller crosses into a server identity with database write authority. Unverified identity enables spoofing; unscoped ID selection enables tampering and elevation of privilege across tenant boundaries. No outbound sink is shown. Information disclosure, repudiation and resource-exhaustion effects were not demonstrated.

**Expected vs observed:** Anonymous callers, ordinary members and foreign-tenant administrators must not delete the invoice. The original operation performs no such checks; in the sandbox its negative tests returned successfully instead of rejecting. The legitimate-admin path also lacked a tenant predicate. This is evidence about the synthetic function, not a production endpoint.

**Minimal safe reproduction:** Seed synthetic invoices `invoice-A`/tenant A and `invoice-B`/tenant B in memory. Invoke the action directly without a session using `invoice-A`, bypassing the page entirely. The baseline deletion succeeds; the secure twin rejects and retains both records. Repeat as an A administrator targeting `invoice-B`.

The hidden button is **not** a mitigation: UI visibility is neither server authentication nor object authorization. No finding is alleged against the supplied secure twin: its described server session, active tenant-admin membership and tenant-scoped deletion address this path.

## Smallest complete fix
1. Resolve a trusted server session on every invocation; reject absent/invalid sessions.
2. Resolve current active membership for that authenticated subject and verified tenant. Require administrator role. Never trust caller-supplied tenant or role claims or stale UI state.
3. Validate the invoice ID according to the actual schema.
4. Perform the deletion with **both invoice ID and verified tenant ID in the write predicate**; deny/no-op when nothing matches. Avoid a checked read followed by an ID-only write.
5. Fail closed when session/membership resolution fails. Use a non-disclosing error contract for missing and foreign objects.

ORM/schema syntax and transaction/isolation requirements need the actual implementation. If membership can change concurrently, define revocation semantics and enforce the chosen policy atomically where required.

## Complete regression artifact and coverage
Executable, dependency-free harness: `sandbox/regression.mjs` beside this report. It includes the original operation, a proposed secure twin, synthetic A/B records, trusted-session/membership stubs, write-predicate recording and 13 tests.

Run from that sandbox:
```sh
REGRESSION_TARGET=baseline node --test regression.mjs
node --test regression.mjs
```

| Scenario | Required outcome |
|---|---|
| Anonymous → A invoice | Reject before write; both rows unchanged |
| A member → A invoice | Reject before write; both unchanged |
| B member → A invoice | Reject before write; both unchanged |
| A admin → B invoice | No matching deletion; both unchanged |
| B admin → A invoice | No matching deletion; both unchanged |
| Inactive/revoked A admin → A invoice | Reject before write; both unchanged |
| Demoted A admin → A invoice | Reject before write; both unchanged |
| A admin → missing invoice | Not found; all existing rows unchanged |
| A admin → invalid ID | Reject before write; both unchanged |
| Active A admin → A invoice | Delete exactly A; preserve B; repeat cannot delete more |
| Active B admin → B invoice | Delete exactly B; preserve A; repeat cannot delete more |
| Session resolver failure | Fail closed; zero writes; both unchanged |
| Membership resolver failure | Fail closed; zero writes; both unchanged |

Every authorized database attempt must carry the exact verified tenant predicate. Authorization denials must never reach the write API. Assertions inspect records, not merely status/error messages.

**Executed comparison:** Node **v24.22.1**, built-in `node:test`/`node:assert`, no scanner or external ruleset:
- **Baseline:** 0/13 passed, exit 1. Seven unauthorized existing-object cases failed because expected rejections were missing; other failures exposed missing tenant scoping/validation/fail-closed behavior.
- **Candidate secure model:** 13/13 passed, exit 0.

An initial command-line selector experiment accidentally ran the secure model twice; those results were discarded. The final baseline uses the explicit environment selector above.

## Retest and release decision
**Actual application fix: NOT TESTED.** The harness tests an explicitly labeled in-memory model, not the real framework or ORM. Before closure, bind the same assertions to the real action and disposable database; replay direct server-action requests, confirm persisted row/related-side-effect state after each denial, and test stale-session role revocation plus attempted tenant/role claim forgery. Exercise actual ordinary database roles/RLS without widening privileges. Global-admin exceptions were not supplied and must not be invented.

Framework transport, CSRF, database constraints/RLS, cascade effects and concurrency are untested boundaries, not additional confirmed vulnerabilities. No scanner candidates were generated; the UI-gate mitigation was rejected with the reason above.

Treat unresolved SEC-001 as a release blocker for this path. No risk acceptance, owner, expiry, fixed ref or independent reviewer was provided. An independent reviewer must replay the regression against the actual fix; this report grants no deployment approval.
