---
name: authz-test-matrix
description: Build and verify an authorization matrix across identities, tenants, objects and actions using synthetic staging records.
---

# Test authorization at every entry point

Require endpoint inventory, subject roles, membership policy, object ownership, staging scope and synthetic fixtures. Stop for unknown expected policy; do not infer authority from UI visibility.

1. Create anonymous, A-member, B-member, A-admin and explicitly scoped global-admin identities.
2. Create A/B-owned objects and canary data. Include nested objects, storage and queued exports.
3. Enumerate read/create/update/delete, list/search, bulk/export, invitations and ownership transfer.
4. For each operation record subject, tenant, object, action, expected policy result, actual status, returned fields and side effects.
5. Replay valid A requests as B and anonymous. Alter IDs in every location; alter tenant/role/owner fields. Test stale membership and revoked role.
6. Check data and side effects, not only HTTP status. A 403 that mutates data fails. A 404 may be an acceptable non-disclosure response.
7. Run RLS tests with real ordinary roles. Test effective USING/WITH CHECK constraints and privileged view/function paths separately. Do not infer a defect solely from an omitted explicit WITH CHECK.
8. Warm caches and complete jobs before querying as another tenant. Check storage links and retrieval namespaces.
9. Verify secure twins preserve legitimate A access while denying B. Save sanitized receipts and regression criteria.

Production queries and cross-tenant customer access are outside default scope. Report gaps and permission errors rather than switching to service-role credentials.
