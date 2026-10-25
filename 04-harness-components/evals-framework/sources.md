# Sources

Research snapshot: 2026-10-25. Tier 1 means official documentation or original research. Tier 2 means named practitioner guidance. No external framework code is vendored here.

| Title | URL | Author/org | Date | Tier | Contribution |
|---|---|---|---|---|---|
| Demystifying evals for AI agents | https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents | Anthropic | 2026-01-09 | 1 | Outcome, trial and grader separation. |
| Your AI Product Needs Evals | https://hamel.dev/evals/ | Hamel Husain | 2024-03-29; living | 2 | Failure-led evaluation. |
| LLM-as-a-Judge guide | https://hamel.dev/blog/posts/llm-judge/ | Hamel Husain | Living; revision unverified | 2 | Principal expert, labels and rubric drift. |
| Product Evals in Three Simple Steps | https://eugeneyan.com/writing/product-evals/ | Eugene Yan | Date unverified | 2 | Minimal loop and swapped comparisons. |
| Evaluation best practices | https://developers.openai.com/api/docs/guides/evaluation-best-practices | OpenAI | Living | 1 | Portable datasets and criteria. |
| Define success criteria and build evaluations | https://platform.claude.com/docs/en/test-and-evaluate/develop-tests | Anthropic | Living | 1 | Specific acceptance checks. |
| Deprecations | https://developers.openai.com/api/docs/deprecations | OpenAI | Notice 2026-06-03 | 1 | Evals API read-only and shutdown dates. |
| Inspect | https://inspect.aisi.org.uk/ | UK AISI | Living | 1 | Canonical runner architecture. |
| promptfoo intro | https://www.promptfoo.dev/docs/intro/ | promptfoo | Living | 1 | Optional prompt and red-team layer. |
| DeepEval repository | https://github.com/confident-ai/deepeval?tab=readme-ov-file | Confident AI | Observed 2026-10-25 | 1 | Alternative pytest-oriented runner. |
| Braintrust evaluation | https://www.braintrust.dev/docs/evaluate | Braintrust | Living | 1 | Optional hosted experiment tracking. |
| Judging LLM-as-a-Judge | https://proceedings.neurips.cc/paper_files/paper/2023/hash/91f18a1287b398d378ef22505bf41832-Abstract-Datasets_and_Benchmarks.html | Zheng et al. | 2023 | 1 | Bias controls and domain limits. |

Local design input: `work/research/08-council-and-evals.md`, section 5, plus section 5 eval designs in research notes 03 through 07 and 09. These working files are build provenance, not required runtime dependencies. Domain-specific examples remain in the corresponding agent eval sets.
