# Review generated code by risk, not a universal failure rate

The Schreiber and Tippe observational CodeQL study reports 861/7,117 analyzed files, or 12.1%, with findings. Its abstract reports 7,703 attributed files before later filtering. These are static findings in selected public files, not a causal comparison with human code or a current-model pass rate. Source: `https://arxiv.org/html/2510.26103v1`, 2025-10-30.

| Candidate weakness | What to verify |
|---|---|
| CWE-89 SQL injection | Trace attacker input to unbound query text; compare a parameterized secure twin |
| CWE-78 OS command injection; CWE-94 code injection | Trace input to execution; test only in an isolated replica |
| CWE-798 hardcoded credentials | Distinguish a fake fixture from a credential-shaped production value; do not validate live keys |
| CWE-862 missing authorization; CWE-639 object access via user-controlled key | Replay A against B's object despite a valid login |
| CWE-918 SSRF | Test initial destination and redirects through enforced egress |
| CWE-79 XSS | Check output context and unsafe rendering; do not flag normal escaped React text |
| CWE-352 CSRF | Test cookie mutations from another origin and a legitimate control |
| CWE-287 improper authentication | Test JWT verification, MFA recovery and fail-open identity errors |

SQL/OS/code injection and hardcoded credentials are reported in the study. The other rows are risk-derived review priorities, not measured frequencies from that study.

Snyk's fetched “nearly half” page does not establish a comparable denominator. The older 56.4% search-only statistic concerns developers encountering issues. Semgrep's fetched Guardian claims concern vendor performance/volume. Neither establishes a universal generated-code vulnerability rate.
