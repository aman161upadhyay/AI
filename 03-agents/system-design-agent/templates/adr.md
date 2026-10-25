# Architecture decision record contract

Create one record per consequential decision. Do not invent a decision date or approval.

| Field | Required content |
|---|---|
| ID, title, status | Stable identifier; proposed/accepted/superseded; actual owner and date |
| Context | Requirement IDs, observed implementation, constraints, assumptions |
| Options | At least the current/simple option and the proposed change; comparable criteria |
| Decision | Chosen option and why it satisfies the named requirements |
| Evidence | URLs/paths, versions, observation dates; distinguish benchmark claim from local test |
| Consequences | Operational cost, security boundaries, migration burden, limitations |
| Validation | Exact experiment/test, acceptance threshold, owner, execution status |
| Rollback | Reversible steps, incompatible data effects, approval owner |
| Reconsideration | Measurable load/cost/failure trigger or changed requirement |
| Related records | Requirement, data-model, API, deployment, threat-model references |

A decision is proposed until its named owner approves it. Keep superseded records with the replacement link.
