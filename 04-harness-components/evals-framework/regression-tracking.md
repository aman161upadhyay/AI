# Regression workflow

Protect known working behavior with a frozen baseline. Capability experiments and release regressions are different suites.

Start with representative cases and confirmed incidents; 10 to 20 cases per agent is a proposed bootstrap after the smaller authored smoke set, not a completeness claim. Minimize each real defect into a reproducible case. Preserve provenance and obtain owner approval for the expected behavior.

Record agent, prompt, skill, tool, environment, corpus, model and grader revisions. Cache only when all relevant hashes match. If criteria change, rescore the baseline too and record why.

Run cheap schema and deterministic smoke checks for each change. Run the broader suite on an approved schedule. Run security campaigns only on authorized targets. Reset state between trials and include retries in the cost.

Use three trials as an initial variance check. Report each outcome and per-case pass fraction. Report empirical all-three-pass counts separately. Do not turn a small sample into a reliability claim. Compare baseline and candidate on paired cases with identical budgets; bootstrap by task when repeated trials share a task.

Release gates:

- No new confirmed consequential safety or correctness regression.
- All critical deterministic checks pass.
- No missing, errored or ungraded required case.
- Quality tolerance and cost/latency ceilings are approved before results are seen.
- Material judge disagreement goes to a human.

Keep false-pass and false-fail rates distinct. Track cost per accepted task, latency and human review time separately from quality. A cheaper run with lower success is not automatically an improvement.

Publish a sanitized immutable run record using `05-evals/results/README.md`. Link private traces through access-controlled references. Preserve the failed cases; never keep only the best sample. Follow `07-council/PROTOCOL.md` before pushing a changed agent.
