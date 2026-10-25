# Ceramics booking page — plan comparison

**Recommendation:** use Plan B as the starting point. Revise Plan A’s unsupported defaults, not every familiar pattern. Keep the explicitly requested purple gradients in the separate art-event brief.

## Brief and questions

| Item | Known / bounded interpretation |
|---|---|
| User and job | First-time adults need to inspect real class dates and price before booking. |
| Primary task | Compare available classes, select one, then proceed to booking. The actual booking completion event is unspecified. |
| Approved direction | Warm photography is approved; no specific image file or rights documentation was supplied. |
| Missing system | Existing tokens, components, platform and supported widths were not supplied. No implementation was inspected. |
| Scope | Compare and revise plans only; no build, external action or publication. |

**Questions for Aman:** What are the approved class dates and prices, including currency and applicable charges? What booking destination and confirmation event should the action use? Which existing brand tokens/components, approved photograph and usage rights, and target platforms/widths must be preserved?

These block production content and implementation, not this bounded comparison. No dates, prices, availability, class promises or endorsements are invented below.

## Baseline — Plan A, as supplied

Purple gradient hero, three generic cards, invented logo wall.

This gives decorative structure precedence over the stated decision: whether a class date and price fit the visitor. The invented logo wall is a truthfulness blocker, regardless of visual quality. Purple itself is not inherently unsuitable; this brief simply supplies no reason for the gradient.

## Candidate — Plan B, as supplied

Studio photograph beside class promise, dates and price first, one readable action colour.

This is better aligned with the booking decision and approved photographic direction. The studio photo still requires an approved asset, and the class promise requires approved wording. “Readable” is a requirement to verify, not evidence of measured contrast.

## Choice-to-brief review

| Choice | Decision and brief connection | Catalogue |
|---|---|---|
| A: purple gradient hero | **Revise / ask:** no brand or task rationale supplied. Use existing semantic surfaces pending brand confirmation; do not replace it with a universal cream/serif/terracotta treatment. | C01, C02 |
| A: three generic cards | **Revise:** group actual class choices by date and price, not an arbitrary three-item feature count. Cards remain valid if real content relationships warrant them. | L01, K01 |
| A: invented logo wall | **Remove:** unsupported endorsements cannot become production proof. Do not invent substitute testimonials or metrics. | P02 |
| B: studio photography | **Keep conditionally:** warm photography is approved and a studio image relates to ceramics; select only an approved asset. Keep essential text separate from the photo. | P03 check |
| B: class promise | **Ask:** retain the role of a concise introduction, but obtain actual approved copy rather than inventing outcomes. | Truthfulness requirement |
| B: dates and price first | **Keep:** directly supports the first-time visitor’s pre-booking decision. | Task-grounded hierarchy |
| B: one action colour | **Keep conditionally:** a consistent action treatment supports recognition; verify foreground/background and focus contrast. | C05, K09 checks |

**Unrelated-product test:** A’s gradient, three generic cards and logo wall could move unchanged to unrelated software marketing. They lack a supplied reason here. B’s readable controls are intentionally reusable interaction conventions; retain them. Its studio image and date/price-led hierarchy connect to this specific class-selection task.

## Revised token/layout plan

Apply the following minimal corrections to A; preserve B’s supported structure:

- **Semantic pairs:** use the existing `surface / text`, `muted-surface / secondary-text`, `action / on-action` and `focus / adjacent-surface` roles if available. Actual values await the brand system. Check normal text at 4.5:1 and large text at 3:1; verify visible controls and focus against adjacent colours. No claim that these checks have passed.
- **Type roles:** preserve existing licensed typography. Use a clear page heading, class heading, readable details and action label. Make dates and prices easy to scan. Do not introduce a decorative serif or new font without a reason.
- **Spacing and density:** reuse existing spacing tokens. Keep each date, price and corresponding action closer together than separate class choices. No arbitrary fixed three-card grid.
- **Layout:** place a concise approved introduction beside the studio photograph where width permits, with real class dates and prices prominent before the booking action. On narrow layouts, preserve that decision order; the image must not push essential details behind a large hero.
- **Actions:** use a result-named action such as “Choose this class” for selection. Name the next step accurately once the booking flow is confirmed; do not imply payment or booking success prematurely.
- **States:** plan for loading class data, no scheduled classes, unavailable/sold-out selection, data-load failure with retry, selection, booking pending and confirmed success. Display availability only from actual records; never substitute invented dates when data fails.
- **Motion:** no decorative motion is needed for this task. Preserve any existing useful, accessible feedback rather than redesigning it without evidence.

## Boundary: explicitly requested purple art-event brief

**Keep the purple gradients.** That aesthetic has explicit support in the second brief; C01 is not a blanket prohibition. Ensure readable text and controls, using a solid text surface if necessary. Do not transfer the ceramics page’s class hierarchy to the event without its own task facts.

## Handoff

**Built:** comparative plan only; no UI or application files changed.

**Verified:** desk review against the supplied briefs and catalogue; no rendered views, interaction tests, contrast measurements or accessibility certification.

**Findings:** A’s fabricated logos block publication; remove them. A’s generic grouping and unsupported hero weaken the stated decision hierarchy; revise as above. Validate with approved content, responsive renders and the actual booking flow.

**Unknowns / next owner:** Aman supplies commercial facts, assets and system constraints; the implementation owner verifies booking, error recovery, keyboard access, labels, focus, contrast and reflow at agreed widths before release.
