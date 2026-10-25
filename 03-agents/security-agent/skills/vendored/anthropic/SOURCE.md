# Source and safety review

Qualifies under PRINCIPLES.md section 1, test 1: Anthropic publishes its own Claude Code security-review workflow at https://github.com/anthropics/claude-code-security-review, inspected at the pinned commit below on 2026-10-25.

- Origin: https://github.com/anthropics/claude-code-security-review
- Author: Anthropic.
- Commit: `0c6a49f1fa56a1d472575da86a94dbc1edb78eda`.
- Retrieval date: 2026-10-25.
- License: MIT, copied as `LICENSE`.
- Quality bar: first-party security-review reference. Latest visible research update, 2026-02-11, falls outside the six-month maintenance target.
- Copied: `.claude/commands/security-review.md` and `claudecode/prompts.py`.
- Changes: content unchanged; `prompts.py` renamed to `prompts-source.md` to retain source as non-executable reference. Local wrapper documentation added.
- Excluded: action implementation, scripts, binaries, assets, dependency trees and `.git`. No upstream workflow is installed.

The upstream README says: “This action is not hardened against prompt injection attacks and should only be used to review trusted PRs.” Never execute an untrusted fork's code with CI secrets because a reviewer is called a security agent.

Review covered network instructions, shell execution, deletion, obfuscation, exfiltration and attempts to disable checks. The command runs Git discovery and requests subagents. `git remote show` may contact a remote. The prompt builder interpolates untrusted PR metadata. No direct deletion or covert exfiltration was found in these selected files.

Unsafe review assumptions remain in the originals: blanket exclusions for resource exhaustion, documentation, logging and dependency issues; claims about memory-safe languages; and treating UUIDs or environment variables as automatically trustworthy. These are not local policy. The local skills retain scoped risk categories and require complete attacker paths. The upstream JSON example also has a trailing comma and is not a valid parser fixture.
