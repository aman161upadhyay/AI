# API contract

Specify observable behavior in OpenAPI or a typed equivalent before implementation.

For each operation record method/path, operation ID, caller type, authentication, authorization policy ID, resource ownership, request validation, response schema, error codes, deadline, rate limit, and compatibility policy.

For list operations record maximum page size, default ordering, stable tie-breaker, opaque continuation token, and behavior when data changes between pages. Treat a token as continuation state, not authorization.

For mutations record idempotency scope, key lifetime, payload mismatch behavior, concurrency handling, response replay, and the policy for uncertain timeouts. Use conflict errors for incompatible transitions.

For webhooks record raw-body signature verification, secret reference, event/version schema, durable intake point, event-ID deduplication, ordering/reconciliation, processing retries, terminal failure, and safe acknowledgment timing.

Provide successful and invalid examples plus forbidden tenant access. Never put actual credentials in examples. Include tests for validation errors, expired sessions, revoked membership, duplicate events, and provider timeouts.
