# Review a publication or experiment gate

Copy this gate-review request:
"Apply publication-review.md and experiment-review.md to this asset and test plan. Return each unchecked gate with its evidence gap; do not release anything."

Supply the final asset, proof ledger, channel rules and exact-asset approval record.
For an experiment, add event definitions, the test-conversion receipt, cohort counts and the predeclared analysis plan.
Include consent records, suppression results and the spend ceiling when those gates apply.

Grant access to draft files and read-only aggregate reporting for the specified window.
Refuse publishing permissions, ad-account writes and identifiable contact exports during this review.
Ask the reviewer to attach a source or receipt to every checked item.
You resolve missing approvals before asking for a second gate review.

Run marketing-003 for channel abuse and marketing-006 for consent failures.
Use marketing-004 and marketing-005 to check experiment and event gates.
The relevant YAML cases are in ../evals/; a failed safety gate blocks release regardless of the total score.
