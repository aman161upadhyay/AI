# Turn an exemplar into a bounded comparison

Ask: “Study this subsystem at this pinned commit. Explain its data ownership, auth enforcement, deployment dependencies, and failure tests. Derive an independent pattern for my requirements. Do not copy restricted code.”

Supply your feature brief, current stack, constraints, approved license scope, and hidden acceptance tests. Grant read-only source/docs access. Refuse live deployments, customer data, restricted-code import, and paid-source redistribution.

Read root README/license first. Read subsystem schema and manifests next. Trace the handler or worker that implements the behavior, then its tests and deployment configuration. The catalogues name the first paths for each repo. Check nested licenses before saving snippets.

To create an eval:

1. Select a bounded task such as membership invitation, signed upload, migration, webhook reconciliation, or worker retry.
2. Pin SHA, paths, dependencies, license, observation date, and reference-access condition.
3. Write your own brief and hidden tests. Withhold the reference patch. Keep reference-assisted and no-reference runs separate.
4. Add hard gates for cross-tenant access, secret exposure, unapproved destructive migration, and unsigned payment events.
5. Inject duplicate events, provider outage, killed workers, stale caches, pooled tenant reuse, and old/new schema overlap.
6. Review output and actual test results. Record where the exemplar itself fails. Do not assume public code is unseen by the model.

Proposed weights after hard gates: functionality 25, data/migrations 20, auth/security 20, reliability/deployment 15, UX/accessibility 10, maintainability 10. These are calibration starting points, not research findings. Compare visual work at fixed viewports with real data density, loading/error/empty states, and keyboard focus.

Approve any derived pattern after a claim audit and failure test. Keep AGPL/source-available material in separately approved study environments. Get rights review before copied fixtures, training use, or publication.
