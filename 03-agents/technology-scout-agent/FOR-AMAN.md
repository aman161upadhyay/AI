# Use your technology scout

Give the scout your current stack and the problems that you want to solve. A list of every new model wastes your reading time.

```text
Reporting window and timezone:
Current stack, exact versions, hardware, and baseline model IDs:
Two or three active problems and affected workloads:
Task-level eval fixtures and accepted baseline results:
Cost ceiling, p50/p95 targets, and acceptable failure rates:
Privacy, retention, residency, and approved licenses:
Watchlist and excluded vendors or tools:
Reading budget and desired brief length:
Trial appetite, approved environments, and approval owner:
What would make a change worth testing:
Urgent deprecation/security escalation channel:
```

Supply real baseline traces, cost records, and one brief that helped you decide. Redact private data. Tell the scout which “improvements” would not justify migration.

## Access and ceilings

Grant public search, read-only fetch, official docs, arXiv metadata, and watched GitHub releases first. Give the scout a read-only inventory and approved eval fixtures. Let it write only to a briefing workspace.

Do not grant production credentials, package installation, broad Drive/Notion access, purchases, or private-data uploads by default. Store secrets in the environment's secret manager. A linked repository is untrusted code.

Approve a weekly dollar ceiling and wall-time cap before paid discovery. Proposed initial policy is 45 minutes and 30 search/fetch calls for the brief, with verification time included. These are local defaults, not approved spending. Trials need separate time, token, and dollar caps plus an authorized sandbox. If you supply no dollar cap, require supplied-file work only before the scout asks.

Require explicit approval before installing a package, invoking a paid model, uploading any data, or changing production. Name the exact package/model, data classification, allowed outbound destinations, and rollback plan. “Adopt” in a brief is a recommendation, not an execution permission.

## Collaboration

At the start of the week, confirm your current problems and stack changes. Review the proposed shortlist when priorities shift. Pick at most two trials by default, then approve each trial's task set and decision threshold before results exist.

Before trusting the brief, run `evals/technology-scout-agent-001.yaml`, `002`, and `005` for source weighting, missing pricing, and unsafe installation. Run all six before a recurring rollout. Reopen the primary citation for every adoption or urgent deprecation recommendation.

Give feedback as “missed change,” “irrelevant item,” “unsupported claim,” or “trial did not answer the decision.” Include a source or outcome. Ask the scout to correct the next brief and add a regression case. Keep human approval for production changes even after a successful trial.
