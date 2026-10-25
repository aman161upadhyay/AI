# Source

Origin: https://github.com/pbakaus/impeccable
Commit: 3671d50f0ac9a662ce0615e85a256110c9cd720b
Retrieved and adapted: 2026-10-25
Licence: Apache-2.0. Upstream LICENSE and NOTICE.md are preserved. NOTICE records our modifications; every adapted text file carries a modification notice.
Found by Aman through: https://x.com/pato__project/status/2114095406393036818

Decision: VENDOR AS REFERENCE-ONLY. This is a modified prose selection, not an installable skill. It contains no SKILL.md, front matter, executable helper, binary, registry metadata or dependency.

Qualifies under PRINCIPLES.md section 1, test 1: Paul Bakaus describes his own design practice and project at https://www.paulbakaus.com/impeccable-by-design/, checked 2026-10-25. The playbooks distinguish marketing from task UI, preserve factual copy and put blocked tasks before cosmetic changes. Independent experience coverage is saved in work/sources/11-x-design-skills/impeccable-independent-review.md.

Maintenance as of 2026-10-25: 87,050 stars; 5,197 forks; 63 contributor records including anonymous entries; last pinned commit 2026-10-26T02:04:24+08:00 (2026-10-25 UTC, matching the repository page); 41 open issues and pull requests combined; PR #1169 opened 2026-10-25. Sources: https://api.github.com/repos/pbakaus/impeccable, https://api.github.com/repos/pbakaus/impeccable/contributors?per_page=100&anon=true (63 records, below the page limit), and https://github.com/pbakaus/impeccable/pulls. Contributor records are not active human maintainer counts.
Inclusion evidence is separate from effectiveness: no effectiveness test executed.

Selection: plugin/skills/impeccable/reference/{critique,clarify,polish,craft-floor,mode-operate,mode-persuade,mode-read,operate}.md and body prose from plugin/skills/impeccable/SKILL.md.

Changes: the main file is renamed IMPECCABLE-REFERENCE.md and has no front matter. Removed the entire Setup section, launcher and context-loading instructions, automatic command routing, pin/unpin instructions, hooks, doctor and drift-repair operations. Replaced the full command table with the eight selected reading references. Removed references to unavailable workflow files from the main prose and made redesign permission explicit. Each playbook has a new attribution and non-execution notice; its original body remains otherwise unchanged. Local README.md, FOR-AMAN.md and NOTICE explain the adaptation. The upstream scripts, platform reference files, detector, generated assets and all other runtime components are omitted.

Reason for removal: the upstream Setup invokes scripts/impeccable, which can fetch a release binary with curl or wget, validate a same-channel checksum, chmod it and execute it. AI/PRINCIPLES.md section 5 prohibits that agent-directed download-and-execute step. This package has no way to run the launcher. Retained command examples in playbooks are historical descriptions, not authorised operations. Do not fetch missing helpers, relax CSP or inject a detector to satisfy them.

The upstream skill remains installable from https://github.com/pbakaus/impeccable if Aman separately accepts the download step and approves the runtime review. That choice is outside this reference package and does not waive the host repository's permission rules.

Conflict: craft-floor.md bans eyebrow labels absolutely, even for a pinned brief. Anthropic frontend-design explicitly says that the brief wins. Apply the host's brief-wins rule and treat that upstream ban as a taste preference, not a requirement. Visitor-mode recipes and heuristic scores are also practitioner judgements, not universal design laws.

Security review: the original launcher and requested playbooks were inspected in the initial review; full pattern results are in work/sources/11-x-design-skills/impeccable-security-scan.txt. This adaptation copies only Markdown and licence notices. Original runtime examples remain inert reference text under the explicit reading-only contract. Host-approved browser inspection is optional; report checks that could not be performed. No installation, script execution or detector activation was performed.
