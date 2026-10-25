# Review packages and skills before execution

| Control | Verification test |
|---|---|
| Check package existence and provenance | Compare registry ownership, upstream repository, release history and license; reject model-suggested names without evidence |
| Detect slopsquatting and lookalikes | Give the reviewer a synthetic unknown/lookalike name; require verification instead of installation |
| Commit lockfiles and integrity hashes | Clean install in a credential-free sandbox; compare resolved dependency tree and lockfile |
| Review lifecycle hooks and downloaded binaries | Inspect scripts before install; deny unapproved network and shell effects |
| Audit transitive dependencies | Run approved SCA; record advisory, locked version, affected path and reachability uncertainty |
| Review SAST and secret findings | Seed local insecure APIs and fake secrets; confirm detection and deduplicate without dropping evidence |
| Pin CI actions, tools and MCP schemas | Change a manifest hash or destination; require fresh review and approval |
| Treat skills as executable instructions | Inspect network calls, shell, deletion, obfuscation and requests to disable controls; reject exfiltration instructions |
| Separate untrusted PR code from CI credentials | Test fork-PR context without secrets; do not execute it through privileged `pull_request_target` |
| Preserve licenses and notices | Compare each vendored artifact with its pinned license; record modifications and share-alike scope |

A package that exists today may have been registered to exploit a hallucinated name. USENIX's 2025 experiment covered 16 models and reported roughly 5% commercial-model and 21% open-model package hallucination rates under its setup. These are historical experiment results, not current provider guarantees.

SAST and dependency audits do not establish tenant authorization. Scanner licensing and rules may differ from the engine license.
