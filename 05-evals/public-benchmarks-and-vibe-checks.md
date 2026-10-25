# Public benchmarks and inspectable examples

Public artifacts are a dated reference slice, not hidden gold. Use exact prompts and output links when rights do not permit copying. A preference label is not functional correctness. Research snapshot: 2026-10-25.

## Benchmarks

| Reference | What to borrow | Limits |
|---|---|---|
| LMArena and [WebDev Arena announcement](https://arena.ai/blog/webdev-arena) | Blind pairwise judgments, explicit ties and task-stratified sampling from the [public preference corpus](https://huggingface.co/datasets/lmarena-ai/webdev-arena-preference-10k). | Self-selected preferences and public-data contamination do not establish suitability for Aman's users. |
| [Design Arena categories](https://www.designarena.ai/system-prompts) | Compare outputs for the same user task with identity hidden. | The fetched page exposed category names, not verified prompt bodies or a downloadable winning-artifact corpus. Do not claim those were extracted. |
| [SWE-bench](https://www.swebench.com/) and [official harness](https://github.com/SWE-bench/SWE-bench) | Pinned issue tasks, containerized patch tests and regression evidence. SWE-bench Verified contains 500 human-filtered instances in the research snapshot. | MIT harness terms do not cover every upstream repository or issue asset. Public saturation limits generalization. |
| [Terminal-Bench](https://www.tbench.ai/) and [task repository](https://github.com/harbor-framework/terminal-bench) | Isolated terminal tasks with environments, reference solutions and verifiers. Official instructions support oracle runs through Harbor. | A reference solution is a witness, not the only correct solution. Review each task's assets and resource needs. |
| [Aider polyglot corpus](https://github.com/Aider-AI/polyglot-benchmark) | Exercism-derived tasks across C++, Go, Java, JavaScript, Python and Rust. Separate first-attempt success from repair-assisted success. | Per-track licenses need review. The [author article](https://aider.chat/2024/12/21/polyglot.html) was search-verified but its full fetch failed; no claim here depends on its task-count description. |

## Verified WebDev rows

The [rows endpoint](https://datasets-server.huggingface.co/rows?dataset=lmarena-ai%2Fwebdev-arena-preference-10k&config=default&split=test&offset=0&length=3) exposes prompts, code outputs and recorded preference. Preserve row IDs and both candidates. Review the [Dataset License Agreement](https://huggingface.co/datasets/lmarena-ai/webdev-arena-preference-10k/blob/main/README.md) before downloading or redistributing; the license is nonstandard, not implied by public access.

| Row and prompt | Recorded result | Borrow |
|---|---|---|
| `38fa1506bce8828d1996156a0a422bee`: vague responsive website brief reproduced below. | `conversation_a`, claude-3-5-sonnet-20241022, beat gemini-2.0-flash-thinking-exp-1219. | Test clarification and concrete design decisions under an underspecified request. |
| `6d09f8ab32c62f355eb30a45192e485b`: `portfolio page for a freelancer` | `conversation_b`, claude-3-5-sonnet-20241022, beat qwen-2.5-coder-32b-instruct. | Compare actual rendering and usability, not only source structure. |
| `d3c79f8667add0d2d1e33eba25dd6cec`: `Snake Game` | gemini-1.5-pro-002 versus qwen-2.5-coder-32b-instruct was a tie. | Test keyboard control, collisions, restart and score. Do not invent a winner. |

Exact row 0 prompt:

```text
Machine,
Pls make website,
all responsive like,
w/ BIG pictures ooo,
use my fav fonts,
also fancy menus with whooosh on,
load fast pls
Thanks,
Human
PS no bugs :)
```

Model labels identify historical artifacts, not current model recommendations. A single vote is not a gold functional test. Prefer stored code plus approved controlled rendering to expired live sandbox URLs.

## Willison's 2026 examples

These are inspectable practitioner examples with context, not benchmark winners.

### Fable 5 knowledge test

Simon Willison, [Initial impressions of Claude Fable 5](https://simonwillison.net/2026/Jun/9/claude-fable-5/), 2026-06-09, publishes this prompt, including its typo:

```text
List all of Simon Willion's open source projects, most recent first, each with a rough date of when they were first released
```

[Fable 5 and Opus responses](https://gist.github.com/simonw/e77abf645156ade8c5c610f524226dcb) and [GPT-5.5 response](https://gist.github.com/simonw/8d05ce836d44bd8543055c9614f7c478) provide comparison artifacts. Willison preferred aspects of Fable's broader knowledge relative to Opus 4.8; GPT listed more projects. Do not label “most entries” correct. Independently verify projects, release dates, omissions and unsupported additions.

### GPT-5.6 SVG grid

Simon Willison, [The new GPT-5.6 family: Luna, Terra, Sol](https://simonwillison.net/2026/Jul/9/gpt-5-6/), 2026-07-09. The post and the grid page show the outputs and settings but not the exact prompt text, so the prompt below is our reproduction of his long-running pelican test, not a quotation:

```text
Generate an SVG of a pelican riding a bicycle
```

The [18-output grid](https://static.simonwillison.net/static/2026/gpt-5.6-pelicans.html) includes three variants across six effort levels, with cost and setting labels. The fetched page does not declare a definitive winner. Borrow renderability, pelican anatomy, bicycle geometry and prompt-fit checks. Preserve original settings; do not infer a general quality ranking from an amusing image.

### Fable 5.1 animation continuation

Simon Willison, [Claude Fable 5.1 made me a really nice animated pelican](https://simonwillison.net/2026/Sep/1/claude-fable-5-1/), 2026-09-01, continues a prior Fable 5.1 Max SVG with:

```text
animate this
```

The [author-favored output](https://tools.simonwillison.net/markdown-svg-renderer?url=https%3A%2F%2Fgist.github.com%2Fsimonw%2F87282467acb3652e0f99c85155554a32#response) requires the earlier SVG as input context. The two-word prompt alone is not reproducible. Check valid rendering, meaningful motion and reduced-motion handling separately from author taste.

## Limits and protocol

The [Fable/Mythos first-party release page](https://www.anthropic.com/news/claude-fable-5-mythos-5?lang=us) contains release claims and later updates. Exact public Mythos 5 prompt/full-output pairs were not verified. Do not fabricate a Mythos gold example or make restricted access a prerequisite.

For every borrowed example, record original URL, prompt context, retrieval date, rights decision, output hash and what the label means. Keep source/model names hidden during preference grading. Test both orders. Run hard functional checks before subjective comparison. Report public-example results separately from fresh private cases.
