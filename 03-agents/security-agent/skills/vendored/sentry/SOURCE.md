# Source and safety review

Qualifies under PRINCIPLES.md section 1, test 1: Sentry publishes guidance used by its own team at https://github.com/getsentry/skills, with underlying first-party OWASP authorization guidance linked below; inspected 2026-10-25. Local HEAD dated 2026-10-23T14:17:27-07:00; research notes record 32 contributors and PR #180 as of 2026-10-25.

- Origin: https://github.com/getsentry/skills
- Upstream path: `skills/security-review/references/authorization.md`.
- Authors: Sentry / Functional Software, Inc.; underlying OWASP Cheat Sheet Series, OWASP Foundation, https://cheatsheetseries.owasp.org/.
- Commit: `d12f250460ffd961f549dbebf7eeb0cf4afd4c2e`.
- Retrieval date: 2026-10-25.
- Quality bar: first-party engineering reference with explicit source attribution.
- Licenses: root Apache-2.0 copied as `LICENSE`; artifact-specific upstream notice copied as `owasp-notice.md`. The authorization reference is CC-BY-SA-4.0. Full legal text copied from the inspected Trail of Bits upstream license as `LICENSE-CC-BY-SA-4.0`.
- Changes: authorization content and notice unchanged. Local wrapper documentation added.
- Excluded: the broad review skill, other references, scripts, assets, binaries, dependencies and `.git`.

Share-alike notice: retain Sentry and OWASP attribution and license links. Adaptations of the authorization reference must use CC-BY-SA-4.0; do not redistribute it as Apache-only.

Reviewed selected content for network calls, shell execution, deletion, obfuscation, exfiltration and disabled controls. It contains grep commands, HTTP test calls and destructive application examples, not hidden execution. Do not run them against real targets. No covert exfiltration or safety-disabling instruction was found.

Two examples need explicit correction before use: string `startswith(base_dir)` does not establish path containment against sibling prefixes or races; use a tested containment strategy with appropriate filesystem handling. The ID enumeration example wrongly treats every successful response as IDOR without checking ownership. Test expected subject/object policy instead.

The broader upstream SKILL.md was inspected but not copied. Its instruction to omit paths that require prior authentication can hide real authenticated-user vulnerabilities. The active local review procedure does not inherit that exclusion.
