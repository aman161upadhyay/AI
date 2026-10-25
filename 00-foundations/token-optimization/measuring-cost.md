# Measure accepted-task cost

Use provider usage as the billing source of truth. Local estimators help diagnose sessions but can omit tool charges or differ from invoices.

## Per-run record

Record task ID, baseline and candidate identities, model IDs, harness revision and pricing date. Record uncached input, cache writes by TTL, cache reads and output tokens. Include every child agent and compaction call.

Record tool costs, retry count, verification duration, wall time, human review minutes, acceptance status and escaped regressions. Store redacted receipts rather than credentials or full private prompts.

```text
model_cost =
  uncached_input * input_rate
  + sum(cache_write_by_ttl * write_rate_by_ttl)
  + cache_read * read_rate
  + output * output_rate
total_run_cost = sum(all_model_calls) + tool_costs
cost_per_accepted_task = sum(costs_of_all_attempts) / accepted_tasks
```

Normalize units when prices are per million tokens. Avoid counting child cost twice if children already appear in the call table. If no task was accepted, report the denominator as zero and the metric as undefined rather than omitting failures.

Track human review minutes separately unless an explicit valuation converts them to dollars. Subscription usage estimates are not automatically incremental cash charges.

## Compare configurations

1. Freeze task, baseline commit, fixtures, environment, model snapshot and evaluator.
2. Run a baseline on representative tasks. Keep hidden checks read-only.
3. Change one component, such as skill loading or prefix layout.
4. Run paired tasks at least three times and retain every failure.
5. Compare acceptance, regressions, unauthorized actions, median/P95 cost and review time.
6. Check long-session recovery and genuine blocker handling.

Promote a cost change only if acceptance quality does not regress. Safety controls may justify increased cost. Three repeats do not establish statistical significance; choose a threshold after measuring variance.

The research inspected ccusage as a conditional local tool. Its estimates may omit charges and differ from invoices. Pin a reviewed version and use matching help rather than executing an unreviewed latest-package install.
