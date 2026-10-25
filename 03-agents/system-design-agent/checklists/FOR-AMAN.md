# Make each check produce evidence

Ask: “For every applicable checklist item, give an implementation path or a test, an owner, and status. Separate design approval from executed validation.”

Supply the exact stack versions, tenant policy, release target, and recovery requirements. Allow read-only inspection and approved nonproduction checks. Refuse live migrations, destructive load tests, and production credential use without separate approval.

Review deferred items against your risk budget. Run tenant isolation and failure injection before trusting happy-path checks. Give unresolved security items to your security agent and require a second review after fixes.
