# Role permissions

This is a proposed policy for Aman's roster. The dispatcher, sandbox and egress proxy must enforce it. Combining roles requires review of their combined privileges.

| Agent | Allowed by default | Denied by default | Approval-gated |
|---|---|---|---|
| Research / technology scout | Public reads through proxy; attributed notes | Production secrets, downloaded execution, private-data sends | Private connectors, authenticated browsing, purchases |
| Coding | Application branch edits; reviewed sandbox commands; synthetic tests | Main writes, production secrets, deployment, unrestricted network | Dependencies, hooks, CI/IAM/MCP changes, migrations |
| Security | Repository and sanitized configuration; approved local scans | Production mutation, customer exports, credentialed untrusted CI | Active scan target/window/rate, sensitive incident evidence |
| Adversarial council | Independent critiques; explicitly scoped replica tests | Third-party attacks, real secrets, persistence | Scope expansion and destructive simulation |
| Data/ML | Approved deidentified datasets and scoped compute | Arbitrary customer records, raw PII export, retention changes | New datasets/providers, training exports, spend increase |
| Writing/design/marketing | Approved briefs and draft artifacts | Publication, customer mail, arbitrary plugins, production records | Final content/destination approval for sends and publication |
| System design/planner | Sanitized architecture and proposed plans | Permission grants, production provisioning, direct secret access | Infrastructure purchases and privileged changes |
| Deployment/operator | Signed artifact and allow-listed runbook with short-lived identity | Arbitrary production-admin shell, self-approval, bulk reads | Deploy/migrate, key rotation, data-impacting rollback |
| Memory/indexer | Bounded attributed facts in scoped namespaces | Credentials, cross-tenant retrieval, untrusted instructions as policy | Shared-memory promotion and policy changes |

Every role needs separate approval for deletion, irreversible migration, sensitive transmission, privilege escalation, new MCP servers or disabling checks. No worker may approve itself.

Run workers without host credential mounts or Docker sockets. Route egress through an allow-list with IP and redirect validation. Remote MCP servers enforce their own scopes; a local shell sandbox does not contain remote effects. Emergency access must expire and receive an independent review.
