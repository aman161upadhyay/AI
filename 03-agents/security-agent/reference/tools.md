# Select tools by the failure being measured

Status snapshot: 2026-10-25. Recheck license, maintenance, pinned revision and provider data terms before installation. No listed tool establishes security alone.

| Tool | Use | Limit or status |
|---|---|---|
| NVIDIA garak | Broad model probes, detectors and evaluation | Apache-2.0 core; inspect dataset/model terms; effects need separate instrumentation |
| Microsoft PyRIT | Adaptive and multi-turn red-team orchestration | MIT; use `microsoft/PyRIT`, not the archived Azure location |
| promptfoo red team | Versioned application-level CI cases | MIT core; pin CLI and inspect providers; full implementation tree was not verified in research |
| NVIDIA NeMo Guardrails | Programmable application flows and validation layers | Apache-2.0 core with separate notices; not an IAM or egress boundary |
| Guardrails AI | Structured-output validation | Apache-2.0 core; review individual validators and their network effects |
| protectai/llm-guard | Historical input/output scanner reference | MIT; archived in the research snapshot, last visible commit 2026-07-08; avoid new production dependency |
| Lakera PINT | Historical detector benchmark | MIT; archived 2026-08-05; excludes indirect-detection scoring and cannot certify agent security |
| Lakera commercial detection | Optional evaluated detection layer | Service terms and current availability need separate review; PINT archival does not establish the commercial service's status |
| Semgrep | Stack-specific SAST and custom insecure-API rules | LGPL-2.1 engine; rule/product licenses differ; repo freshness not verified |
| CodeQL | Supported-language data-flow queries | MIT queries/libraries; CLI separately licensed, private use may need entitlement |
| Gitleaks / TruffleHog | Redacted secret candidates | Workflow options, not adoption-ranked here; no live verification without approval |
| OWASP ZAP / nuclei | Scoped staging DAST / reviewed template probes | Workflow options; nuclei adoption and template safety not verified in research |

Prefer existing licensed scanners over adding a new service. Keep raw candidate evidence separate from the final findings. Tool links and evidence status are in `../sources.md`.
