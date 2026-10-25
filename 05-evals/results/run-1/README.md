# Run 1 artifacts (2026-10-25)

One folder per executed case. Contents are evidence, kept verbatim: the lint does not apply the repository's prose rules here (it still scans for secrets).

- `candidate.json`: what the candidate session received (agent, task, inputs).
- `grader.json`: what the judge session received (gold, rubric, judge method, anti-patterns).
- `output.md`: the candidate's response, unedited.
- `candidate-meta.json`: the candidate's own account of skills loaded, files read, commands run and questions asked.
- `judgement.json`: the judge's per-criterion verdicts with quoted evidence, outcome, weighted score, notes and limits.
- `rerun/`: the same three result files for the same-day re-run of design-001 and research-agent-001.

Sandboxes (Node fixtures for the coding and security cases) are not committed; the judge re-ran their tests before grading and the results are quoted in `judgement.json`.

Observation for the next prompt revision: six of the ten outputs contain em dashes, which PRINCIPLES.md section 4 bans in our own prose. The agents' system prompts inherit the writing rules only by reference; the shared scaffold should state the rule directly.
