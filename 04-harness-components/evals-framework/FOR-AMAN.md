# Establish your baseline

Start with “Evaluate this agent revision on these cases. Do not change the prompt or criteria during the run.” Supply approved model access, expected outcomes, a budget and sanitized examples of real failures.

Read 30 to 50 representative traces as a proposed bootstrap, then write failure observations before naming categories. Give the grader rights-cleared examples that you accept and reject. Keep held-out answers outside the evaluated agent's context.

Grant the runner a disposable workspace and approved provider endpoints. Grant the grader separate read access to final state and hidden labels. Refuse production credentials, unrestricted egress, writes to hidden tests and automatic publication. Approve hosted tracing only after retention and region review.

Before trusting results, run an intentionally failing case, a clean control and a missing-tool case. The grader must distinguish FAIL from INFRA_ERROR and UNKNOWN. Calibrate semantic judges on your labels. Use Inspect only after you inspect the adapter mapping described in `runners.md`.

Set safety gates, quality tolerance, per-run dollars and wall time before comparing candidates. Inspect disagreement with your domain expert. Turn confirmed failures into regressions, then rerun the same baseline cases on the revised agent. Do not improve a score by rewriting gold to match the output.
