# Review your design before implementation

Ask: “Use architecture-review on this design. Identify violated requirements with path/section evidence and a safe validation step. Do not force a finding count.”

Supply the brief, diagrams, schema, API/deployment contracts, accepted ADRs, and allowed checks. Grant read-only inspection and authorized nonproduction validation. Refuse cloud writes, production probes, and credential discovery.

Run the preview-isolation, duplicate-webhook, and underspecified-brief evals. Compare against an unassisted review. Approve fixes after your security agent checks consequential risks; do not accept generic advice as a located finding.
