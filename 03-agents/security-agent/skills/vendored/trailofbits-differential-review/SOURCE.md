# Source and safety review

Qualifies under PRINCIPLES.md section 1, test 1: security auditor Trail of Bits publishes its own audit workflow and discovered-bug evidence at https://github.com/trailofbits/skills, inspected 2026-10-25; local HEAD dated 2026-10-23T11:26:17+02:00. Research notes record 7.8k stars and PR #475 as of 2026-10-25.

- Origin: https://github.com/trailofbits/skills
- Upstream path: `plugins/differential-review/skills/differential-review/`.
- Author: Trail of Bits.
- Commit: `196a9073ab10d35bacf111f945e02c00b2c6883a`.
- Retrieval date: 2026-10-25.
- License: CC-BY-SA-4.0; full upstream `LICENSE` copied.
- Quality bar: maintained audit methodology from an established security auditor.
- Copied unchanged: `SKILL.md`, `methodology.md`, `adversarial.md`, `reporting.md`, `patterns.md`.
- Changes: local wrapper documentation only.
- Excluded: plugin/subagent implementations, assets, scripts, binaries, dependencies and `.git`.

Share-alike notice: preserve Trail of Bits attribution, pin and change notices. Adaptations of the selected material must remain CC-BY-SA-4.0.

Safety review covered each selected file for network calls, shell execution, deletion, obfuscation, exfiltration and disabled controls. Methodology invokes Git checkout and GitHub CLI; checkout mutates a worktree and GitHub CLI may use ambient authentication. Reporting allows Desktop/home/temp fallback writes. Other references invoke uninstalled skills or issue-writer. Contract exploit examples are analysis fixtures, not authority to transact. No covert exfiltration, obfuscated installer or safety-disabling instruction was found.

Use only a disposable checkout and an approved output directory. Do not execute companion commands automatically. Caller counts and missing tests determine investigation priority, not vulnerability severity. Illustrative impact amounts and example CVEs are not verified incidents. The local report format supersedes upstream formatting.
