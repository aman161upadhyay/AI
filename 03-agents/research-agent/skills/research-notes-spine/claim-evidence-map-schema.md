# Claim-to-evidence schema

Store a sequence in `claims.yaml`. Each record is one externally checkable assertion or one explicitly labeled inference.

| Field | Type and meaning |
|---|---|
| `claim_id`, `atomic_claim` | Stable ID and exact wording. Split independently testable clauses. |
| `claim_type` | `observed`, `source-assertion`, `inference`, or `proposal`. |
| `question_ids`, `report_section` | Coverage links and intended draft location. |
| `as_of_date`, `scope_limits` | Observation date and population, version, definitions, or geography. |
| `supporting_evidence`, `contradicting_evidence` | Sequences of evidence records defined below. Empty means no evidence recorded, not proof of absence. |
| `confidence`, `confidence_basis` | `high`, `medium`, `low`, or `unknown` with evidence-based justification. These labels are not calibrated probabilities. |
| `verification_status` | `unreviewed`, `verified`, `qualified`, `unsupported`, or `inaccessible`. |
| `audit` | Draft revision, verifier, timestamp, checked locator, verdict, and repair/retest result. |
| `supersedes`, `superseded_by`, `change_reason` | Nullable claim IDs and explicit reason for reversal. |

Each evidence record contains `source_id`, `exact_excerpt`, `locator`, and `relationship` (`supports`, `qualifies`, or `contradicts`). A locator names a page/table/section or pinned code lines. Use a restricted pointer instead of an excerpt when rights or privacy prohibit duplication. Explain that limitation.

Derived claims also record `formula`, `input_claim_ids`, `units`, and `calculation_check`. Inference records name their premises and the inference limit. Do not label an inference verified merely because its premises have citations.
