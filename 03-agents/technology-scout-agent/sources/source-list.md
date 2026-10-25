# Weighted source list

Weight describes how to use evidence, not a numerical truth score. Priority 1 gets verification attention first. Priority 2 supports discovery. A source's role remains claim-specific.

These URLs come from the supplied research watchlist. Except for the cited documentation captures, they were not all individually fetched. Verify availability and feed terms before subscribing.

| Priority | Endpoint or subscription | Weight and use | Required check |
|---|---|---|---|
| 1 | [Anthropic news](https://www.anthropic.com/news), [engineering](https://www.anthropic.com/engineering), [API release notes](https://platform.claude.com/docs/en/release-notes/overview) | Primary for announcements and documented API behavior. Interested testimony for comparative results. | Compare app and API behavior. Record exact model/version and effective date. |
| 1 | [OpenAI news](https://openai.com/news/), [API changelog](https://developers.openai.com/api/docs/changelog) | Primary for availability claims, API changes, and deprecations. | Verify account/region availability, current price basis, and effective dates. |
| 1 | [DeepMind blog](https://deepmind.google/discover/blog/), [Gemini API changelog](https://ai.google.dev/gemini-api/docs/changelog) | Research intake and first-party API changes. | A research result does not establish an accessible product. Check exact endpoint. |
| 1 | [Hugging Face blog](https://huggingface.co/blog) and linked original model cards | Discovery of open-weight artifacts with publisher evidence. | Check publisher, weight license, revision, hardware, and data policy. Code license is separate. |
| 1 | arXiv [cs.AI](https://arxiv.org/list/cs.AI/recent), [cs.CL](https://arxiv.org/list/cs.CL/recent), [cs.LG](https://arxiv.org/list/cs.LG/recent) | Primary preprint evidence for the authors' experiments. Not peer review or independent replication. | Read methods and limitations. Follow code, data, revisions, and later evidence. Deduplicate cross-lists. |
| 1 | [arXiv RSS/Atom documentation](https://info.arxiv.org/help/rss.html) | Verified feed configuration source. | Follow official syntax and API terms. Do not infer that a feed result has been read in full. |
| 1 | GitHub Releases for approved watched repositories; [release documentation](https://docs.github.com/en/repositories/releasing-projects-on-github/about-releases) | Primary evidence for packaged versions and release notes. | Tag date can differ from release date. Inspect compatibility, security advisories, tests, and pinned commits. |
| 2 | [Hacker News](https://news.ycombinator.com/), [Show HN](https://news.ycombinator.com/show) | Leads, implementation reports, and failure anecdotes. Upvotes do not establish reliability. | Follow originals. Attribute a comment as one person's report. Check whether a reproduction exists. |
| 2 | [GitHub Trending, weekly](https://github.com/trending?since=weekly) | Emerging-tool discovery only. | Inspect license, meaningful maintenance, contributors, issues/PRs, tests, and installation risk. Popularity does not establish fitness. |
| 2 | [Simon Willison](https://simonwillison.net/) | Accountable practitioner observations and reproducible artifact leads. | Preserve prompt, input context, settings, and the author's actual judgment. Do not invent a winner. |

For each shortlisted item, record claim, source ID, primary URL, version, dates, exact locator, evidence origin, vendor/independent/local status, and unknowns. Use the research agent's notes spine when a topic needs a longer investigation.

Official material receives priority for what an organization released. Independent reproduction receives more weight for comparative claims when conditions fit. Local workload tests receive more decision weight than public scores when privacy and reproducibility checks pass.
