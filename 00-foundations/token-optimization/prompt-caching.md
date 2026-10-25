# Prompt caching

Caching reuses computation for matching prompt prefixes. It is not persistent agent memory and does not make irrelevant context useful.

As-of date: 2026-10-25. These semantics reproduce the verified research snapshot, including model-specific differences. Check the current provider documentation and installed SDK before configuring an application. CLI-managed caching may not expose application-level controls.

## Anthropic

Source: [Prompt caching](https://platform.claude.com/docs/en/build-with-claude/prompt-caching), Anthropic, living documentation, Tier 1.

- The reusable prefix consists of exact content through the cache breakpoint.
- Explicit breakpoints or supported automatic `cache_control` identify reusable content.
- The invalidation hierarchy is `tools -> system -> messages`. Changing an earlier layer invalidates downstream content.
- Default TTL is five minutes. A one-hour option exists where documented.
- Five-minute cache writes cost 1.25 times base input. One-hour writes cost 2 times base input.
- Minimum cacheable length varies by model. Breakpoint/block restrictions include a documented 20-block lookback. Check the model's current limits rather than inferring them.
- Images, tool choice and thinking-block preservation have model-specific rules.

The fetched Sonnet 4.6 table lists $3 per million base-input tokens, $3.75 for five-minute writes, $6 for one-hour writes and $0.30 for reads. These prices are snapshot evidence, not a recommendation to choose that model. Later models in the same research capture use 0.05x or 0.025x read multipliers. Do not apply the legacy 0.1x read multiplier universally.

Illustration using the legacy 1.25x write and 0.1x read: two uses cost `1.25 + 0.1 = 1.35` input units instead of `2`, a 32.5% reduction for those prefix tokens. Ten uses cost `1.25 + 9 × 0.1 = 2.15` instead of `10`, a 78.5% reduction. This assumes all later calls hit within the TTL. It excludes new input, outputs and tools.

## OpenAI

Source: [Prompt caching](https://developers.openai.com/api/docs/guides/prompt-caching.md), OpenAI, living documentation, Tier 1.

The longest matching rendered prefix can be reused. Exact matching is not semantic similarity. Model choice, tool definitions, `parallel_tool_calls` and reasoning settings rendered before the breakpoint can affect reuse.

| Model generation in the captured documentation | Configuration and retention | Cost semantics in the capture |
|---|---|---|
| Supported newer GPT-5.6+ family | `prompt_cache_options` and `prompt_cache_breakpoint`; default 30 minutes, option for 12 hours. | 30-minute writes 1.25x input; 12-hour writes 2.5x; reads generally 0.1x. |
| GPT-6.1 Sol exception | Verify the supported newer configuration. | Read multiplier 0.05x in the capture. |
| Earlier supported models | Older `prompt_cache_retention` semantics; in-memory or supported extended 24-hour retention. | No extra write fee in the older mode; read rates depend on model. |

Do not send new fields to old model/SDK combinations. Do not replace the captured newer semantics with the older blanket claim that all OpenAI caching is implicit and write-free. Conversely, do not assume every current endpoint supports explicit breakpoints.

## Operational checks

Record model ID, API/SDK version, price snapshot, TTL, uncached input, cache writes and cache reads. Confirm actual cache hits in provider usage before claiming savings.

Keep tool enumeration stable. Append observations after reusable content. Avoid changing timestamps or run IDs in the static prefix. A compaction or configuration rewrite can replace the prefix and reduce hit rate.

Cold requests, expired entries and one-off prefixes can make write premiums exceed savings. Compare total accepted-task cost, not hit percentage alone. Cache retention is also not an application data-deletion guarantee; inspect provider retention and privacy controls separately.
