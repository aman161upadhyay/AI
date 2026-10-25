---
name: model-release-evaluation
description: Assess a model or tool release against an installed baseline with primary evidence, fixed workload tests, public prompt checks, and explicit execution approval.
---

# Evaluate a candidate release

Use for a shortlisted release, a disputed benchmark, or a proposed migration. Source review is the default mode. Execution requires scoped approval.

## Establish the experiment

1. Record the current problem and exact installed baseline. Ask for missing task fixtures before recommending Adopt.
2. Identify candidate model ID, endpoint, revision, access tier, region, hardware, license, and availability.
3. Read primary release notes and model cards. Check limitations and effective dates. Keep vendor assertions separate from independent reproductions.
4. Freeze sanitized task IDs, metrics, success threshold, repetitions, and a confirmation set. Record time, token, and dollar caps before tests.
5. Confirm authorized provider, sandbox, outbound destinations, data classification, owner, and rollback target. Do not install or call a paid model without this approval.

## Choose checks that fit the workload

| Dimension | What to check | Record |
|---|---|---|
| Task quality | Actual research, code, extraction, or generation tasks from the intended workload, including failure cases. | Per-task correctness and severity of regressions, not only a mean. |
| Tools and structured output | Required tool selection, arguments, schema validity, error recovery, and unsupported-feature behavior. | Actual effects and parse/test results. A valid schema does not prove correct content. |
| Context and retrieval | Long-document attribution, relevant-span recovery, citation entailment, stale evidence, and injected page instructions. | Source locators, wrong claims, abstentions, and unauthorized action attempts. |
| Latency and reliability | Matched load, p50/p95 when the sample supports those estimates, rate limits, timeouts, and retries. | Sample count, distribution, errors, cache state, and run conditions. |
| Total cost | Input/output tokens, reasoning/tool costs, retries, hardware/hosting, and migration work as applicable. | Actual billable basis and observation date. Unknown charges stay unknown. |
| Compatibility and privacy | SDK/API changes, licenses, retention, region, data handling, and rollback. | Verified terms and unresolved blockers. |

A small smoke test can establish an obvious failure. It cannot establish stable p95 or rare-failure rates. Repeat noisy tests within the cap and report sample size.

## Reuse public prompts carefully

Public prompts are a separate reference slice, not hidden tests. The prompts below are verified in the supplied council research. Link outputs rather than copying them when redistribution rights are unclear.

| Public prompt | Source and reference | Test and limit |
|---|---|---|
| `Generate an SVG of a pelican riding a bicycle` | [Simon Willison's article](https://simonwillison.net/2026/Jul/9/gpt-5-6/) and [output grid](https://static.simonwillison.net/static/2026/gpt-5.6-pelicans.html), 2026-07. | Render in an isolated environment. Check SVG validity, prompt fit, anatomy, and bicycle geometry. The source does not declare a definitive winner. One drawing does not establish reasoning quality. |
| `List all of Simon Willion's open source projects, most recent first, each with a rough date of when they were first released` | [Willison's original analysis](https://simonwillison.net/2026/Jun/9/claude-fable-5/), 2026-06-09. Preserve the typo in the original prompt. | Independently verify project identity and dates. Unsupported additions reduce accuracy. The longest answer is not the gold answer. |
| `animate this` | [Willison's continuation](https://simonwillison.net/2026/Sep/1/claude-fable-5-1/), 2026-09-01. | Reuse only with the exact prior SVG and full input context. Check animation, validity, and reduced-motion behavior. If the artifact or rights are unavailable, skip and record why. |

Add Aman's own held-out tasks because these prompts are public and narrow. Do not infer a model's quality across unrelated tasks from an amusing or attractive output.

## Run and record

Keep versions and settings fixed across matched comparisons. Counterbalance order when a human or model judge could prefer the first output. Hide candidate identity from semantic reviewers. Allow ties and unknowns. Use deterministic tests before semantic judges.

Record each run in an authorized YAML data file with:

- Run ID, date, prompt revision, task ID, source URL, and input artifact hash.
- Baseline/candidate IDs, endpoint, settings, seed if available, tool versions, hardware, and cache state.
- Approved permissions, data class, caps, metric definitions, and threshold.
- Actual output artifact pointer, test results, tool errors, retries, tokens, actual cost, and latency.
- Per-criterion PASS/FAIL/UNKNOWN, evidence locator, reviewer, and uncertainty.
- Decision, regressions, confirmation-set result, rollback target, and approval still required.

Do not populate fields with invented run values. “Not run” is distinct from failure. Keep hidden labels and private traces outside the public checkout.

Stop on a cap, unsafe behavior, revoked access, or an environment mismatch that invalidates the comparison. Preserve failed trials in the report. Recommend Adopt only when applicable gates pass. Otherwise choose Trial, Watch, or Ignore and state the next discriminating evidence.

Basis: provider evaluation guidance, GitHub release semantics, arXiv source rules, and the public artifacts above. Full provenance is in `../../sources.md`.
