---
name: architecture-review
description: Reviews application architectures and material design changes against requirements, tenant boundaries, failure recovery, deployment, and cost. Use for design reviews and ADR changes. Does not deploy infrastructure or perform active security testing.
---

# Review an application architecture

## Inputs

Request the requirements, current diagram, data model, API contract, deployment plan, accepted ADRs, and authorized checks. Ask for exact versions and a pinned repository revision. Do not request secret values.

## Procedure

1. Identify the intended change and affected critical journeys. Separate facts, assumptions, and missing evidence.
2. Map each requirement to a component, data flow, and acceptance test. Stop a dependent recommendation when a missing constraint could invalidate it.
3. Trace authentication to server-derived membership and resource authorization. Follow scope through queries, jobs, caches, search, storage, and exports.
4. Read [the system checklist](../../checklists/system-design.md). Mark required, deferred with reason, or not applicable. Read [database checks](../../checklists/database.md) for data changes and [deployment checks](../../checklists/vercel-and-nextjs-deployment.md) for that stack.
5. Test the design mentally against timeout-after-success, duplicate/out-of-order webhook, worker death, membership revocation, stale cache, and partial rollout. Run only approved nonproduction checks.
6. Compare the proposed complexity with the existing/simple alternative. Require a named constraint or measured trigger for an added service.
7. Report located findings by severity. Do not invent issues to fill a quota. Keep uncertain concerns separate from confirmed violations.
8. Prepare security-agent questions for unresolved trust-boundary and privileged-operation risks.

## Output

Return scope/revision, findings, accepted trade-offs, missing evidence, checks run/results, and handoff. Each finding includes location, violated requirement, evidence, impact, confidence, correction, and validation. Record owner and approval needed for consequential fixes.

## Stop rules

Stop before production actions, paid resources, active attacks, deletion, or external writes without scoped authorization. Do not change tests or permissions to make the architecture pass. Report blocked checks explicitly.
