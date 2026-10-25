# Give the agent a product contract

Ask: “Read this repository and brief. Produce the architecture artifact set in an approved design directory. Design ownership and authorization before endpoints. Label assumptions and unresolved risks. Do not deploy or change infrastructure.”

Supply:

- Your users, tenant boundaries, and three critical journeys with acceptance tests.
- Sensitive data, jurisdiction, retention, deletion, and backup requirements.
- Current and expected users/requests/jobs/data size, with uncertainty.
- Latency, availability, RPO/RTO, monthly cost ceiling, and non-goals.
- Existing repository/schema/infrastructure, exact versions, and approved providers.
- Integration read/write scope, reference products, approval owner, and security reviewer.

Grant access in stages. Start with public docs and a read-only checkout. Add sanitized schemas, redacted traces, representative nonproduction data, and known failure cases for design evaluation. Grant isolated development service accounts only for an approved implementation phase.

Refuse production secrets in chat, unrestricted cloud IAM, live payment/email actions, customer-data export, and automatic purchases. Production migration, deployment, IAM/DNS changes, deletion, and paid resources require separate scoped approval. A design task does not authorize them.

Review the requirements and assumptions first. Then review how the system identifies users and enforces tenant boundaries, and approve that before anything else. Check that the API and deployment plans agree with the data model, then decide the open architecture questions recorded in the ADRs. Give `threat-model.md` to your security agent and `implementation-plan.md` to your coding agent. Do not accept a production-readiness claim while a critical risk remains open.

Run all six cases in `evals/` before trusting this role. Before trusting a design on your real project, test that one tenant cannot read another tenant's records, that a duplicate webhook does not repeat an operation, and that a pooled database connection does not carry one request's tenant state into the next. Replay the migrations from scratch, check that preview environments are isolated from production, and time a restore from backup. Mark each check as proposed or executed; report design-only checks separately from executed ones.
