# Ceramics booking page — bounded design review

## Integrity gate (before aesthetic judgement)
An invented logo wall fails the evidence requirement and disqualifies its plan as supplied. Remove it; do not replace it with invented testimonials, prices or metrics. The other plan contains no explicit fabricated evidence, but its proposed dates, price and class promise still require approved content before publication.

## Comparison with origin labels withheld
### Response X
Purple gradient hero, three generic cards, invented logo wall.
- Integrity: disqualified by fabricated social proof.
- Task fit: neither the gradient nor the generic grouping has support in this brief; real dates and price are not explicitly prioritized.

### Response Y
Studio photograph beside class promise, dates and price first, one readable action colour.
- Integrity: no explicit fabrication; verify the promise and supply actual commercial data.
- Task fit: the decision information matches first-time adults’ stated need, and photography matches the approved direction.

**Judgement: Y.** This is a task-fit preference, not evidence of higher conversion or release readiness.

**Labels restored:** Response X is Plan A; Response Y is Plan B.

## Intake and questions
| Item | Known fact or boundary |
|---|---|
| Audience and job | First-time adults evaluating a ceramics class before booking. |
| Required information | Real class dates and price, available before booking. |
| Primary task | Select a suitable class and proceed to booking; the actual completion event is not supplied. |
| Visual permission | Warm photography is approved; no particular asset, font or brand palette is supplied. |
| Authorized scope | Compare plans and revise unsupported defaults only; no implementation or external action. |

Questions I would ask Aman:
1. What are the approved class dates, times/time zone, prices/currency, applicable fees and booking terms, and which class-promise copy is substantiated?
2. What is the existing booking flow and confirmed completion event, and what availability states must it support?
3. Which existing brand tokens/components, target platform/widths and rights-cleared studio photograph should this plan use?

These questions block publication or implementation, not this bounded comparison. No commercial values or promises are invented below.

## Choice-to-brief review
| Choice | Decision and reason | Catalogue |
|---|---|---|
| Invented logo wall | Remove outright: unsupported proof, regardless of appearance. | P02 |
| Purple gradient in the ceramics plan | Revise its default hero treatment: there is no brand or brief support here. Prioritize approved photography and decision content instead; do not infer that purple itself is prohibited. | C01, P03 |
| Three generic cards | Replace generic grouping with class/date/price relationships. Cards remain acceptable if actual content warrants them; the number three is not a requirement. | L01, K01 |
| Studio photo and promise | Keep subject-specific imagery and the layout concept. Ask for the actual approved asset and verified promise; do not invent studio attributes or learning outcomes. | P03 |
| Dates and price first | Keep: directly serves the explicit pre-booking information need. | T08 |
| One readable action colour | Keep its semantic role, not an unprovided hue. Pair it with tested on-action text and visible focus. | C05, K09 |
| Type, density, spacing, motion | Neither plan specifies these. Preserve existing system decisions pending evidence; do not introduce a decorative font, cream/terracotta palette or animation as a universal cure. | C02, T01, L04, M01 |

Unrelated-product check: the gradient/three-card/logo-wall package could move unchanged to unrelated marketing pages without helping class selection. The photograph alone is not sufficient differentiation either; actual ceramics content and the date/price decision order establish the task connection. Familiar controls need not be made unusual.

## Revised token/layout plan
Use Plan B as the direction. Repair Plan A only by removing false proof and replacing unsupported hero/grouping defaults with the same task-first priorities; do not redesign unrelated elements.

- **Semantic pairs:** retain existing surface/text, secondary-text/surface, action/on-action, focus/adjacent-surface and error/surface pairs where available. Exact colours are unresolved. Validate normal text at 4.5:1, large text at 3:1, and relevant controls/focus at 3:1; keep operational text off variable photography unless a stable treatment passes testing.
- **Type roles:** existing licensed heading, body, operational date/price and action-label roles. Keep dates and prices legible and comparable; do not select a new font without a reason.
- **Spacing and density:** reuse the existing spacing scale. Keep each class’s date and price close together, with larger separation between class options. Favor scanability over a large decorative hero.
- **Layout:** studio image beside a short, verified class promise where space permits. Put actual class dates and corresponding prices in the first decision section, before the booking action. At narrow widths, preserve decision-content-first reading order rather than letting the image push it away.
- **Actions:** use a result-specific label such as “Choose a class” only if that is the actual next step. Preserve familiar controls; never imply a booking is confirmed merely because a button was clicked.
- **States to confirm:** loading, no scheduled classes, unavailable/sold-out selection, fetch failure with retry, selection and booking handoff. If booking is in scope, also define submission, recoverable failure and confirmed success. Denied/no-results states apply only if the real flow requires them.
- **Motion:** no decorative motion is needed by the supplied task. Preserve any existing useful feedback and reduced-motion behavior rather than inventing animation.

**Boundary case:** retain purple gradients for the separate art-event brief because they are explicitly requested. Check readability and task hierarchy without deleting the intended aesthetic. A catalogue tell is not a blanket style ban.

## Handoff
- **Built:** comparison and revised plan only; output.md and candidate-meta.json are the sole changed artifacts. No app files changed.
- **Verified:** textual integrity gate, choice-to-brief mapping and unrelated-product check. No screenshots, contrast measurements, interaction tests or conversion tests performed.
- **Findings:** invented proof is a publication blocker; unsupported hero/card defaults are task-fit concerns. Remove false proof, restore date/price priority, then validate with approved content.
- **Unknowns:** actual commercial data, promise, assets/rights, existing implementation/tokens, supported widths and booking behavior. Visual/accessibility verification remains unperformed; no rendered draft or preview was supplied for this comparison.
- **Next owner:** Aman supplies facts and approvals; coding agent implements and tests keyboard, focus, labels, contrast, reflow and recovery states at agreed widths; writing agent verifies promise and booking copy.
