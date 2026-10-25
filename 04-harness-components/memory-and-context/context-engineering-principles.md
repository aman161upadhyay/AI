# Context engineering principles

Use the canonical [context rules with evidence](../../00-foundations/context-engineering/principles.md) for general rules, sources, and limitations. This file defines the harness implementation contract.

Recommended context order: stable policy and tool schemas, bounded approved memory, relevant task contract, selected evidence, then current state and error. This is a local assembly policy. Validate it against actual task performance and cache usage.

Record the available context budget, the output reserve, and the remaining tool/time budget with each handoff. Bound retrieved spans and approved memory before assembly. Select compaction thresholds from measured failure traces; HumanLayer's 40-60% utilization range is a practitioner heuristic, not an automatic trigger.

Before handoff, save baseline/current candidate identities, approved paths, criterion IDs, changed files, decisions, failed approaches, evidence locations and pending approvals. Resume by reading current repository state. Never reconstruct missing authority from a summary's silence.
