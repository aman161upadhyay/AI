# Source

Qualifies under PRINCIPLES.md section 1, test 1: Anthropic's official skills repository, https://github.com/anthropics/skills, inspected 2026-10-25; local HEAD dated 2026-10-09T18:45:49Z. Anthropic publishes guidance for its own agent system.

- Origin: https://github.com/anthropics/skills/tree/main/skills/canvas-design
- Commit: `dbd4588f9e1033efb41dad4bef2f7947c8993d44`
- Retrieved: 2026-10-25.
- License: Apache-2.0 from the skill-specific license.
- Quality: trusted first-party static-design procedure.
- Changes: upstream `SKILL.md` unchanged; added local metadata and duplicate `LICENSE`. Excluded all font binaries and their directory, not only large files. No images, archives, videos, dependencies or Git metadata copied.
- Security review: inspected instructions for network calls, shell, deletion, obfuscation, exfiltration and safety bypass. Upstream requests font downloads and assumes a local font directory. No downloader is included. Require explicit network permission and asset-license verification. No exfiltration or safety-disable instruction was found.
