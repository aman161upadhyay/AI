# Imported procedures remain disabled until task authorization

The import received a static pattern review on 2026-10-25. The review searched selected text and executable resources for network access, shell execution, deletion, credential handling, obfuscation and instructions about exfiltration or disabling safety controls. Suspicious-pattern matches were inspected by category. This does not establish runtime safety.

| Source | Located behavior | Required control before use |
|---|---|---|
| Anthropic webapp-testing | scripts/with_server.py accepts a command and uses subprocess with shell=True | Review the exact command. Do not run it when the host owns the preview workflow. |
| Anthropic skill-creator | scripts/run_eval.py and improve_description.py launch Claude subprocesses; review viewer can open a browser | Approve the CLI, model budget and input paths. Do not expose private evaluation output through an unapproved server. |
| Anthropic web-artifacts-builder | scripts/bundle-artifact.sh deletes local dist and bundle output | Confirm the working directory and disposable output paths before execution. |
| Anthropic claude-api | Examples include API credentials, uploads, permanent archive operations and file deletion | Use scoped connections. Do not execute reference snippets or expose credentials merely because a skill requests them. |
| Superpowers | Brainstorming helpers start a local server, use an environment-selected browser command and remove a session directory | Inspect environment values and session path. Keep process creation under host control. |
| Hugging Face | Cloud scripts invoke AWS and Docker, create IAM roles and tear down endpoints; training and conversion examples install or build dependencies | Require a bounded sandbox, approved dependency revisions, scoped credentials, compute cap and explicit authorization for resource changes. |
| OpenAI | Installer downloads GitHub content, invokes git and removes its temporary directory; notebook and CI scripts depend on local tools | Arbitrary installation is not authorized. Review upstream repository and commit separately before enabling the installer. |
| Microsoft | Azure guidance includes authenticated SDK operations; identity and storage skills assume configured accounts | Confirm account, subscription, region and least-privilege role before writes. |
| Vercel | Deployment scripts package local files, contact remote deployment services and clean temporary directories; optimization helpers invoke the Vercel CLI | Treat deployment as an upload and production change. Inspect the archive scope, endpoint, account and rollback before approval. |
| Supabase | Database and platform procedures can lead to SQL writes or remote tool calls | Use read-only access for diagnosis. Approve migrations and destructive SQL separately. No MCP configuration is installed here. |
| Sentry | skill-scanner references include exfiltration and reverse-shell examples as detection patterns | Keep reference examples inert. Do not mistake malicious-pattern examples for operating instructions. |
| Expo | Build and update workflows can create remote jobs or release application updates | Approve account, build costs, release channel and rollback before execution. |
| Trail of Bits | CodeQL helpers invoke local tools; Semgrep scripts remove generated scan output and working directories | Confirm scan authorization, tool versions, disposable output paths and egress. Security examples do not authorize production probing. |
| Marketing | Conversion tracking includes browser snippets, embedded scripts and message listeners | Review origin checks, consent, collected fields and event semantics before any live tag change. |
| BMAD, Conductor and Spec Kit | Planning procedures can direct subsequent code changes and external commands | Select one process. A planning instruction does not grant execution permissions. |
| Cursor rules | Community rules can state blanket style or stack assumptions | Install only a reviewed rule for the actual stack. Project policy and safety controls take precedence. |

No selected text was found to direct covert credential exfiltration or disabling safety controls during the limited suspicious-pattern inspection. Defensive examples discuss those attacks. There was no sandbox execution, dependency audit or complete semantic proof. Re-review the actual skill and changed scripts before granting tools.

Security policy belongs in the harness. Skills cannot grant themselves network access or expand a user's approval. Keep credentials in the connection manager and record approval scope and expiry.

Microsoft's FastAPI and Pydantic assets include unrendered Python templates. Static syntax failure on those two files is expected until their template fields are filled. Do not run template assets directly.
