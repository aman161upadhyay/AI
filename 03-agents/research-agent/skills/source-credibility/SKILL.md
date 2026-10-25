---
name: source-credibility
description: Assess a source's suitability for a specific research claim through lateral checks, origin tracing, and explicit scoring.
---

# Assess claim-relative credibility

Use when accepting a source into the evidence set or when a consequential claim depends on unfamiliar material.

1. Write the atomic claim and the decision consequence. Identify whether the source is evidence of an observation or only of what its author says.
2. Confirm identity, relevant expertise, date, version, and access status. Do not score a snippet as a read source.
3. Read laterally. Check publisher ownership, relevant accountability, and independent descriptions before trusting the page's self-description.
4. Trace the assertion to the original record. Assign an `origin_family_id`. Reprints and summaries retain that origin.
5. Inspect methods, population, units, uncertainty, and applicability. Check corrections or retractions for consequential research.
6. Apply `rubric.md`. Record unknown dimensions as unknown. Hard rejection gates override totals.
7. Record incentives and the claim-relative tier. Official documentation can establish the issuer's own behavior. It cannot independently establish superiority.
8. Return accept, qualified-use, discovery-only, or reject with a short reason and the missing check.

Return source ID, claim ID, five dimension scores, total or unknown, tier, origin family, conflicts, relevant locator, disposition, and next verification action.

Never turn a credibility score into a probability of truth. Do not invent independent confirmation to satisfy a threshold.

Basis: SIFT, CRAAP, Stanford lateral-reading findings, and PRISMA bias reporting. Sources and limits are in `../../sources.md`. The numeric policy is repository-authored.
