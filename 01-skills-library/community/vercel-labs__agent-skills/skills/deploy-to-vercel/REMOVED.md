# Removed deploy-to-vercel skill

Removed the entire skill: `SKILL.md`, `resources/deploy.sh`, `resources/deploy-codex.sh`, and local `README.md` / `FOR-AMAN.md` files in the skill and resources folders.

Reason (SEC-003, SEC-006): both fallback scripts posted a broad working-directory archive to https://claude-skills-deploy.vercel.com/api/deploy, ignoring .gitignore and .vercelignore. Exclusions covered only node_modules, .git, .env and .env.*; other credentials and private data remained eligible. Supplied .tgz files were uploaded unchanged. The preferred git path staged everything and could push a production branch after generic preview approval.

Upstream: https://github.com/vercel-labs/agent-skills/tree/063bee94c3f4df8453406c830b0a7df0f2860278/skills/deploy-to-vercel

Not available for installation. See excluded.md and the upstream-root SOURCE.md. Reconsider only after approved file manifests, deployment-ignore handling, sensitive-file scans, exact destination/payload approval, rejection of unreviewed tarballs, and enforced preview/production approval boundaries.
