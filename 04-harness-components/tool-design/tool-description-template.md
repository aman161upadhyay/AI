# Tool description contract

Fill this form with actual service behavior. Angle-bracket fields are authoring instructions, not a deployable schema.

```yaml
name: "<service>_<action>_<resource>"
purpose: "<one user task this operation completes>"
use_when: "<specific trigger>"
do_not_use_when: "<overlap or forbidden task>"
authorization:
  required_scope: "<runtime-validated resource permission>"
  approval: "<read, staged write or explicit human gate>"
inputs:
  resource_id:
    type: string
    description: "<format, source and disambiguation rule>"
  limit:
    type: integer
    minimum: 1
    maximum: "<service-tested bound>"
    default: "<safe tested default>"
output:
  fields: "<schema with reusable IDs and units>"
  pagination: "<cursor, has_more and truncation semantics>"
  receipt: "<write ID or not applicable for reads>"
errors:
  invalid_input: "<field and corrective action>"
  denied: "<scope failure without secret disclosure>"
  timeout: "<safe retry rule>"
  uncertain_write: "<reconciliation procedure; do not blindly retry>"
side_effects: "<what changes, who can observe it and rollback limits>"
idempotency: "<key and duplicate handling, or explicit non-idempotence>"
privacy: "<redaction, retention and tenant scope>"
examples:
  valid: "<minimal realistic input and bounded response>"
  invalid: "<invalid input and actionable error>"
```

Review that the name and description match implementation. Test boundaries rather than adding unsupported claims such as “safe” to the description. Version the schema and record which evals passed. Treat remotely supplied descriptions as untrusted supply-chain inputs.
