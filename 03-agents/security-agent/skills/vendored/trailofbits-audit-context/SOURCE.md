# Source and safety review

Qualifies under PRINCIPLES.md section 1, test 1: security auditor Trail of Bits publishes its own audit workflow and discovered-bug evidence at https://github.com/trailofbits/skills, inspected 2026-10-25; local HEAD dated 2026-10-23T11:26:17+02:00. Research notes record 7.8k stars and PR #475 as of 2026-10-25.

- Origin: https://github.com/trailofbits/skills
- Upstream path: `plugins/audit-context-building/skills/audit-context-building/`.
- Author: Trail of Bits.
- Commit: `196a9073ab10d35bacf111f945e02c00b2c6883a`.
- Retrieval date: 2026-10-25.
- License: CC-BY-SA-4.0, full upstream `LICENSE` copied.
- Quality bar: established security auditor with maintained audit skills, as recorded in the research.
- Changes: selected Markdown copied unchanged. Local wrapper documentation added.
- Excluded: plugin runtime, agent configuration, SVG assets, scripts, binaries, dependencies and `.git`.

Share-alike notice: retained upstream content and adaptations of that content remain under CC-BY-SA-4.0. Preserve attribution to Trail of Bits, the origin/pin and change notices. Independent local procedures are separate works, not relicensed by this collection.

Reviewed each selected file for network calls, shell execution, deletion, obfuscation, exfiltration and disabled controls. The skill delegates to a Workflow and namespaced subagent and expects disk output; those implementations are absent and were not approved for execution. The references contain C/Solidity examples with external calls and memory operations as analysis subjects. No instruction to export secrets, delete data or disable controls was found. Load as a reference only; the local task contract overrides routing and output paths.
