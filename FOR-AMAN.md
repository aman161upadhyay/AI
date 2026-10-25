# Aman, start here

This file is the operating manual. It says what to do in the first hour, how to load the repository into whatever agent stack you use, how to run the loop that keeps quality up, and where the limits are. Each folder repeats the same pattern at its own level in its `FOR-AMAN.md`.

## The first hour

1. Read [PRINCIPLES.md](PRINCIPLES.md). Seven short sections. Every agent, reviewer, and you yourself check work against it.
2. Read [03-agents/README.md](03-agents/README.md) for the roster and the handoff diagram.
3. Open [03-agents/writing-agent/FOR-AMAN.md](03-agents/writing-agent/FOR-AMAN.md) and follow its voice-training steps with 30 to 50 of your own messages per register. This is the one agent that needs your data on day one, and the one whose output you can judge by eye.
4. Run `03-agents/writing-agent/evals/writing-001.yaml` unchanged, following `03-agents/writing-agent/evals/README.md`. It is a synthetic smoke test: it tells you whether the prompt and the register load and behave, not whether the voice is yours. Record the run with `05-evals/results/TEMPLATE-run-report.md`.
5. Write a second case from a real brief of your own (copy `04-harness-components/evals-framework/TEMPLATE-eval-case.yaml`), keep the facts you expect outside the drafting session, and compare the agent's draft with one you wrote blind.

After that afternoon you have a baseline for the writing agent and a record of it. Reliable imitation of your voice takes the calibration loop in the agent's `voice-training/` folder over the following weeks.

## Loading the repository into your stack

The repository is text. Three loading modes cover the tools in use today.

**Coding agents (Claude Code, Codex CLI, Cursor, Gemini CLI).** Copy the skills you want from `01-skills-library/` and `03-agents/*/skills/` into the tool's skills directory, and paste the relevant `SYSTEM-PROMPT.md` into the tool's instructions file. The exact directories and file names differ per tool and change between releases; the one authoritative table, checked against each vendor's documentation with the date of the check, is in [01-skills-library/FOR-AMAN.md](01-skills-library/FOR-AMAN.md). Every other file in this repository points there instead of repeating it. The coding agent's `templates/` and `guardrails/` folders hold the hook and permission examples.

**Your own agents (Claude Agent SDK, OpenAI Agents SDK, Hermes, OpenClaw, or a framework you write).** `SYSTEM-PROMPT.md` is the system message. Mount the agent's `skills/` directory so the agent lists skill names and descriptions at start and reads a `SKILL.md` only when it needs it; that is the progressive-disclosure pattern in `00-foundations/context-engineering/`. The permissions in each `FOR-AMAN.md` become the allow and deny lists enforced outside the model (`04-harness-components/security-guardrails/`). The YAML in `evals/` feeds the runner contract in `04-harness-components/evals-framework/`. The reference architecture for the whole stack is in `00-foundations/agent-architectures/reference-architecture-for-amans-agents.md`.

**A retrieval index (an "AI brain" over your notes).** Index `00-foundations/`, `02-prompts/`, `04-harness-components/`, `06-reference-library/`, and the `README.md`, `FOR-AMAN.md`, `WORKFLOW.md` and `checklists/` files under `03-agents/`. Exclude `SYSTEM-PROMPT.md` and `evals/` under `03-agents/`, every `SKILL.md`, and everything under `01-skills-library/` and `03-agents/*/skills/`: prompts and skills are instructions, and an agent that retrieves instructions by similarity follows the wrong ones; eval files contain the answers. Load skills explicitly by name. Check the exclusion after building the index: `grep -c -E "SKILL.md|SYSTEM-PROMPT.md|/evals/" <your manifest>` should print 0.

In all three modes, keep the vendored skills read-only and update them by re-vendoring from the pinned upstream, so your changes live in your own skills and survive upgrades.

## The collaboration loop

Per task, seven steps: brief, plan, approve, execute, review, decide, record.

- Brief: the framing sentence from the agent's `FOR-AMAN.md`, the facts you authorise, the inputs, the gate you want.
- Plan: the agent returns a plan before touching anything that costs money or leaves the sandbox. Every `WORKFLOW.md` marks this.
- Approve: you approve the plan, or change the gate. Gates move earlier, never later.
- Execute: the agent works inside the permissions you granted for this run.
- Review: for anything published, merged, sent, or deployed, run the adversarial council (`03-agents/adversarial-council-agent/`) with at least three personas. For small internal drafts, one persona.
- Decide: you decide on the findings. The council finds; it does not approve.
- Record: if the task revealed a failure mode, note it in one line in the agent's `evals/INBOX.md`, then promote it to a full case from `04-harness-components/evals-framework/TEMPLATE-eval-case.yaml` before the next prompt change. Only a complete case, with frozen inputs and pass conditions, counts as "the next run tests for it".

Per week, three things: read the technology scout's brief (`03-agents/technology-scout-agent/`), rerun the eval sets touched by any prompt change, and prune anything that has not earned its place.

## What to give each agent

| Agent | You supply | Grant | Refuse by default |
|---|---|---|---|
| writing | Your own messages per register, the facts for this piece, the recipient's relationship to you | Read access to the redacted brief and examples | Sending, publishing, inbox search, corpus upload without approval |
| research | The question, the decision it serves, the deadline, sources you already trust or distrust | Web search and fetch; read access to the documents you name; write access to one named research directory for notes, the source registry and the claim map | Paid API spend without a cap; writing anywhere outside that directory |
| coding | The repository, the acceptance check, the branch | Read and write in a branch; test execution in a sandbox | Merge to `main`, deploy, secrets, destructive git, network beyond package registries |
| design | The brief, the audience, existing tokens or brand, screenshots of the current state | Read access to the design files; a preview environment | Shipping to production; purchasing fonts or assets |
| security | The scope, the authorisation, an isolated replica | Read access to code and configuration; execution only in the replica | Any action against production; disclosure outside the agreed channel |
| adversarial council | The artifact, the acceptance criteria, which personas | Read access to the artifact and its sources | Editing the artifact; access to the other reviewers' findings before they finish |
| system design | The product brief, constraints, the existing system if any | Read access to architecture docs and code | Deployment and any mutation of running systems |
| marketing | The product facts, the audience, proof points you can defend, the channel | Read access to analytics exports you choose | Publishing, ad spend, sending email |
| technology scout | Your watchlist weights, the stack you run | Web search and fetch; the subscription feeds you name | Installing or upgrading anything |

The detailed version of each row, including the approval gates, is the agent's own `FOR-AMAN.md`.

## Extending without degrading

New sources go through the four tests in `PRINCIPLES.md` section 1, and the reason is recorded next to the item. Vendored folders get `SOURCE.md` and the upstream licence. Before any push, run `python3 07-council/tools/lint.py .` and a council round (`07-council/PROTOCOL.md`); commit the round log with the change. When you want to add a whole new area, write its `README.md` and `FOR-AMAN.md` first, then fill it; a folder that cannot explain itself in two files is not ready.

## Limits you should know

- No agent here has been run on your repositories, inbox, or products. The prompts are first versions built from the best public sources; expect to revise them after the first week of evals.
- Ten of the 72 eval cases have been executed once, against a model, with a separate model as judge (7 PASS, 2 FAIL, 1 UNKNOWN; one failure fixed and re-run to PASS, one still open). Every case asked for a human judge, so each of those results awaits your adjudication; the other 62 cases are written but unrun. `05-evals/results/` says exactly what has and has not run.
- Numbers that move (stars, prices, model names, cache semantics, API deadlines) carry an as-of date. Check them before relying on them; the technology scout's weekly brief is the mechanism for that.
- The skills library is curated from upstreams at pinned commits. Upstream fixes after 2026-10-25 are not here until you re-vendor.

## Where the sources and the working notes went

The research notes, source captures, and the cloned repositories that this library was built from were kept outside the repository. Every file inside cites what it took and from where, so the repository stands on its own; the `sources.md` in each folder is the index.
