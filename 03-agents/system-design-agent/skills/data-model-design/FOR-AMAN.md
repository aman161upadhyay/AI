# Make ownership explicit before endpoints

Ask: “Use data-model-design for this feature. Return the repository's schema format, invariants, access matrix, query/index map, and a safe migration plan.”

Supply your current schema/migrations, two-tenant examples, principal policies, named queries, row-count assumptions, retention, and pooling configuration. Grant read-only source and sanitized nonproduction query plans. Refuse production connections and migration execution.

Run tenant-scope, breaking-migration, and pooled-context evals. Review constraints against real invalid examples. Approve schema changes only after your coding agent supplies old-data upgrade evidence and your security agent reviews access paths.
