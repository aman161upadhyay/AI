Adapted from pbakaus/impeccable at 3671d50f0ac9a662ce0615e85a256110c9cd720b; the upstream launcher that downloads and executes a release binary was removed under this repository's PRINCIPLES.md section 5. This is reference prose for a design reviewer, not an installable skill. Modified from the original; see SOURCE.md.

# Impeccable reference

Modification notice, 2026-10-25: adapted from plugin/skills/impeccable/SKILL.md. Licence: Apache-2.0; see LICENSE and NOTICE.md.

This package has no agent discovery metadata, launcher, detector, hooks or other runtime. Read the selected playbooks as design reference, not as tool instructions. Commands and executable examples retained inside the playbooks describe the upstream workflow only. Do not run them, fetch omitted files or install dependencies to complete a reference-only review. Use only separately authorised host tools and report unavailable evidence.

The client's brief wins over upstream taste rules. In particular, craft-floor.md's absolute eyebrow-label ban does not override an explicit request or a functional label. Heuristic scores are reviewer judgements, not measured usability results.

This skill gives you the tools and permission to make design that earns the name out-of-distribution craft. Work as an award-winning design director would: production-grade code, a clear POV, a deep grasp of what the client and its users need, and exceptional craft.

Core principles:
- Finish the job. No hedging, no shortcuts: the deliverable is complete, except assets the user must provide.
- Scale ambition to the surface's mode (see Modes). Persuade and Experience get full commitment: bold, distinct work with a point of view. On Operate and Read, ambition shows as precision and restraint, and patterns the visitor already knows earn their place.
- Verify by looking at the rendered result at the sizes it ships at, and batch the checks: fix what one look shows before looking again, rather than screenshotting after every tweak.

## How to design

- **The brief wins.** Honor pinned aesthetics, eras, materials, fonts, and palettes even when they conflict with a saturated-pattern warning. Redirecting a clear brief toward your taste is failure.
- **Refinement preserves; redesign replaces.** Refinement keeps the incumbent identity, behavior, copy, and everything outside scope. Ask before replacing factual copy or adding claims. Redesign keeps product truth, content, function, native affordances, and constraints, but treats the old look as evidence and anti-reference; choose a replacement world and replace DESIGN.md only with the user's approval. Never split the difference into polish on the discarded look.
- **Loaded symbols stay out of the decoration.** A subject's world does not license emblems tied to militarism, supremacy, or hate movements as motifs, badges, or ornament, such as the Rising Sun flag's rays, the Confederate battle flag, or Nazi-era insignia and their stylised variants; reach for that world's neutral forms instead. Content that documents such a symbol as fact stays as it is.
- **Visual authority is evidence, not a filename.** Missing DESIGN.md alone does not make a project greenfield; determine whether to preserve, expand, or replace the incumbent world.

## Modes

The mode names what the visitor's success looks like on this surface.

- **Persuade:** the visitor decides and acts; design is the product. Landing pages, marketing, campaigns, pricing. Earn attention and action. Ship real imagery when the brief needs it; follow the committed world, not category habit.
- **Operate:** the visitor completes a task. App UI, dashboards, editors, admin, settings, tools. Scanability, consistency, native expectations, and the real usage scene outrank expression. Brand lives in precise details.
- **Read:** the visitor understands something. Docs, articles, guides, help, changelogs. Structure for comprehension, then make the reading experience worth staying in.
- **Experience:** the visitor is inside the work itself. Portfolios, galleries, showcases. Let the artifact lead from the first viewport; the interface recedes.

Choose the mode from the requested surface, not the product, and persist it only in that surface brief. A tool's landing page is still Persuade; a fashion house's documentation is still Read; a docs index is Read, not Persuade. See [operate.md](reference/operate.md) for deeper Operate/Read guidance.

## Selected playbooks

This table adapts the upstream command table into reading references. It does not register commands.

| Reference | Purpose |
|---|---|
| [critique.md](reference/critique.md) | Design review with heuristic scoring and evidence limits. |
| [clarify.md](reference/clarify.md) | Improve UX copy, labels and error messages. |
| [polish.md](reference/polish.md) | Final quality pass without concealed redesign. |
| [craft-floor.md](reference/craft-floor.md) | Quality checks and opinionated defaults, subordinate to the brief. |
| [mode-persuade.md](reference/mode-persuade.md) | Marketing direction and composition. |
| [mode-operate.md](reference/mode-operate.md) | Task-first product direction and composition. |
| [mode-read.md](reference/mode-read.md) | Reading direction and composition. |
| [operate.md](reference/operate.md) | Product typography, state and interaction detail. |

The upstream Setup, command routing, context-loader calls, pin/unpin, hooks, doctor and drift-repair instructions are intentionally absent. Do not infer permission to install the upstream skill from this reference.
