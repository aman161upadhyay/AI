# Deployment-plan contract

| Section | Required content |
|---|---|
| Target | Approved project/environment, owner, runtime/package versions, regions/residency |
| Service inventory | Frontend/API/worker/database/cache/storage/email/payment/telemetry responsibilities |
| Secret inventory | Secret references, consumer, scope, rotation, environment; never values |
| Preview isolation | Separate data/credentials, protected access, sandbox providers, disabled external writes |
| CI gates | Type/lint/test/build, tenant-negative checks, dependency/license review |
| Database release | One migration runner, approved rollout, backfill/lock budgets, code/schema overlap |
| Rollout | Health checks, staged traffic, smoke tests, alert thresholds, stop owner |
| Recovery | Code rollback, feature disable, data rollback limits, backup retention, timed restore drill |
| Observability | Journey metrics, redacted logs, trace correlation, queue/DB saturation, on-call owner |
| Cost | Baseline/peak assumptions, compute/storage/egress/providers, spend/quota alerts |
| Validation | Login/tenant switch/upload/webhook/job tests on the actual target; blocked checks listed |

Record target confirmation before the first deployment. Code rollback does not reverse data changes or provider side effects.
