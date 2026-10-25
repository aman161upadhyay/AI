# Source and search record schemas

Store a sequence of source records in `sources.yaml`. All fields are required. Use `null` for unknown metadata and state the reason in `access_notes`. Never guess a publication date from a footer.

| Field | Type and meaning |
|---|---|
| `source_id` | Unique string, stable within the run. |
| `canonical_url`, `title`, `author_org` | Strings or null when access did not establish identity. |
| `published_at`, `updated_at`, `accessed_at` | ISO dates/timestamps or null for unknown publication metadata. Access time is required. |
| `version` | Document revision, model ID, commit, or null if not established. |
| `snapshot_path`, `content_hash` | Authorized local pointer and hash when available. Null if snapshots are prohibited. |
| `origin_family_id` | Shared ID for a common underlying observation, release, dataset, or study. |
| `source_type` | `paper`, `official-doc`, `record`, `code`, `reporting`, `testimony`, or `discovery`. |
| `claim_assessments` | Sequence of claim ID, tier 1/2/3, five credibility dimensions 0-4 or unknown, conflicts, and disposition. |
| `access_status` | `read`, `partial`, `blocked`, `metadata-only`, or `excluded`. |
| `access_notes`, `rights_notes` | Limits, permitted uses, and destination restrictions. |

Store search records in `search-log.yaml`: `search_id`, `question_id`, `query`, `database_or_tool`, `searched_at`, `filters`, `returned_count`, `selected_source_ids`, `exclusions`, `new_claim_ids`, `new_origin_ids`, `cost`, `error`, and `batch_id`.

Counts describe observed tool results, not an inferred universe of evidence. Use null for unavailable counts. Each exclusion names the record and a reason. Retain failed calls in resource accounting. Redact private queries in any public export.
