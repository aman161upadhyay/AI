# Selected Fabric transformations

These 25 selections follow research 10's editorial ranking. Selection reflects a narrow task and an inspectable output, not measured model performance. All adapted prompts remain untested.

| Folder | Use |
|---|---|
| `extract-recommendations/` | Extract advice with attribution and evidence spans |
| `compare-and-contrast/` | Compare alternatives against supplied criteria |
| `review-code/` | Find evidence-backed code defects |
| `analyze-product-feedback/` | Group feedback without losing counts or verbatims |
| `create-prd/` | Turn an approved brief into testable requirements |
| `check-falsifiability/` | Define observations that could disprove claims |
| `extract-predictions/` | Build an attributed forecast ledger |
| `explain-code/` | Explain supplied code or configuration |
| `summarize-meeting/` | Separate decisions from discussion |
| `create-stride-threat-model/` | Map authorized trust boundaries and threats |
| `review-design/` | Review software architecture, not visual polish |
| `extract-main-idea/` | Extract a thesis and any stated recommendation |
| `analyze-claims/` | Compare claims with real support and rebuttal |
| `analyze-paper/` | Review methods, findings and reproducibility |
| `identify-job-stories/` | Express evidenced customer progress |
| `analyze-sales-call/` | Review a call against customer context |
| `extract-references/` | Extract exact resource names and locations |
| `summarize/` | Produce a grounded compact summary |
| `improve-writing/` | Edit without changing intent |
| `create-design-document/` | Draft architecture with knowns and assumptions |
| `analyze-tech-impact/` | Separate observed effects from forecasts |
| `extract-primary-problem/` | Attribute the author's central problem |
| `extract-primary-solution/` | Attribute the author's proposed remedy |
| `judge-output/` | Evaluate Honeycomb queries with supplied domain rules |
| `improve-prompt/` | Patch a prompt from observed failure traces |

- `FOR-AMAN.md`: safe adaptation and eval loop.
- `LICENSE`: upstream MIT license, also copied in each pattern folder.

Each folder has an adapted `system.md`, local orientation, `SOURCE.md` and MIT license. Twenty-four retain unchanged `upstream.md` for historical comparison only. Do not load `upstream.md` as an active prompt. It can contain word quotas, fictional thinking times, warning suppression or permission to invent data. The adapted contracts reject those behaviors.

`improve-prompt/` omits the raw file because it embeds extensive provider guide text whose redistribution rights were not separately established. Its `system.md` is an original replacement, not an upstream copy. See its provenance.
