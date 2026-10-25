# Use the security agent

Give the agent a mode, an immutable repository ref, a policy matrix and a written scope. Supply routes, migrations, lockfiles, sanitized identity-provider settings and the expected tenant boundaries.

Use one of these prompt frames:

```text
Review: Review the diff between <BASE_REF> and <HEAD_REF>. Trace callers and
shared policy outside the diff, but distinguish new defects from existing risks.
Report evidence, severity, safe reproduction and a regression test.

Hunt: Hunt within <AUTHORIZED_TARGETS> at <REF> in disposable staging.
The approved window is <WINDOW>, rate is <RATE>, and budget is <BUDGET>.
Use synthetic tenant A/B identities. Do not expand targets or exploit production.

Design consult: Assess <DESIGN> against <ASSETS_AND_INVARIANTS>.
Produce trust boundaries, abuse paths, proposed controls and acceptance tests.
Label unimplemented controls as proposals. Do not claim observed vulnerabilities.
```

For every mode, name forbidden actions and an approval contact. Provide anonymous, A-member, B-member, tenant-admin and global-admin test identities. Supply synthetic records, recovery channels and a local canary collector. Choose an ASVS 5.0.0 level with the application owner.

Grant read-only repository access and an ephemeral sandbox. Grant approved Semgrep, CodeQL, dependency-audit, secret-scanner and staging-proxy access through a broker. Confirm scanner licensing, including private CodeQL use. Inspect build hooks before allowing execution. Keep production credentials out of model context.

Refuse production mutation, customer exports, unrestricted SQL, database-owner credentials, ambient browser sessions and Supabase service-role keys. If staging cannot answer a specific question, you may approve a separate read-only observability view with tenant filters, redaction, row limits, expiry and an audit trail.

The agent must never deploy, delete data, rotate real credentials, change IAM/CI/MCP/hooks, install unreviewed packages, widen egress or disable security checks without your independent approval. Bind each approval to exact arguments and destination. The agent cannot approve its own actions.

Run `evals/` before trusting reports. Require detection of the mandatory authorization and secret cases and rejection of their secure twins. Read the evidence for high/critical findings yourself. Assign the coding agent the smallest fix, then ask a separate reviewer to replay the failing test. Accept residual risk only with an owner and expiry.
