# Report fields

Complete each field with evidence or state NOT TESTED and why. This is a field specification, not a prefilled claim.

## Scope

- Mode, owner, repository/ref and environment.
- Authorized targets, window/rate/budget and prohibited operations.
- Test identities and tenant/role policy.
- Tools, versions, rule revisions and sanitized artifact locations.
- Coverage matrix with PASS, FAIL, NOT TESTED or NOT APPLICABLE.

## Each confirmed finding

- ID and precise title.
- Severity with impact/likelihood reasoning; confidence and evidence type.
- CWE if supported; ASVS chapter/version or agent-risk category.
- File:line and affected ref.
- Attacker prerequisites and input-to-impact trace.
- Affected asset and tenant scope.
- Minimal safe reproduction using synthetic data.
- Expected versus observed result with redacted receipt.
- Smallest complete fix and regression test.
- Retest status, fixed ref and independent reviewer.

## Remaining decisions

List hypotheses with the missing evidence. List hardening advice separately. Record rejected scanner candidates and reasons. Identify release blockers, owner-approved risks with expiry and untested boundaries. Never include live credentials, customer records or unapproved third-party exploit instructions.
