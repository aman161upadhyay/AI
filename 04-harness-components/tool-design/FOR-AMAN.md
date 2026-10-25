# Design a tool with your agent

Give your agent the user task, authorized resources, service/API versions, current tool catalog and examples of failed selections. Ask it to propose the smallest useful operation and an evaluation before implementation.

Load writing-tools-for-agents.md and the description template. Load safety notes before adding a remote server. Do not paste every service endpoint into every agent's prompt.

Grant read-only synthetic service data first. Broker credentials in the runtime. Refuse wildcard account scopes and production mutations during discovery. Require separate approval for destructive tools, external sends and network destinations.

Before trust, run ten stable read-only tasks whose answers you have independently verified, plus negative tests for scope, ambiguous identifiers, pagination, malformed input and timeouts. Hold out some tasks during description tuning. Review tool-call traces with the agent and change one cause at a time. You approve schema or server updates before activation.
