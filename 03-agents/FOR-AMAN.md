# Aman, how to put these agents to work

## The shape of every run

Each agent expects the same five things from you. The agent's own `FOR-AMAN.md` fills in the specifics.

1. A framing sentence that names the agent, the register or mode, and the deliverable. Example for the writing agent: "Use the shared writing contract and the professional register. Draft a reply to the email below. Return plain text."
2. The inputs it may use: the brief, the facts you authorise, examples, the repository path, the design tokens. Agents in this repository are told to ask when a fact is missing, not to invent it.
3. The access you grant: usually read access to one folder or one thread. Refuse send, publish, deploy, delete, and payment permissions unless the run specifically needs them, and then grant them for that run only.
4. The gate: where you want to approve before the agent continues. Every `WORKFLOW.md` marks its gates; you can move them earlier, never later.
5. The eval: before trusting a new prompt or a changed skill, run the cases in `evals/` and record the outcome in `05-evals/results/`.

## Loading an agent into your tools

Pick the mode that matches the tool you are using that day.

| Where you work | What to do |
|---|---|
| Claude Code, Codex CLI, Cursor, Gemini CLI, or another coding agent | Copy the agent's `skills/` folder into the tool's skills directory and paste `SYSTEM-PROMPT.md` into its instructions file. The directories and file names per tool, checked against vendor documentation, are in the one table at [01-skills-library/FOR-AMAN.md](../01-skills-library/FOR-AMAN.md); they are not repeated here because they change. The checklists go into the tool as slash commands or saved prompts |
| Your own agent built on an SDK (Claude Agent SDK, OpenAI Agents SDK, Hermes, OpenClaw) | `SYSTEM-PROMPT.md` becomes the system message; `skills/` is mounted as a directory the agent can list and read (progressive disclosure, see `01-skills-library/spec/`); the tool permissions in `FOR-AMAN.md` become the allow and deny lists; `evals/` feeds the runner described in `04-harness-components/evals-framework/` |
| A chat interface with no file access | Paste `SYSTEM-PROMPT.md`, then paste the one or two skills the task needs. Keep the pasted total under about 8,000 tokens; the prompts were written to be self-contained for this case |
| A retrieval index over the whole repository | Use the allowlist in the root `FOR-AMAN.md`, unchanged: index `00-foundations/`, `02-prompts/`, `04-harness-components/`, `06-reference-library/`, and only the `README.md`, `FOR-AMAN.md`, `WORKFLOW.md` and `checklists/` files under `03-agents/`. Do not index `SYSTEM-PROMPT.md`, `evals/`, any `SKILL.md`, `01-skills-library/` or `03-agents/*/skills/`: prompts and skills are instructions, and an agent that retrieves instructions by similarity obeys the wrong ones; eval files contain the answers. Load skills explicitly instead |

## The loop that keeps them honest

Per task: brief, plan, approve, execute, review, decide, record. The review step is the adversarial council for anything that will be published, merged, or sent; for small internal drafts a single reviewer persona from `adversarial-council-agent/personas/` is enough. The record step is a line in the agent's `evals/INBOX.md` when the task revealed a new failure mode, promoted to a full YAML case (template in `04-harness-components/evals-framework/`) before the next prompt change.

Per week: read the technology scout's brief, rerun the eval sets that touched changed prompts, and prune. A skill that has not been loaded in a month is a candidate for removal; the quality bar in `PRINCIPLES.md` applies to what stays, not only to what enters.

## Access you should never grant by default

- Inbox-wide or drive-wide read access. Give the thread, the folder, the document.
- Credentials in prompts. Use the tool's secret store; the agents are told to refuse credentials pasted into chat.
- Autonomous sending, publishing, merging to `main`, deployment, deletion, or payment.
- Running vendored scripts without reading `SOURCE.md` first. The security review note there says what the script does and what was removed.

## What to do first

Start with the writing agent and its voice-training folder. Nothing else in this repository depends on your private data as directly, and you can judge the result yourself in an afternoon. The second afternoon goes to the research agent, because its evidence format is what every other agent consumes.
