# Runtime controls and their limits

| Control | Enforce | Does not stop | Verification |
|---|---|---|---|
| Tool allow-list | Explicit operations and resource scope for a user/tenant/task | Misuse of a broad allowed tool or malicious original schema | Call unknown tool, wrong tenant and wrong resource; require denial |
| Deny-list | Known hazardous commands, paths and destinations | New encodings, equivalent tools or unlisted paths | Test alternate write tools, rename, symlinks and absent-file creation |
| Filesystem sandbox | Read/write roots, no home/cloud/SSH/socket mounts | Remote API effects or unsafe files inside allowed roots | Attempt outside-root read/write and host-socket access |
| Execution sandbox | Disposable process/container/VM, limits and no ambient credentials | Kernel/runtime vulnerabilities or deliberate privileged mounts | Inspect mounts/identity, terminate runaway work and verify cleanup |
| Egress proxy | Scheme/origin/IP/redirect limits, size and destination labels | Disclosure to an overbroad allowed recipient | Test IPv6, link-local, private ranges, changed DNS and every redirect |
| Credential broker | Scoped expiring tokens injected only into a specific tool | Authorized but overprivileged operations | Verify scope/expiry and absence from model inputs and logs |
| Approval service | Independent approval bound to principal, args/hash, resource, destination and expiry | Misleading human decisions or an unsafe approved operation | Change body, resource, actor or destination; reject reused/expired approvals |
| Output filtering | Schema, redaction and known sensitive patterns before egress | All semantic secrets, encodings or unauthorized tool effects | Seed canaries across outputs, errors and streamed chunks |
| Audit logging | Actor, policy decision, approval ID, redacted args and outcome | Prevention by itself or worker tampering if stored in its workspace | Attempt audit deletion; verify append-only external records and alerts |
| Budgets | Global tool/time/cost/worker caps and bounded retries | Damage within the first allowed action | Exhaust fixture quota and verify immediate termination |
| Memory policy | Tenant namespaces, attributed facts and reviewed promotion | False facts accepted by an authorized reviewer | Inject a future export rule; inspect persistent state for rejection |

## Dispatch sequence

Authenticate the task principal. Resolve the pinned tool manifest and validate the argument schema. Evaluate operation/resource/data policy. Resolve any independent approval and verify its binding. Execute with scoped credentials and sandbox/egress constraints. Filter returned data before model exposure. Persist a redacted receipt.

Do not allow schema validation to substitute for authorization. A valid URL can still point to metadata, and a valid object ID can belong to another tenant. Never trust the model to perform the policy check that constrains the model's own tool.

## MCP boundary

Bind OAuth audience and per-client consent; reject token passthrough. Validate exact redirect destinations and discovery fetches. Pin tool descriptions as well as executable/schema revisions. A schema change forces review, but a malicious original schema also needs inspection.

Remote servers need independent authorization and audit. Local command sandboxing does not constrain a remote connector's database writes. Stop when a server changes its destination, identity requirements or tool manifest.
