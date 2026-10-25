---
name: launch-checklist
description: Prepares an approval-ready launch decision for Product Hunt or Show HN. Use for launch readiness and channel assets. Does not post, solicit votes or change spend.
metadata:
  author: aman-repository-build
  status: unevaluated
---

# Launch checklist

## Inputs
Request the tryable product, approved claims, channel, launch owner, support capacity, release window, tracking test evidence and rollback route.

## Procedure
1. Verify the supplied demo can support the promised task. Mark unavailable checks.
2. Check each public claim against proof and each quote against permission.
3. Recheck the channel's current first-party rules. Record URL and observation date.
4. For Show HN, require maker participation and something people can try. Reduce access friction. Do not substitute a landing page for a tryable product.
5. For Product Hunt, prepare demo assets and a maker explanation. Ask for feedback; never ask for coordinated votes.
6. Confirm completed-action events, attribution windows, deduplication and support ownership.
7. Return Go, Hold or Cancel with blockers. Ask for explicit approval of the exact asset, account, timing and spend cap before any live action.

## Output
Return readiness table; channel-ready draft; proof ledger; measurement plan; support and rollback owners; blocked checks; approval request.

## Checks and stop rules
Hold on broken demos, unknown consent, missing support, unverified critical claims or absent human approval. Halt automated loops after a tool error or duplicate send. No fake accounts, engagement or vote automation.

## References
Read ../../reference/launch-playbooks.md and ../../checklists/publication-review.md.
