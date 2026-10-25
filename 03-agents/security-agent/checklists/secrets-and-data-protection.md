# Protect credentials and data through their lifecycle

| Control | Verification test |
|---|---|
| Resolve short-lived scoped credentials in tools, not prompts | Inspect model inputs and tool schemas; verify only opaque handles cross the boundary |
| Exclude secrets from repository/history/builds/logs/tickets | Run approved redacted scans; plant a fake canary and confirm it cannot leave in traces |
| Restrict secret recipients and origins | Change endpoint origin; require reapproval before a token-bearing request |
| Rotate after exposure | Revoke a fixture token; prove old token fails; verify dependent services recover |
| Minimize personal data sent to models | Compare outbound fields with the documented purpose; remove unneeded identifiers |
| TLS verification and encryption at rest/backups | Reject invalid certificates; inspect key access and restore permissions |
| Retention and deletion by purpose | Delete a synthetic record and inspect indexes, cache, exports and backup restoration policy |
| Least-privileged audit access | Attempt bulk log access and deletion as an app worker; require denial |
| Incident escalation without additional leakage | Send a sanitized urgent finding to the approved owner; verify no raw secret is attached |

Environment variables are a delivery mechanism, not a vault. Dumps, child processes and logs can expose them. GDPR obligations also include lawful basis, transparency, rights handling and accountability. Encryption alone does not satisfy them; seek jurisdiction-specific legal review.
