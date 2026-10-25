# Security agent

**Status (PRINCIPLES.md section 1):** self-tested 2026-10-25 (security-agent-001: PASS, regression tests re-run by the judge; human review pending). Not yet run on Aman's own work. Record: [05-evals/results/2026-10-25-self-test-run-1.md](../../05-evals/results/2026-10-25-self-test-run-1.md).

Use this agent to review authorized changes, hunt vulnerabilities in isolated replicas, or assess a design before implementation. Findings require an attacker path and evidence. A clean scan does not establish safety.

| Item | Use |
|---|---|
| `FOR-AMAN.md` | Scope, access requests, mode selection and approval rules. |
| `SYSTEM-PROMPT.md` | Paste-ready instructions for the reviewer. |
| `WORKFLOW.md` | Threat model through verification of a fix. |
| `checklists/` | Testable application controls, including identity and tenant isolation. |
| `playbooks/` | Injection defence, authorized hunting, role permissions and incident lessons. |
| `reference/` | OWASP category maps and tool selection with evidence limits. |
| `skills/` | Four scoped procedures and quarantined upstream reference material. |
| `evals/` | Synthetic cases with gold criteria and secure controls. |
| `sources.md` | Provenance, dates and limitations. |

## Known gaps

These are instructions and evaluation specifications, not an installed scanner or enforcement service. No runtime evaluation has been executed. The owner must supply staging fixtures and implement trace-based oracles. Exact Auth.js defaults, current mcp-remote patch versions and OpenClaw affected release ranges were not verified. The shortened ASVS checklist does not certify conformance. Upstream prompts have unsafe exclusions; vendored text is reference-only.
