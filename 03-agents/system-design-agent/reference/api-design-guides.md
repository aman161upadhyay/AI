# API design guides

Write a contract before endpoints. These sources clear the quality bar as first-party specifications or provider behavior, observed 2026-10-25.

| Source | Apply | Caveat |
|---|---|---|
| [Google AIP-158](https://google.aip.dev/158), changelog through 2025-07-08 | Add pagination initially, bound page sizes, use opaque continuation tokens | Reauthorize every page; a token is not tenant authorization |
| [Zalando API-first guidelines](https://raw.githubusercontent.com/zalando/restful-api-guidelines/main/chapters/general-guidelines.adoc), living source | Review OpenAPI contracts and stable references early | Adapt naming to existing code instead of forcing a second style |
| [Stripe webhooks](https://docs.stripe.com/webhooks), living docs | Verify raw body signatures, persist/deduplicate, acknowledge promptly, process durably | Duplicate/out-of-order delivery requires reconciliation |
| [Stripe idempotent requests](https://docs.stripe.com/api/idempotent_requests), search-only research evidence | Specify retry keys and payload consistency | Recheck exact endpoint retention/error semantics before implementation |

For each mutation define retryable failures, deadline, idempotency scope, uncertain-result reconciliation, and terminal state. Do not retry authorization or validation errors as if they were transient outages.

Use stable error codes with safe client messages and trace IDs. Do not expose SQL, secrets, or another tenant's resource existence. Add contract tests for invalid input, unauthorized resource IDs, pagination under writes, duplicate events, and timeout-after-success.
