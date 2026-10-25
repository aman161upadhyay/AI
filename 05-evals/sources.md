# Public-eval sources

Snapshot: 2026-10-25. Tier 1 means original artifacts or first-party benchmark documentation; tier 2 means practitioner interpretation. This folder links outputs rather than redistributing upstream code.

| Title | URL | Author/org | Date | Tier | Contribution |
|---|---|---|---|---|---|
| WebDev Arena announcement | https://arena.ai/blog/webdev-arena | Arena team | Living | 1 | Pairwise web-development comparison. |
| WebDev preference dataset and terms | https://huggingface.co/datasets/lmarena-ai/webdev-arena-preference-10k/blob/main/README.md | Arena team | Historical battles; checked 2026-10-25 | 1 | Dataset rights and provenance. |
| First three preference rows | https://datasets-server.huggingface.co/rows?dataset=lmarena-ai%2Fwebdev-arena-preference-10k&config=default&split=test&offset=0&length=3 | Arena team | Retrieved 2026-10-25 | 1 | Exact prompts, outputs and votes. |
| Design Arena categories | https://www.designarena.ai/system-prompts | Design Arena | Retrieved 2026-10-25 | 1, limited | Category discovery; prompt bodies unverified. |
| SWE-bench | https://www.swebench.com/ | SWE-bench authors | Living | 1 | Verified issue-task scope. |
| SWE-bench harness | https://github.com/SWE-bench/SWE-bench | SWE-bench authors | Observed 2026-10-25 | 1 | Containerized patch evaluation. |
| Terminal-Bench | https://github.com/harbor-framework/terminal-bench | Terminal-Bench authors | Observed 2026-10-25 | 1 | Task environments and verifiers. |
| Terminal-Bench site | https://www.tbench.ai/ | Terminal-Bench authors | Living | 1 | Benchmark entrypoint. |
| Aider polyglot corpus | https://github.com/Aider-AI/polyglot-benchmark | Aider maintainers | Observed 2026-10-25 | 1 | Six-language exercise corpus. |
| Aider polyglot article | https://aider.chat/2024/12/21/polyglot.html | Aider | 2024-12-21 | 1, search-only | Discovery; full fetch failed. |
| Initial impressions of Claude Fable 5 | https://simonwillison.net/2026/Jun/9/claude-fable-5/ | Simon Willison | 2026-06-09 | 2 | Exact knowledge prompt and response links. |
| Fable/Opus knowledge outputs | https://gist.github.com/simonw/e77abf645156ade8c5c610f524226dcb | Simon Willison | Linked 2026-06-09 | 1, artifacts | Inspectable outputs. |
| GPT-5.5 knowledge output | https://gist.github.com/simonw/8d05ce836d44bd8543055c9614f7c478 | Simon Willison | Linked 2026-06-09 | 1, artifact | Alternative output. |
| The new GPT-5.6 family | https://simonwillison.net/2026/Jul/9/gpt-5-6/ | Simon Willison | 2026-07-09 | 2 | SVG prompt and setting comparison. |
| GPT-5.6 pelican grid | https://static.simonwillison.net/static/2026/gpt-5.6-pelicans.html | Simon Willison | 2026-07 | 1, artifacts | Eighteen outputs with effort labels. |
| Fable 5.1 animated pelican | https://simonwillison.net/2026/Sep/1/claude-fable-5-1/ | Simon Willison | 2026-09-01 | 2 | Continuation context and author preference. |
| Animated output | https://tools.simonwillison.net/markdown-svg-renderer?url=https%3A%2F%2Fgist.github.com%2Fsimonw%2F87282467acb3652e0f99c85155554a32#response | Simon Willison | Linked 2026-09-01 | 1, artifact | Inspectable favored animation. |
| Fable/Mythos announcement with updates | https://www.anthropic.com/news/claude-fable-5-mythos-5?lang=us | Anthropic | 2026-06; July update | 1 | Limits on verified public Mythos examples. |

Execution and calibration sources are in `../04-harness-components/evals-framework/sources.md`. Build provenance is `work/research/08-council-and-evals.md`. No benchmark was run during this documentation build.
