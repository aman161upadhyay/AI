# Credibility scoring

Score suitability for the exact claim from 0 to 4 in each dimension. Unknown is a separate state, not a zero or an average.

| Dimension | 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|---|---|
| Authority | Unverifiable identity | Named, no relevant record | Relevant experience | Accountable expert or institution | Direct responsible authority or expert with strong relevant public record |
| Directness | No evidence or false reference | Untraceable assertion | Secondary account with original identified | Original document, data, or code | Original evidence with exact passages and auditable records |
| Method | Invalid or contradicted | Unsupported anecdote | Method with major gaps | Appropriate method and limits | Auditable validation appropriate to the claim |
| Currency and fit | Wrong period or definition | Materially stale | Major qualification needed | Appropriate period and scope | Exact version, period, and population checked |
| Independence | Deceptive undisclosed conflict | Promotion without adequate disclosure | Disclosed interest or shared dependency | Meaningfully independent for this claim | Independent origins and relevant conflict checks |

| Total | Disposition |
|---|---|
| 17-20 | Preferred evidence, subject to entailment verification. |
| 13-16 | Usable with named limitations. Corroborate consequential claims. |
| 9-12 | Context or qualified attribution. Never sole support for a recommendation. |
| 0-8 | Exclude from substantive support. |
| Any unknown dimension | No high-confidence total. Record missing evidence. |

Reject substantive support regardless of total when identity or references are fabricated, the supporting passage is inaccessible, the version is wrong, a quotation is unverifiable, evidence is manipulated, or a material retraction defeats the claim.

Tier 1 means original evidence or authoritative documentation for the issuer's own behavior. Tier 2 means accountable reporting or synthesis with traceable references. Tier 3 means discovery-only material such as snippets or unattributed aggregation. A forum post can establish that person's stated experience, not prevalence.

Worked example: OpenAI's deep research page can support “OpenAI acknowledges hallucinations.” The research draft scores that claim 4 + 4 + 3 + 4 + 2 = 17. The same page cannot establish “this is the best researcher for Aman.” That claim needs workload-specific evaluation and independent comparison.

These thresholds are proposed consistency aids, not validated truth scores. Sources: CRAAP and SIFT in `../../sources.md`.
