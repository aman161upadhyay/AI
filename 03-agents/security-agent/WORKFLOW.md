# Review loop

1. Establish authorization. Record mode, ref, target, budget, forbidden actions and approver. Missing active-test scope blocks execution, not authorized reading.
2. Build a threat model. Inventory entry points, service identities, data stores, tenant boundaries and outbound destinations. Apply STRIDE at each tool boundary. Record attacker control and business impact.
3. Review context and changes. Follow callers through server handlers, policy helpers, database roles, caches, exports and background jobs. Compare with the relevant checklists. A UI gate or middleware redirect is not object authorization.
4. Test in isolation. Inspect scripts first. Pin scanner/rule versions. Use synthetic identities and negative tests as well as valid requests. Save redacted receipts and distinguish scanner candidates from confirmed effects.
5. Report. Use `skills/security-review/report-template.md`. Keep unverified hypotheses separate. Preserve rejected candidates with reasons so false-positive filtering remains auditable.
6. Verify a fix. Require a test that fails before the patch and passes afterward. Replay the same exploit path and adjacent variants. Verify legitimate behavior remains available. An independent reviewer approves closure.

Stop on scope changes, unknown network destinations, permission errors, control-plane changes or exhausted budgets. Capture a sanitized checkpoint and request an owner decision. A tool failure is NOT TESTED, never PASS. Do not bypass a failing control to finish a scan.

Use `skills/security-review/severity-rubric.md` for impact and likelihood. Block unresolved exploitable critical/high findings unless a named human accepts time-bounded risk. Do not convert a scanner severity directly into a business severity.

For design consultations, replace observed reproduction with an abuse scenario and an acceptance test. For hunts, maintain a route-by-role coverage matrix. For differential reviews, distinguish introduced defects from relevant pre-existing issues.
