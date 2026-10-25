# Security-agent provenance

Research snapshot: 2026-10-25. Inputs: `work/research/06-security.md` and `work/research/02-agent-architectures.md`, read during this build. Saved research captures remain under `work/sources/06-security/` and `work/sources/02-architectures/`; they are not redistributed here.

Tier 1 means first-party standards, implementation, original research or maintainer advisories. Tier 2 means practitioner interpretation or observational/vendor research with stated limits. “Living” means a publication day was not verified; observed date is 2026-10-25. Local procedures, severity decisions and proposed evaluation thresholds are original synthesis, not validated benchmark results.

## Standards and implementation guidance

| Title and URL | Author/org | Date | Tier | Contribution |
|---|---|---|---|---|
| [ASVS 5.0.0](https://github.com/OWASP/ASVS/tree/v5.0.0/5.0/en) | OWASP | 2025-05-30 release | 1 | Versioned acceptance baseline |
| [V6 Authentication](https://raw.githubusercontent.com/OWASP/ASVS/v5.0.0/5.0/en/0x15-V6-Authentication.md) | OWASP | 5.0.0, 2025-05-30 | 1 | Identity and recovery checks |
| [V7 Session Management](https://raw.githubusercontent.com/OWASP/ASVS/v5.0.0/5.0/en/0x16-V7-Session-Management.md) | OWASP | 5.0.0, 2025-05-30 | 1 | Rotation, expiration and revocation |
| [V8 Authorization](https://raw.githubusercontent.com/OWASP/ASVS/v5.0.0/5.0/en/0x17-V8-Authorization.md) | OWASP | 5.0.0, 2025-05-30 | 1 | Server-side access policy |
| [LLM Top 10 2025 exact list](https://genai.owasp.org/llm-top-10?cat) | OWASP | 2025 edition | 1 | LLM category names |
| [Agentic Top 10 2026](https://genai.owasp.org/download/52117/) | OWASP | December 2025, 2026 edition | 1 | ASI category names and boundaries |
| [Agentic Threats and Mitigations](https://genai.owasp.org/agentic-ai-threats-and-mitigations/) | OWASP | 2025-02-17 | 1 | Distinction from the later ASI Top 10 |
| [Web Top 10 2025](https://owasp.org/Top10/2025/) | OWASP | 2025 | 1 | Current requested web taxonomy |
| [Authentication Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html) | OWASP | Living | 1 | Generic errors, MFA and abuse controls |
| [Session Management Cheat Sheet](https://raw.githubusercontent.com/OWASP/CheatSheetSeries/master/cheatsheets/Session_Management_Cheat_Sheet.md) | OWASP | Living | 1 | Cookie and lifecycle tests |
| [Authorization Cheat Sheet](https://raw.githubusercontent.com/OWASP/CheatSheetSeries/master/cheatsheets/Authorization_Cheat_Sheet.md) | OWASP | Living | 1 | Deny-by-default object policy |
| [Password Storage Cheat Sheet](https://raw.githubusercontent.com/OWASP/CheatSheetSeries/master/cheatsheets/Password_Storage_Cheat_Sheet.md) | OWASP | Living | 1 | Argon2id minimum parameters |
| [Input Validation Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Input_Validation_Cheat_Sheet.html) | OWASP | Living | 1 | Schema and interpretation checks |
| [REST Security Cheat Sheet](https://raw.githubusercontent.com/OWASP/CheatSheetSeries/master/cheatsheets/REST_Security_Cheat_Sheet.md) | OWASP | Living | 1 | JWT, CORS and endpoint controls |
| [OAuth2 Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/OAuth2_Cheat_Sheet.html) | OWASP | Living | 1 | Redirects, state/nonce and PKCE |
| [Secrets Management Cheat Sheet](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/Secrets_Management_Cheat_Sheet.md) | OWASP | Living | 1 | Brokered credentials and rotation |
| [Supabase Row Level Security](https://supabase.com/docs/guides/database/postgres/row-level-security) | Supabase | Living | 1 | Real roles, policies and bypass review |
| [Next.js Authentication](https://nextjs.org/docs/app/guides/authentication.md) | Vercel | Living | 1 | DAL, routes and server-action checks |
| [Clerk middleware](https://clerk.com/docs/reference/nextjs/clerk-middleware) | Clerk | Living | 1 | Middleware is not object authorization |
| [MCP Security Best Practices](https://modelcontextprotocol.io/docs/tutorials/security/security_best_practices) | MCP maintainers | Living | 1 | Token passthrough, consent, SSRF and confused deputy |
| [Personal-data processing principles](https://commission.europa.eu/law/law-topic/data-protection/rules-business-and-organisations/principles-personal-data-processing-under-gdpr_en) | European Commission | Living | 1 | Purpose, minimization, retention and accountability |

These checklists summarize engineering controls in original prose. They do not reproduce complete ASVS or OWASP documents or establish conformance. The vendored Sentry reference retains its separate OWASP share-alike license.

## Research and incident evidence

| Title and URL | Author/org | Date | Tier | Contribution and limit |
|---|---|---|---|---|
| [Defeating Prompt Injections by Design](https://arxiv.org/abs/2503.18813) | Debenedetti et al., including Google DeepMind researchers | 2025-03-24; revised 2025-06-24 | 1 | CaMeL control/data separation and qualified AgentDojo result |
| [Design Patterns for Securing LLM Agents against Prompt Injections](https://arxiv.org/abs/2506.08837) | Luca Beurer-Kellner et al. | 2025-06-10; revised 2025-06-27 | 1 | Six architecture patterns; research saved abstract, with detailed interpretation below |
| [Prompt-injection design patterns](https://simonwillison.net/2025/Jun/13/prompt-injection-design-patterns/) | Simon Willison | 2025-06-13 | 2 | Practical pattern interpretation and lethal-trifecta explanation |
| [Package hallucinations](https://www.usenix.org/publications/loginonline/we-have-package-you-comprehensive-analysis-package-hallucinations-code) | Spracklen et al., USENIX | 2025-06-17 | 1 | Slopsquatting mechanism; historical experiment, not current provider rate |
| [Security Vulnerabilities in AI-Generated Code](https://arxiv.org/html/2510.26103v1) | Maximilian Schreiber, Pascal Tippe | 2025-10-30 | 2 | CodeQL observational findings with denominator and attribution limits |
| [Secure at Inception](https://snyk.io/articles/secure-at-inception-the-new-imperative-for-ai-driven-development/) | Snyk | Date not verified | 2 | Vendor claim used only to explain non-comparable prevalence statistics |
| [Semgrep Guardian](https://semgrep.dev/blog/2026/introducing-semgrep-guardian-real-time-security-for-ai-written-code) | Semgrep | 2026 | 2 | Vendor volume/performance claims are not code-generation prevalence |
| [Cursor special-files advisory](https://github.com/cursor/cursor/security/advisories/GHSA-4cxx-hrm3-49rm) | Cursor | 2025-08 | 1 | CVE-2025-54135 and absent-file approval bypass |
| [CVE-2025-53773](https://msrc.microsoft.com/update-guide/vulnerability/CVE-2025-53773) | Microsoft | 2025-08-12; updated 2025-09-08 | 1 | Command-injection facts, not every claimed injection chain |
| [Safeguarding VS Code against prompt injections](https://github.blog/security/vulnerability-research/safeguarding-vs-code-against-prompt-injections/) | GitHub Security | 2025-08-25; updated 2026-07-06 | 1 | Tool-boundary fixes and token-exposure lessons |
| [OpenClaw gateway token advisory](https://github.com/openclaw/openclaw/security/advisories/GHSA-g8p2-7wf7-98mq) | OpenClaw | 2026-01 | 1 | CVE-2026-25253 token destination failure; release ranges not extracted |
| [mcp-remote advisory](https://github.com/advisories/GHSA-6xpm-ggf7-wc3p) | GitHub advisory database | 2025, exact day not verified | 1, search-only | CVE-2025-6514 command-injection identification; patch versions not verified |

The design-patterns paper is linked, not reproduced or represented as fully reviewed in this build. Its operational summary relies on the verified practitioner explanation and research synthesis. PostgreSQL's canonical manual fetch failed in the research; deployed policy semantics still need validation. Exact Auth.js defaults were not verified.

## Tools and vendored artifacts

| Title and URL | Author/org | Date | Tier | Contribution |
|---|---|---|---|---|
| [Claude Code security review](https://github.com/anthropics/claude-code-security-review) | Anthropic | Observed 2026-10-25; latest visible update 2026-02-11 | 1 | MIT review prompt/rubric; trusted-PR limitation |
| [Trail of Bits skills](https://github.com/trailofbits/skills) | Trail of Bits | Observed 2026-10-25 | 1 | CC-BY-SA-4.0 audit-context and differential-review references |
| [Sentry skills](https://github.com/getsentry/skills) | Sentry / Functional Software, Inc. | Local inspection 2026-10-25 | 1 | Apache root, CC-BY-SA authorization reference and safety caveats |
| [garak](https://github.com/NVIDIA/garak) | NVIDIA | Observed 2026-10-25 | 1 | Broad probes; Apache-2.0 core |
| [PyRIT](https://github.com/microsoft/PyRIT) | Microsoft | Observed 2026-10-25 | 1 | Multi-turn orchestration; MIT |
| [promptfoo](https://github.com/promptfoo/promptfoo) | promptfoo | Observed 2026-10-25 | 1 | Versioned red-team cases; MIT core |
| [NeMo Guardrails](https://github.com/NVIDIA-NeMo/Guardrails) | NVIDIA | Observed 2026-10-25 | 1 | Additional flow/validation layer; Apache-2.0 core |
| [Guardrails AI](https://github.com/guardrails-ai/guardrails) | Guardrails AI | Observed 2026-10-25 | 2 | Structured validation; individual validators require review |
| [llm-guard](https://github.com/protectai/llm-guard) | Protect AI | Last visible commit 2026-07-08; archived at observation | 1 | Historical reference, not new-production recommendation |
| [PINT benchmark](https://github.com/lakeraai/pint-benchmark) | Lakera | Archived 2026-08-05 | 1 | Detector benchmark limits; not commercial-service status evidence |
| [CodeQL](https://github.com/github/codeql/tree/main) | GitHub | Observed 2026-10-25 | 1 | Static analysis queries; CLI license separate |
| [Semgrep copyright](https://github.com/semgrep/semgrep/blob/develop/COPYRIGHT) | Semgrep | File commit 2024-04-16 | 1 | LGPL engine distinction; not repo freshness evidence |
| [Snyk CLI](https://github.com/snyk/cli) | Snyk | Observed 2026-10-25 | 1 | Optional scanner; exact license type not verified |
| [OpenClaw skills](https://docs.openclaw.ai/tools/skills) | OpenClaw | Living | 1 | Skill trust and host-process secret injection |
| [OpenClaw security](https://docs.openclaw.ai/gateway/security) | OpenClaw | Living | 1 | Separate trust domains and runtime policy |
| [Hermes skills](https://hermes-agent.nousresearch.com/docs/user-guide/features/skills) | Nous Research | Living | 1 | Reviewed skill changes and procedural-learning boundary |
| [Unrolling the Codex agent loop](https://openai.com/index/unrolling-the-codex-agent-loop) | Michael Bolin, OpenAI | 2026-01-23 | 1 | Policy dispatcher and bounded execution |

Gitleaks and ZAP are workflow options recorded in the security research, not independently ranked tool recommendations. TruffleHog and nuclei were requested adjunct names; this build makes no verified adoption, version or template-safety claim for them.

Each vendored directory contains its exact commit, copied license, exclusions and safety review in `SOURCE.md`. Sentry's source was opened in the supplied clone during this build. No proprietary Claude Code runtime, full paper or third-party article is copied. No runtime security result is claimed.
