# Secure-by-default checks

Choose an ASVS 5.0.0 target with the owner. Level 2 is a proposed starting point for applications holding user data. This checklist is not full ASVS conformance. Record status, evidence location, test ref and owner per row.

| Group | Required control | Verification test |
|---|---|---|
| Auth/identity | Authenticate protected server entry points with a maintained provider | Call APIs, server actions and downloads anonymously and as a disabled account; require no protected effect |
| Auth/identity | Require administrator MFA and step-up for sensitive changes | Attempt recovery, factor replacement and destructive actions without the required factor |
| Auth/identity | Generic errors, throttling and single-use expiring reset tokens | Compare known/unknown identities; expire and replay tokens; test approved bounded bursts |
| Auth/identity | Store local passwords with Argon2id at least 19 MiB, t=2, p=1 | Inspect hashes and configuration; check logs for plaintext; benchmark under expected load |
| Session | Secure, HttpOnly and appropriate SameSite cookies | Inspect actual HTTPS Set-Cookie; verify `__Host-` cookies have Path=/ and no Domain |
| Session | Rotate and revoke server-side; idle and absolute expiry | Replay pre-login, rotated, logged-out and expired sessions |
| Session | CSRF protection for cookie mutations; no GET mutations | Submit cross-origin requests with missing/invalid token and Origin; assert no effect |
| Authz | Deny by default at subject/object/action/tenant boundary | Replay all verbs, exports and bulk operations as anonymous/A/B/admin |
| Authz | Ignore client-supplied authority and prevent mass assignment | Change tenant, owner and role fields in body, headers and nested JSON |
| Authz | RLS with least-privileged roles; audit views/functions | Run real-role CRUD tests and new-row ownership checks; inspect browser assets for service keys |
| Input/output | Validate types, sizes, nesting, fields and upload signatures | Send malformed JSON, deep nesting, unknown fields and mismatched file types |
| Input/output | Parameterize queries; avoid shell interpolation; encode by output context | Test local metacharacters and benign apostrophes; inspect bound parameters and browser output |
| Input/output | Restrict protocols, destinations, redirects and resolved IPs | Test loopback, IPv6, private/link-local ranges and redirect-to-private in an isolated network |
| Input/output | Verify JWT signature, algorithm, issuer, audience, expiry and nbf | Reject wrong key/algorithm/issuer/audience, expired and future tokens; accept valid control |
| Data | Minimize model payloads; validate TLS; encrypt storage/backups | Inspect payloads; reject invalid certificates; inspect encryption and key permissions |
| Data | Retention/deletion across primary data, backups and derived stores | Delete a synthetic record, restore under policy and check caches/indexes for residual disclosure |
| Data | Tenant-scoped caches, object storage, retrieval and jobs | Warm tenant B's cache and export queue; A must never receive B's canary |
| Secrets | Broker short-lived scoped credentials; no prompt/bundle/log secrets | Scan history and built assets; test fake canary redaction and expiry |
| Secrets | Revoke exposed credentials, not just remove text | Revoke a test token and prove old use fails while replacement works |
| Infra | Separate production; restrict IAM, egress and debug/admin routes | Attempt anonymous admin access; inspect worker mounts; deny host socket and home credentials |
| Infra | Exact CORS origins, secure redirects, applicable CSP and quotas | Test attacker/null Origin, credentialed requests, redirect tricks and bounded expensive requests |
| Infra | Fail closed on auth and policy errors | Inject provider timeout and policy failure; require denial without stack or secret leakage |
| Logging | Record actor/tenant/action/resource/result/correlation/approval | Trigger denied cross-tenant access and privilege change; inspect redaction and alert routing |
| Logging | Protect audit integrity and retention | Attempt log deletion as the app role; verify denial and incident-owner notification |
| Dependencies | Verify provenance, lock versions/integrity and inspect hooks | Reproduce install in a credential-free sandbox; compare lockfile and lifecycle scripts |
| Dependencies | Scan SAST, secrets, dependencies and relevant infrastructure | Add safe local seeded defects; require CI detection, then remove seed and verify remediation |

Sources: ASVS 5.0.0, OWASP cheat sheets, Supabase RLS and Next.js authentication in `../sources.md`.
