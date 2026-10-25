# Prompt for the model that will execute the task

Use clear goals and checkable outputs before adding reasoning instructions. OpenAI's reasoning guidance recommends simple prompts and avoiding explicit chain-of-thought requests. Gemini also performs internal reasoning. Historical “think step by step” results do not transfer automatically to reasoning-trained models.

| Concern | Current practice | Compatibility caveat |
|---|---|---|
| Reasoning effort | Choose supported API effort against task success, cost, and latency | Exact options vary by model. GPT-5.1 documentation includes `none`; do not assume every model supports it. |
| Agentic eagerness | State permitted exploration, completion conditions, and escalation | “Keep going” without an external limit can cause excessive calls. |
| Instruction hierarchy | Put durable policy in system/developer messages; task in user message; retrieved text in data | Verify the actual provider's message semantics and persistence across calls. |
| Prefill | Replace formatting prefills with supported structured output | Anthropic's observed guidance says assistant prefills are unsupported starting with Claude 4.6. Recheck the exact model ID and API. |
| Demonstrations | Start zero-shot for reasoning models; add examples for observed ambiguity | Google broadly recommends examples. Local task/model tests resolve this difference. |
| Visible reasoning | Request source spans, calculations, tests, and a concise rationale | Do not request hidden reasoning transcripts or mistake verbose explanations for verification. |
| Long documents | Put evidence first and the specific query last | Do not bury high-priority policy inside documents. |
| Old self-check recipes | Retain only improvements that pass regression tests | Current instruction-following models may amplify conflicting “always” rules. |

Record model ID, API version where applicable, reasoning setting, tool definitions, prompt version, and observation date for each benchmark. Re-run compatibility checks after model changes.

Sources: OpenAI reasoning best practices and GPT-5/5.1 guides; Anthropic current prompting guidance; Gemini strategies, listed in [sources](../sources.md). Snapshot: 2026-10-25. Historical prompt improvers may generate CoT or prefill instructions that conflict with current guidance.
