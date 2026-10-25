# Removed vercel-cli-with-tokens skill

Removed files: `SKILL.md` and local `README.md` / `FOR-AMAN.md`.

Reason (SEC-004): token-discovery commands printed credentials from environment variables and files into tool output and model transcripts.

Upstream: https://github.com/vercel-labs/agent-skills/tree/063bee94c3f4df8453406c830b0a7df0f2860278/skills/vercel-cli-with-tokens

Not available for installation. See excluded.md and the upstream-root SOURCE.md. Authentication must use presence-only checks, redacted identity/status calls, and secret-manager or browser provisioning outside model context.
