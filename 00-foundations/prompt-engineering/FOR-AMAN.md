# Improve a prompt from a failed task

Ask: “Diagnose this failure before changing the prompt. Separate missing evidence, tool defects, contradictory instructions, and model limitations. Propose the smallest patch and rerun the fixed evaluation set.”

Supply the current prompt, exact model/API settings, input examples, failed outputs, desired behavior, and evaluator feedback. Grant sanitized trace and fixture access. Refuse private chain-of-thought requests, production secrets, and permission expansion.

Start with a plain task contract. Add demonstrations only when you can name the ambiguity that they resolve. Use native schema enforcement when your exact model supports it.

Approve the diagnosis, then the patch. Compare against the unchanged baseline at equal cost and latency limits. Run an abstention case and an injected-evidence case before trusting factual output. Keep the previous prompt version for rollback.
