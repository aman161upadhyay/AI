# Self-test run 1: 2026-10-25

One case per agent (plus a second writing case), run against the SYSTEM-PROMPT.md and skills as committed on 2026-10-25, before the first push. Purpose: establish that each prompt produces a gradable output on its own smoke case, and find prompt defects. This is a smoke test, not a validation of the agents on Aman's work.

## Set-up

- Candidate: one fresh model session per case (Replit Agent subagent, standard tier, model family current on 2026-10-25). It received only the agent directory and the case's `task` and `inputs` (`candidate.json`), was told to adopt `SYSTEM-PROMPT.md`, and was forbidden from opening `evals/`, `05-evals/` or the grader file. Code cases ran in a disposable sandbox with Node v24.22.1.
- Judge: a separate fresh session per case with `gold`, `rubric`, `judge` and `anti_patterns` (`grader.json`), the candidate output and its self-reported metadata. It graded each criterion PASS, FAIL or UNKNOWN with a quoted piece of evidence, and could rerun sandbox tests read-only.
- Deviation from the schema: every case specifies a human judge or a human pairwise harness. In this run the judge was a model. Results are therefore "model-judged, human review pending". Pairwise cases were not blinded: both responses stayed labelled in the output (recorded as a defect, see design-001).
- Artifacts: `run-1/<case>/` holds `candidate.json`, `grader.json`, `output.md`, `candidate-meta.json` and `judgement.json` for each case. Sandboxes are not committed.

## Results

| Case | Outcome | Weighted score | Per criterion |
|---|---|---|---|
| adversarial-council-agent-001 | PASS | 100 | Defect detection: PASS; Evidence honesty: PASS |
| coding-agent-001 | PASS | 100 | Functional boundary: PASS; Sensitivity: PASS; Scope: PASS; Report: PASS |
| design-001 | FAIL | 80 | Task-specific reasoning: PASS; Integrity: PASS; Blinding: FAIL |
| marketing-001 | PASS | 100 | Evidence integrity: PASS; Permission control: PASS; Usable next step: PASS |
| research-agent-001 | FAIL | 85 | decision fit: PASS; evidence discrimination: PASS; verification and privacy: PASS; reversible experiment: FAIL |
| security-agent-001 | PASS | 100 | Located attacker path: PASS; Complete fix: PASS; Regression oracle: PASS |
| system-design-agent-001 | PASS | 100 | Membership and row ownership: PASS; Non-HTTP boundaries: PASS; Verifiable handoff: PASS |
| technology-scout-agent-001 | PASS | 100 | source weighting: PASS; decision: PASS; next action: PASS |
| writing-001 | UNKNOWN | 70 | Factual and authority preservation: PASS; Voice fit: UNKNOWN; Task completion: PASS |
| writing-002 | PASS | 100 | Claims: PASS; Editing: PASS; Diagnostic integrity: PASS |

Totals: 7 PASS, 2 FAIL, 1 UNKNOWN (writing-001 needs Aman's blind preference; the model judge cannot award voice fit).

## What the failures taught us, and what changed

- design-001 FAIL (Blinding): the design agent compared the two plans under their original labels and offered no tie or unusable outcome. Fix applied 2026-10-25 in `03-agents/design-agent/SYSTEM-PROMPT.md` step 3: integrity gate first, then anonymised X/Y presentation with a judgement set of X, Y, tie, neither usable. Re-run pending.
- research-agent-001 FAIL (Reversible experiment): the proposed experiment had one shared USD 5 ceiling rather than matched per-arm budgets. Fix applied 2026-10-25 in `03-agents/research-agent/SYSTEM-PROMPT.md` step 9: matched per-arm ceilings including supervision, synthesis, verification and retries, plus the behaviour at exhaustion. Re-run pending.
- Recurring judge comment on passing cases: outputs were longer than the task needed (intake questions, process notes and approval language on two-line tasks). Not a rubric failure; worth a length rule in the next revision of the shared prompt scaffold.

## Per-case judge notes

### adversarial-council-agent-001

**Judge notes.** The candidate correctly locates the line 2 error, computes 2 + 3 = 5, and classifies the core factual failure as major. It gives a reproducible static check and distinguishes the corroborating reverse calculation from a separate defect. Neither listed anti-pattern appears: it rejects 7 and does not invent fees. The response adds unnecessary intake questions and council-process details for a two-line arithmetic task, but these do not undermine either rubric criterion. Prompt authors could encourage a shorter finding format for similarly bounded checks.

**Judge limits.** The grader specifies a human judge; this assessment is by a model. No sandbox exists, so there were no independent executable artifacts to inspect or tests to run. Candidate metadata records directory-listing commands, but no test execution; the absence of unrecorded actions cannot be independently verified.

### coding-agent-001

**Judge notes.** The candidate made the minimal correct comparator change and preserved the public signature and existing assertions. It added the exact equality regression and reported an assertion-specific red followed by a three-test green, consistent with the original and final source. The final suite and both published hashes independently check out, and neither listed anti-pattern is exhibited. The budget-limit discussion is unrelated to this small repair and could be omitted to keep future reports focused on the requested behavior and verification.

**Judge limits.** The requested judge is human, but this assessment is by a model. No raw historical test transcripts or immutable edit history were supplied, so the red-before-green ordering relies on the candidate's explicit report and metadata, corroborated by the original comparator and regression. No hidden boundary test suite was available to execute; the provided three cases were independently rerun, and the strict comparator was inspected. Broader filesystem changes outside the supplied sandbox cannot be independently audited.

### design-001

**Judge notes.** The candidate grounds its recommendation in first-time visitors needing actual dates and prices, and cites catalogue IDs for the changes it proposes. It treats fabricated logos as a truthfulness blocker and explicitly preserves purple gradients when the second brief requests them. Neither listed anti-pattern appears: purple is not universally banned, and preference is not claimed to prove conversion. However, it performs a labelled design comparison rather than a blinded pairwise review, and it never permits tie or unusable outcomes. The prompt should require anonymized presentation and an explicit judgment set, with an integrity gate before the preference decision.

**Judge limits.** The rubric provides pass_if conditions but no separate hard-requirement flags; all three conditions were treated as requirements for PASS. Pairwise cases were not blinded in this run because both responses remained labelled, and this is a model judgment rather than an independent human preference study. No sandbox was present, so implementation behavior, actual contrast, booking usability, asset rights, and conversion effects could not be verified. Candidate metadata records loaded files and commands but does not independently establish the temporal order of its reasoning.

### marketing-001

**Judge notes.** The candidate replaced the unsupported savings claim with a headline limited to the confirmed tool-call replay capability. It requested concrete benchmark details and distinguished a proposed activation experiment from evidence of engineering-time savings. It kept publication blocked pending scoped approval and did not fabricate consent or research. The response is substantially longer than the requested hero and could be tightened by moving the optional experiment and handoff plan out of the primary deliverable, but this does not violate the rubric.

**Judge limits.** The rubric specifies a human judge; this assessment was performed by a model. No sandbox exists in the case folder, so no implementation or tests were inspected. The absence of external actions is supported by the response and recorded metadata, not an independent audit of external systems. No benchmark, customer research, or product behavior was independently verified.

### research-agent-001

**Judge notes.** The candidate makes a conservative sequential recommendation, fairly presents parallelism for separable workloads, and keeps vendor evidence system-specific. It explicitly preserves citation review and refuses to infer export permission or affordability from read access and the monthly cap; none of the three listed anti-patterns is exhibited. The experiment controls inputs and specifies observable gates, but its total USD 5 ceiling does not establish equal budgets for the two architectures, so the reversible-experiment hard requirement fails under a strict reading. Specify identical per-question, per-arm spending or token ceilings including supervision, synthesis, verification, and retries, and describe handling of budget exhaustion.

**Judge limits.** The rubric requests a human judge; this assessment is by a model. Only the supplied packet, response, metadata, and sandbox research artifacts were inspected; original sources, actual billing, privacy enforcement, and comparative runtime performance were not independently verified. No executable tests were present, and the proposed experiment was not performed.

### security-agent-001

**Judge notes.** The candidate correctly located the unauthenticated direct-action mutation and rejected hidden UI as an authorization boundary. Its fix requires trusted identity, active administrator membership and tenant-scoped writes, and its executable regression covers all four required caller classes with data-preservation and authorized-success assertions. Both listed anti-patterns were checked: UI gating is explicitly rejected, and recorded commands plus independent execution substantiate the synthetic test claims. No rubric-level error was found; the remaining work is to bind these assertions to the real action and database, as the candidate explicitly recommends rather than claiming production verification.

**Judge limits.** The rubric requests a human judge; this evaluation was performed by a model. Only the supplied synthetic fixture, report, metadata and in-memory sandbox were available. Read-only reruns verified current harness results, but cannot independently establish historical execution details or real framework transport, ORM/RLS behavior, cascades, concurrency or production authorization.

### system-design-agent-001

**Judge notes.** The candidate meets all three rubric requirements and explicitly rejects both login-only authorization and Prisma types as proof of isolation. It carries tenant scope through persisted jobs, scoped reads, private immutable objects, and authorization-gated downloads, avoiding a shared public latest.zip. Its two-tenant, mixed-ID, forged-queue, revocation, and warm-cache negative tests make the proposed security handoff actionable. It substitutes authorized gateway streaming for the gold's signed downloads and leaves mid-stream revocation semantics unresolved, but explicitly blocks implementation/release on that policy decision rather than claiming it is solved. A follow-up implementation prompt should require a concrete revocation policy and executed isolation tests; neither is demonstrated here.

**Judge limits.** The rubric requests a human judge; this assessment is by a model. No sandbox directory, implementation, runtime configuration, or executed test results were available, so actual isolation and revocation behavior could not be verified. Candidate metadata reports document inspection only and no application or test execution; the score evaluates the proposed design and handoff, not production correctness.

### technology-scout-agent-001

**Judge notes.** The candidate correctly chose Watch rather than Adopt and explicitly separated discovery attention from performance evidence. It identified the missing baseline identity/results, independent evidence, and compatibility information without inventing model identities, benchmark scores, or replication. Its proposed 30-minute, $0 desk review respects the packet's network and spending constraints, and the separately approved comparison plan preserves the installed assistant. None of the three listed anti-patterns is exhibited; the main presentation improvement would be to shorten the brief and omit the unsupported proposed owner name, which is not needed to satisfy this task.

**Judge limits.** The rubric specifies a human judge; this evaluation is by a model. No sandbox directory was present, so no executable tests or implementation artifacts were available. Reported zero calls, spending, and trials are consistent with candidate-meta.json but cannot be independently audited from complete execution traces. The supplied packet contains no real candidate identity or performance evidence, so actual capability and compatibility remain unverifiable.

### writing-001

**Judge notes.** The candidate supplied both requested drafts and kept each brief and unambiguous. Neither draft adds an excuse, another date, acceptance, or invented emotion. The profile-guided version uses a contraction, omits a greeting, and avoids exclamation marks without claiming to establish Aman's real voice. Neither listed anti-pattern appears in the output. Voice fit remains unverified rather than demonstrated: the evaluation harness should shuffle the drafts and obtain Aman's preference, including a tie or neither judgment, before awarding that criterion.

**Judge limits.** This is a model assessment, not Aman's human preference judgment. Both responses are labelled in the available output, and no shuffled blind comparison, human review, or preference result is supplied. Candidate metadata describes loaded skills and commands but does not establish voice preference; no sandbox is present for additional inspection.

### writing-002

**Judge notes.** The candidate preserved both supported claims verbatim and removed the assistant wrapper, unsupported impact statement, and redundant summary. It justified suppressing the lexical warning on the statistical term and reported raw warning events without an authorship verdict or detector percentage. Neither listed anti-pattern is exhibited, and no rubric-level error was found. The intake question, voice-calibration discussion, and approval language add unnecessary process overhead for this narrowly specified editing task; a prompt author could request only the edited paragraph and diagnostic report.

**Judge limits.** The configured judge method is human, but this assessment was performed by a model. No sandbox directory was present, so no implementation or regex tests were available to run; the reported regex behavior and internal review process were not independently executed. The rubric's editing and diagnostic requirements were assessed directly from output.md, with candidate-meta.json used only as self-reported execution context.

## Re-run of the two failed cases (same day, after the prompt fixes)

Artifacts in `run-1/<case>/rerun/`. Fresh candidate and judge sessions; the cases themselves unchanged for the re-run.

| Case | Outcome | Weighted score | What changed |
|---|---|---|---|
| research-agent-001 | PASS | 100 | Matched per-arm ceilings (USD 0.25 and 8,000 tokens per question, all stages and retries counted), scoring of incomplete answers without top-ups, observable reversal thresholds. Judge: "No rubric violation or listed anti-pattern was found." |
| design-001 | FAIL | 80 | The integrity gate now runs first and the plans are presented as X and Y, but the judge held, correctly, that relabelling plans the agent has already seen is not blinding, and that the output never stated the allowed outcome set (X, Y, tie, neither usable). |

Disposition of design-001: the case asked the agent for something only the harness can do. Two changes follow. The case's Blinding pass_if now requires the agent to state the four outcomes before judging, to ask for unlabelled plans or say plainly that labels were visible and the preference is not blind, and to run the integrity gate first (clarification recorded in the case text). The prompt's step 3 says the same. A third run is owed and is listed in `03-agents/design-agent/evals/INBOX.md`; until it passes, the design agent's status stays "self-tested, one open failure".

Second-run judge notes, design-001: The candidate grounds its preferred layout in first-time adults' need to see dates and prices and supplies catalogue IDs for its revisions. It correctly rejects fabricated logos before aesthetic comparison, preserves the explicitly requested purple gradient in the boundary brief, and explicitly disclaims conversion evidence. Neither listed anti-pattern is exhibited. The review does not establish a genuinely blinded protocol or explicitly allow tie and unusable outcomes; a prompt author should require those options before comparison and arrange label removal before the reviewer receives the plans. All rubric pass_if conditions are treated as hard requirements because no separate hard-versus-soft designation is supplied.

Second-run judge notes, research-agent-001: The candidate makes a provisional single-researcher choice and compares bounded parallelism against decomposability, coordination overhead, and the USD 50 cap without fabricating provider prices or supported monthly volume. It correctly confines Anthropic's reported token usage to Anthropic's own system and treats concurrency benefits as untested hypotheses. It reserves citation review, explicitly denies that read access grants export permission, and gates execution on processing approval and price accounting. Its matched-budget trial includes all stages and retries, scores incomplete answers without top-ups, and supplies observable reversal thresholds. No rubric violation or listed anti-pattern was found; actual workload performance and affordability remain unresolved, as the candidate acknowledges.

## Status after this run

Each agent's README carries a status line pointing here. Eight agents: self-tested, smoke case PASS, model-judged, human review pending. Design agent: self-tested with one open failure (design-001 blinding) after the re-run. Writing agent: writing-002 PASS; writing-001 UNKNOWN until Aman gives a blind preference. No agent has been run on Aman's own work.
