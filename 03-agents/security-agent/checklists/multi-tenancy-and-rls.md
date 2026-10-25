# Verify every tenant boundary

Authenticate the subject, then authorize the object and action using server-derived tenant membership. Next.js middleware is not authorization for server actions, route handlers or direct data access.

| Control | Verification |
|---|---|
| Scope reads and writes near data access | As A, request B's ID through path/query/body, nested objects, batch routes and downloads; require no disclosure or mutation |
| Derive tenant/role from verified authority | Forge tenant headers and role/owner fields; require rejection or safe ignoring |
| Enable RLS for exposed tables | Inspect schema coverage and run SELECT/INSERT/UPDATE/DELETE as actual anon/A/B roles |
| Distinguish old-row visibility from new-row validity | Test UPDATE of owner/tenant and INSERT into another tenant; inspect effective USING and WITH CHECK rules |
| Test policy composition | Add multiple permissive/restrictive policies in the replica; verify their combined effect matches the intended predicate |
| Avoid privileged-role false confidence | Compare ordinary roles with table owner, superuser and BYPASSRLS; document bypass paths |
| Protect Supabase service role | Keep key server-side; inspect browser bundles and server code that uses it; require explicit app authorization before privileged queries |
| Review views and functions | Exercise views and security-definer functions with A's token; verify execution identity, grants and constrained search path |
| Scope derived resources | Warm B's cache; run A's retrieval, storage download, realtime subscription and queued export; B's canary must remain absent |
| Verify indirect ownership | Test invitations, transfers, deleted memberships and stale tokens; require policy recalculation |

PostgreSQL can reuse USING as WITH CHECK when the latter is omitted in applicable policies. Absence of an explicit WITH CHECK clause alone is not proof of a vulnerability. Demonstrate an unauthorized new-row state under the effective policy.

`FORCE ROW LEVEL SECURITY` changes owner handling but does not constrain superuser/BYPASSRLS behavior. Recheck deployed PostgreSQL semantics. The research verified Supabase's guide, not a successful fetch of the PostgreSQL manual.
