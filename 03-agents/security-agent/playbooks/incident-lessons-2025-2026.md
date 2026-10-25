# Incident lessons with evidence boundaries

Snapshot: 2026-10-25. Advisory identifiers refer to evidence, not proof that the installed version is safe.

| Incident | Verified facts | Required regression |
|---|---|---|
| Cursor CVE-2025-54135 / GHSA-4cxx-hrm3-49rm | Maintainer advisory lists affected <=1.2.1 and patched 1.3.9; an indirect-injection chain could create absent sensitive MCP configuration without approval | Deny creation, rename, alternate write tools and edits of control files |
| Copilot/Visual Studio CVE-2025-53773 | Microsoft advisory dated 2025-08-12 establishes CWE-77, user interaction, local attack vector and fix in VS 2022 17.14.12 | Gate command execution and configuration changes independently of text |
| GitHub VS Code investigations | GitHub describes malicious issue content, token exposure and unauthorized tool chains; article updated 2026-07-06 | Separate hostile reading from credentials; bind confirmation to destination |
| OpenClaw/Clawdbot CVE-2026-25253 | Maintainer describes query-string `gatewayUrl`, automatic token-bearing connection and resulting operator access; fix adds confirmation | Reject changed token destinations before connection; loopback hosting does not excuse forwarding |
| mcp-remote CVE-2025-6514 | Official advisory search result identifies OS command injection through untrusted MCP connections | Do not interpolate server/OAuth metadata into shell; directly verify patched version before adoption |

Copilot's advisory does not independently establish every popular prompt-injection narrative. OpenClaw release ranges were not extracted. The mcp-remote advisory is search-only evidence; usable NVD version details were not retrieved.

OpenClaw marketplace-malware investigations appear as search-only sources in the architecture research. Claims of official infrastructure compromise, current prevalence or “thousands compromised” are unverified here and must not be repeated as established facts.

Links and dates are in `../sources.md`. Do not replay incident chains against third parties.
