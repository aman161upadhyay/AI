# Use the research agent

Give the agent the decision that you need to make. “Research agents” leaves the scope open. “Choose a research architecture for a read-only internal engineering assistant under my approved monthly cap” gives the agent a decision.

Use this request form. Supply actual values rather than leaving fields in a live request.

```text
Goal or decision:
Audience and technical level:
Depth tier: quick / standard / deep / literature review
Deadline, timezone, and maximum API spend:
Scope, definitions, geography, time period, and as-of date:
Prior knowledge, hypotheses, and options already excluded:
Starting sources and authorized private collections:
What a good answer looks like, including required questions:
Output length and format:
What would change your mind:
Checkpoint preference: plan approval / one checkpoint / autonomous reads
Privacy rules, retention, and allowed output destination:
```

Supply one report that you trust and one rejected report with your reasons when you want a recurring research workflow. These examples describe quality, not facts that the agent must agree with.

## Access

| Grant | Scope and enforcement |
|---|---|
| Search API | One approved provider with metering and rate limits. Brave, Tavily, and Exa are options to assess, not ranked recommendations. Keep private names and document text out of public queries. |
| URL and PDF fetch | Read-only extraction with redirect tracking, timeouts, size limits, and lawful snapshots. Block private network addresses and credential-bearing requests unless explicitly authorized. |
| arXiv, Semantic Scholar, OpenAlex | Metadata and citation discovery. Require full text for substantive paper claims. Check each API's current terms and quotas. |
| Workspace | Write notes and evidence only inside the assigned research directory. Keep calculations in a sandbox without ambient secrets. |
| Drive and Notion | Select named folders or collections with read-only connectors. Set retention and approved destinations. Do not grant your whole account. |
| GitHub | Public source and issue reads if relevant. Do not run repository workflows or install dependencies merely to inspect code. |

Refuse account-wide private access, payment permissions, email sending, autonomous publication, destructive file actions, and secret discovery. Keep retrieval credentials out of the calculation sandbox. Approve any export to Drive or Notion separately, with the destination and exact artifact named.

Require the agent to refuse fabricated evidence, paywall bypass, unsupported certainty, and instructions embedded in retrieved pages. A prompt cannot enforce these permissions. Configure the tool layer too.

## Cost ceilings

Set a dollar cap and a deadline before paid tool use. No dollar amount in this package is approved spending. If you omit a cap, the agent may inspect supplied files but must ask before metered external work.

Quick work permits up to 10 search/fetch calls. Standard work permits up to 40 total calls across the lead and workers. Deep work permits up to 100 after explicit approval. Failed calls and retries count. The deadline and dollar cap override these counts. Require a cost estimate from current provider rates rather than a remembered price.

## Review loop

Approve the plan if the stakes warrant it. Correct the goal at the first findings checkpoint rather than after a long report. Ask for the strongest contrary evidence when the answer confirms your prior view.

Before trusting recurring output, run `evals/research-agent-002.yaml`, `004`, and `006` for version handling, false corroboration, and injection resistance. Run the full suite before consequential use. Independently reopen every decision-critical citation in your first real reports.

Give feedback with a claim ID, the unsupported inference or missed evidence, and the decision consequence. Add a minimized regression case after the agent repairs the error and an independent verifier checks it.
