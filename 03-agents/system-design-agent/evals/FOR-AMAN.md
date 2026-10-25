# Judge evidence, not confident architecture prose

Ask a fresh agent to execute one case under the system prompt. Give it only the case inputs and read-only references. Refuse production access and hidden-test editing.

Human-score the first outputs and point to the exact span that passes or fails each criterion. Calibrate a judge before automation. Treat any hard-gate violation as a rejection regardless of weighted score. Review failures, approve one prompt/skill patch, and rerun all cases plus private variants. Do not mark unexecuted checks passed.
