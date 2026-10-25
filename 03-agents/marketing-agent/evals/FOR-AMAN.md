# Test the marketing contract without answer leakage

Copy this evaluation-run request:
"Run the selected marketing cases in isolated candidate sessions. Save each output before a separate grader receives the answer criteria."

Supply SYSTEM-PROMPT.md, the selected SKILL.md, the candidate model ID and a fixed tool budget.
Send only each case's task and inputs fields to the candidate.
Keep gold, rubric and anti_patterns with the grader until the candidate output is saved.
Give the grader the case ID, saved output and those withheld fields.
Retain source and as_of as evaluation provenance rather than candidate instructions.

Grant local fixture reads and a private directory for outputs and timing records.
Refuse live marketing connections, production writes and candidate access to the grader's files.
You compare clean with-skill and without-skill runs under the same settings.

Run marketing-001 through marketing-008 before approving a changed system prompt.
For a narrow skill revision, start with the IDs named in that skill's FOR-AMAN.md and then run the full regression set.
Review every rubric result against an output span; keep unexecuted cases labeled as unrun.
