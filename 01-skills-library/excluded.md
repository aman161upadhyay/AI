# Excluded and link-only sources

These decisions apply to the inspected snapshot of 2026-10-25. Exclusion is not a claim that every item in a source is bad.

| Source | Decision and reason |
|---|---|
| vercel-labs/agent-skills: deploy-to-vercel | Removed at 063bee94c3f4df8453406c830b0a7df0f2860278 (SEC-003, SEC-006). Both resources/deploy.sh and deploy-codex.sh posted working-directory archives to https://claude-skills-deploy.vercel.com/api/deploy, excluding only node_modules, .git, .env and .env.* while ignoring .gitignore and .vercelignore; other credentials and private data remained eligible. Opaque .tgz inputs passed through unchanged. SKILL.md:56-83 used git add ., commit and push without checking the current/configured production branches, allowing generic preview approval to trigger production. Entire skill removed; REMOVED.md retained. |
| vercel-labs/agent-skills: vercel-cli-with-tokens | Removed at the same pin (SEC-004). SKILL.md:20,28,42 printed raw credentials via printenv and grep into tool output/model transcripts. Entire skill removed; REMOVED.md retained. Reconsider only with presence-only checks and authentication outside model context. |
| huggingface/skills: convert_to_gguf.py helper | Removed at fabc634a893f62ad5c2039830397efa35fa62715 (SEC-002), not the trainer skill. Lines 130,152 trusted model-repository Python without revisions; unpinned llama.cpp clone/dependency install/build/execution shared a process with HfApi uploads and credentials. scripts/REMOVED.md records the required review boundaries. |
| https://github.com/nextlevelbuilder/ui-ux-pro-max-skill | EXCLUDE whole skill at d14efff8ed1faa4187f004f79926f428c8074ec7. Verified examples: work/vendor/nextlevelbuilder__ui-ux-pro-max-skill/src/ui-ux-pro-max/data/ui-reasoning.csv:2 prescribes glassmorphism for data-heavy SaaS; the same CSV at :9 assigns neumorphism to healthcare. scripts/design_system.py applies those rules. These mappings have no cited supporting studies. Approximate adoption as of 2026-10-25: 140,300 stars, 14,900 forks, 569 watchers, 103 contributor entries and 90 open issues plus PRs. MIT and adoption do not validate the mappings. See work/research/11-x-post-design-skills.md for evidence and limits. |
| https://github.com/pbakaus/impeccable | Vendored as reference-only at 3671d50f0ac9a662ce0615e85a256110c9cd720b; launcher excluded. See [the modified prose selection](community/pbakaus__impeccable/README.md). Apache-2.0 permits this adaptation with notice. IMPECCABLE-REFERENCE.md has no front matter or runtime setup; no SKILL.md, launcher, detector or hooks were imported. Retained command examples in playbooks are inert reference text. Approximate adoption as of 2026-10-25: 87,500 stars, 5,200 forks and 61 contributor entries. |
| ibelick/ui-skills: create-design-md and ui-skills-root | EXCLUDE these subskills at 59193a75432e5f41c6980f53b9e6a7bd56919947, not the six accepted sibling procedures. create-design-md requires unpinned npx @google/design.md for spec, lint, export and diff. ui-skills-root invokes the unpinned registry CLI. Reconsider after a pinned local tool audit and an explicitly approved adaptation. |
| ibelick/ui-skills: baseline-ui | EXCLUDE this subskill at the same pin. Mandatory Tailwind and Motion, a blanket purple-gradient ban and restrictions on custom easing conflict with the brief-led Anthropic skill and work/research/05-design-and-ui.md. Six more specific procedures were selected instead. |
| emilkowalski/skills: eleven unselected siblings | Not imported in this four-skill selection. They include broader construction, dependency choice and Swift procedures. This is a scope decision, not a finding that every sibling fails quality review. |
| https://github.com/ComposioHQ/awesome-claude-skills | Not imported. Five Anthropic example bodies are byte-identical; derived MCP and authoring copies diverge without evidence of added benefit. Connector procedures add dependency and credential risk. Nested document licences remain restrictive. |
| https://github.com/linny006/awesome-agent-skills | Rejected as curation authority. Metadata tracker, no actual SKILL.md procedures, missing root licence grant. |
| https://github.com/uhub/awesome-agent-skills | Rejected as curation authority. Broad README-only list with no skill evaluation evidence or observed licence. |
| https://github.com/hesreallyhim/awesome-claude-code | Link only. CC-BY-NC-ND-4.0 prohibits the intended catalogue remix. |
| https://github.com/anthropics/claude-code | Proprietary root. Do not infer reuse rights from runtime examples. |
| https://github.com/remotion-dev/skills | Link only. No licence file observed in the clone. |
| Anthropic docx/pdf/pptx/xlsx | Proprietary individual licences; see anthropic/restricted-skills.md. |
| Anthropic doc-coauthoring | Missing individual grant in the mixed-licence repository; link only. |
| https://github.com/anthropics/claude-plugins-official | Frontend-design is byte-identical to canonical Anthropic skill. Marketplace externals require separate audits. No duplicate plugin copied. |
| https://github.com/google-gemini/gemini-cli | Runtime linked, not vendored. Large executable harness is outside an on-demand procedure library. |
| https://github.com/affaan-m/everything-claude-code | Bulk framework and internal mirrors excluded. Overlap with chosen development procedures; independent efficacy evidence absent. |
| Sentry security-review | OWASP-derived CC-BY-SA references excluded from the Apache pack. Trail of Bits provides an isolated share-alike security pack. |
| OpenAI unselected skills | Only individually checked Apache selections copied. No root licence assumed. |
| Microsoft unselected SDKs | Only 12 relevant Python/service skills selected. Actual stack fit is still required before activation. |
| Marketing unselected procedures and tools | Seventeen decision-focused skills copied. Unneeded connectors and automatic external actions excluded. |
| Fonts, videos, archives, caches, large images | Omitted by import policy; exact selected-tree omissions recorded in SOURCE.md. Missing assets can prevent upstream examples from running unchanged. |

Maintenance policy: replace the source decision after a new licence review and a task-level evaluation. Popularity alone is not grounds for admission.

## Exact duplicate decisions

The inspected research compared bytes, not topic labels. Composio's `brand-guidelines`, `canvas-design`, `internal-comms`, `theme-factory` and `webapp-testing` skill bodies match Anthropic's copies. Only the Anthropic copies are stored here. `frontend-design` matches the Anthropic skills, Claude Code and official-plugin copies; the individually licensed skills source is canonical.

Composio's `mcp-builder`, `skill-creator` and `slack-gif-creator` differ from current upstream. They are divergent revisions, not new independent capabilities. No extra copy is admitted without a diff review and a task-level evaluation.
