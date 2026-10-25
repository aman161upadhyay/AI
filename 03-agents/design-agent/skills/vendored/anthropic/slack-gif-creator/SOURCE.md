# Source

Qualifies under PRINCIPLES.md section 1, test 1: Anthropic's official skills repository, https://github.com/anthropics/skills, inspected 2026-10-25; local HEAD dated 2026-10-09T18:45:49Z. Anthropic publishes guidance for its own agent system.

- Origin: https://github.com/anthropics/skills/tree/main/skills/slack-gif-creator
- Commit: `dbd4588f9e1033efb41dad4bef2f7947c8993d44`
- Retrieved: 2026-10-25.
- License: Apache-2.0 from the skill-specific license.
- Quality: first-party scoped GIF workflow with validation concepts.
- Changes: skill unchanged; Python utilities and requirements excluded under the Markdown-only rule. Added metadata and duplicate license. No binary assets copied.
- Security review: inspected instruction text and searched utilities for network calls, shell, deletion, obfuscation, exfiltration and safety bypass. The skill contains pip installation and local file-write examples. No exfiltration or safety-disable instruction was found. Utilities are not enabled or shipped. Revalidate channel limits before use.
