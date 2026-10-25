# Keep the OWASP lists separate

Snapshot: 2026-10-25. These mappings are local design judgments, not OWASP certification. Category names come from OWASP; meanings and control mappings are abbreviated original summaries. Controls are documented procedures until the owner implements and tests them.

## LLM Top 10 2025

| Category | Meaning | Local control |
|---|---|---|
| LLM01 Prompt Injection | Hostile content redirects model behavior | `../playbooks/prompt-injection-defence.md`: independent permission and egress checks |
| LLM02 Sensitive Information Disclosure | Responses or tools reveal private information | `../checklists/secrets-and-data-protection.md`: minimization and canary tests |
| LLM03 Supply Chain | Dependencies or model artifacts introduce risk | `../checklists/dependency-and-supply-chain.md`: provenance and pinned versions |
| LLM04 Data and Model Poisoning | Modified inputs to training or retrieval alter behavior | `../playbooks/prompt-injection-defence.md`: attributed data and reviewed promotion |
| LLM05 Improper Output Handling | Consumers execute or render model output unsafely | `../checklists/secure-by-default.md`: contextual encoding and no shell interpolation |
| LLM06 Excessive Agency | Broad capabilities enable unauthorized effects | `../playbooks/agent-permission-model.md`: per-role scope and approval |
| LLM07 System Prompt Leakage | Hidden instructions become exposed | `../SYSTEM-PROMPT.md`: refuse disclosure; never store secrets in prompts |
| LLM08 Vector and Embedding Weaknesses | Retrieval exposes or mixes unauthorized data | `../checklists/multi-tenancy-and-rls.md`: tenant-aware retrieval tests |
| LLM09 Misinformation | Unsupported outputs mislead users | `../WORKFLOW.md`: evidence and separate hypotheses |
| LLM10 Unbounded Consumption | Uncontrolled requests exhaust resources | `../playbooks/vulnerability-hunt.md`: budgets; secure-default quota tests |

## Agentic Top 10 2026

| Category | Meaning | Local control |
|---|---|---|
| ASI01 Agent Goal Hijack | Attacker changes the agent's objective | `../playbooks/prompt-injection-defence.md`: data cannot grant authority |
| ASI02 Tool Misuse and Exploitation | Tools execute unintended operations | `../playbooks/agent-permission-model.md`: scoped tools and typed arguments |
| ASI03 Identity and Privilege Abuse | Agents misuse delegated identities | `../playbooks/agent-permission-model.md`: expiring task-bound credentials |
| ASI04 Agentic Supply Chain Vulnerabilities | Skills or connectors introduce hostile behavior | `../checklists/dependency-and-supply-chain.md`: inspect and pin skills |
| ASI05 Unexpected Code Execution (RCE) | Content reaches execution without authorization | `../playbooks/vulnerability-hunt.md`: isolated execution and reviewed hooks |
| ASI06 Memory & Context Poisoning | Attacker text persists as trusted knowledge | `../playbooks/prompt-injection-defence.md`: attributed memory, reviewed promotion |
| ASI07 Insecure Inter-Agent Communication | Peer messages lose identity or trust boundaries | `../playbooks/prompt-injection-defence.md`: preserve provenance across workers |
| ASI08 Cascading Failures | One failure propagates across an agent system | `../WORKFLOW.md`: stop rules, bounded retries and sanitized checkpoints |
| ASI09 Human-Agent Trust Exploitation | Misleading output causes unsafe human approval | `../playbooks/prompt-injection-defence.md`: exact action/destination approval display |
| ASI10 Rogue Agents | Agents deviate beyond authorized control | `../playbooks/agent-permission-model.md`: external enforcement and expiry |

## Web Top 10 2025

| Category | Meaning | Local control |
|---|---|---|
| A01 Broken Access Control | Unauthorized subjects access objects or operations | `../checklists/multi-tenancy-and-rls.md`: cross-tenant CRUD matrix |
| A02 Security Misconfiguration | Unsafe deployment settings expose services | `../checklists/secure-by-default.md`: IAM/debug/CORS tests |
| A03 Software Supply Chain Failures | Builds or dependencies introduce compromise | `../checklists/dependency-and-supply-chain.md`: audit hooks and lockfiles |
| A04 Cryptographic Failures | Data or credentials lack appropriate protection | `../checklists/secrets-and-data-protection.md`: TLS, key scope and storage controls |
| A05 Injection | Untrusted data becomes an interpreter command | `../checklists/secure-by-default.md`: binding and context-aware encoding |
| A06 Insecure Design | Required security invariants are missing | `../WORKFLOW.md`: threat model before review |
| A07 Authentication Failures | Identity or session mechanisms permit impersonation | `../checklists/auth-and-identity.md`: recovery, JWT and replay tests |
| A08 Software or Data Integrity Failures | Untrusted changes are accepted as authentic | `../checklists/dependency-and-supply-chain.md`: integrity pins and review |
| A09 Security Logging and Alerting Failures | Important events are missed or not acted on | `../checklists/secure-by-default.md`: denied-access alerts and protected audit logs |
| A10 Mishandling of Exceptional Conditions | Error paths grant access or leak state | `../checklists/secure-by-default.md`: fail-closed fault injection |

Sources: OWASP LLM 2025 exact risk list, ASI 2026 full document and Web 2025 in `../sources.md`. The research verified the requested LLM 2025 edition, not that it remains the latest edition.
