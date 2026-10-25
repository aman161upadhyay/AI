# Run and interpret your evals

Choose the agent and a concrete task family. Say: “Run the indexed cases on this frozen prompt revision. Preserve every trial, report actual state and do not change the gold.”

Supply approved model access, sanitized inputs, accepted examples and your budget. Grant the runner disposable environments; grant the grader separate hidden-label access. Refuse production credentials, writes to protected tests and automatic external actions. Public benchmark rights need separate approval.

Follow the manual run procedure in `../04-harness-components/evals-framework/runners.md` until an Inspect adapter is implemented and inspected. Run a known failure, a clean control and a missing-tool case before trusting the scorer. Use a human for voice, ambiguous evidence and high-impact judgments.

Record results using `results/README.md`. Compare the candidate and baseline on identical cases and budgets. Look at per-failure-mode results, cost and time; do not select from a single aggregate score. Review disagreement, repair the agent and add the minimized failure to its local eval folder. Submit the change to the repository council before pushing.
