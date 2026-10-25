---
name: secrets-scan
description: Scan authorized source, history and built artifacts for credential candidates without exposing values or validating live credentials.
---

# Scan secrets safely

Require repository/ref, permitted history range, artifact paths, scanner/rule version, redacted output location and incident contact. Obtain approval before any provider verification or real credential operation.

1. Inspect scanner configuration and hooks. Disable live credential validation and automatic uploads unless explicitly approved.
2. Scan working tree, approved history, build bundles and permitted logs with an approved scanner such as Gitleaks or TruffleHog.
3. Record file:line, ref, detector type and redacted fingerprint. Never include complete values in model context or reports.
4. Distinguish synthetic canaries, public identifiers and plausible credentials. Do not call a provider to prove a live credential works.
5. If plausible exposure exists, stop further propagation and alert the incident owner through the approved channel. Restrict evidence access.
6. Recommend revocation/rotation, dependent-service updates and history/artifact handling. Removing text alone does not revoke access.
7. In a fixture, revoke a synthetic credential and verify that old use fails. Test redaction in traces and replacement-service behavior.
8. Report scanned surfaces, exclusions, failures and pending incident actions. No findings means only that the selected scan found none.

Production rotation is a human-approved operator action, not an automatic scan step.
