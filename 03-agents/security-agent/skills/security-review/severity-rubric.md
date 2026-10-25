# Severity is impact and likelihood, not confidence

| Severity | Decision rule |
|---|---|
| Critical | Practical broad privileged execution, signing-authority compromise, large-scale sensitive tenant compromise or irreversible production destruction |
| High | Demonstrated authentication bypass, sensitive cross-tenant access, significant secret exposure, exploitable injection or unauthorized privileged agent action |
| Medium | Bounded sensitive impact or material additional prerequisites |
| Low | Limited-impact weakness or a defense-in-depth gap |
| Informational | Useful hardening with no demonstrated security violation |

For each finding, state affected assets, scale, attacker access and required conditions. Use CVSS where appropriate, with its version and vector, but do not substitute it for business context.

Confidence records evidence strength: confirmed by isolated reproduction; supported by a complete static path; or unverified hypothesis. Do not report a numerical confidence as a measured probability. Missing tests may raise review priority without proving greater vulnerability severity.

Critical/high release blockers need independent verification. Lower severity does not authorize ignoring a regulatory or explicit contractual requirement.
