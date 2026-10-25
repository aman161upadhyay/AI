# Write evals from observed errors

Start with error analysis, not a generic quality score. Hamel Husain's [product-eval guidance](https://hamel.dev/evals/) and [judge guide](https://hamel.dev/blog/posts/llm-judge/) make domain expertise and real failure observations central.

1. Collect consented, sanitized traces across real task families. Preserve tool outcomes and final artifacts. A proposed 30-to-50-trace starting sample is a working default, not statistical sufficiency.
2. Open-code observations in ordinary language before building a taxonomy. Record what failed, where it failed and the consequence. Do not force every observation into a preselected framework.
3. Group repeated mechanisms. Select failures that change a user's outcome. Distinguish failure to retrieve evidence from failure to use evidence that was retrieved.
4. Write an independent brief and minimal fixture. State permitted tools, environment reset and observable success. Remove secrets and verify rights before storage.
5. Write gold criteria before generating candidates. Use binary tests for requirements. Add positive and negative examples with explanations. A public preferred output is a comparison reference, not automatic truth.
6. Choose deterministic graders for executable requirements. Use a calibrated semantic judge for entailment or voice. Reserve human decisions for ambiguous or consequential cases.
7. Run a defective control to show that the grader can detect failure. Run a clean control to detect false positives. Test a missing-tool condition so infrastructure failure cannot become a pass.
8. Freeze the case and split development from held-out release data by task family, user/thread and near duplicates. Keep a fresh challenge set. Public benchmarks remain a separate contamination-prone slice.
9. Review disagreements with the principal expert. Change the rubric only with a recorded reason and a new version; rerun the old baseline under the new rubric.

[Anthropic's agent-eval guidance](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents) distinguishes task outcome from the final message. Verify the actual sent-record or database state rather than an agent's claim that a tool succeeded.

[OpenAI's evaluation best practices](https://developers.openai.com/api/docs/guides/evaluation-best-practices) support versioned datasets and criteria. Preserve that abstraction even when changing runners. [Eugene Yan's product-eval method](https://eugeneyan.com/writing/product-evals/) supports swapped-order comparisons; reversals require ties or review.

For writing, preserve supplied facts and commitments. For design, require interactions and fixed viewports before preference. For code, test the final tree and test sensitivity. For security, measure unauthorized effects plus benign refusal. For systems, include tenant isolation, duplicate events, failed workers and migration compatibility. These dimensions follow the corresponding agent rubrics; do not collapse them into one score.
