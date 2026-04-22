---
name: prcss-product-design
description: Kickstart and run a product design project using the PRCSS* framework — a 7-phase Double-Diamond-inspired workflow (Discover, Define, Ideate, Design, Test, Deliver, Measure) with a pre-built project template and a reusable Design Actions library. Trigger with "PRCSS", "product design project", "design workflow", "design phases", "project brief", "design actions", "Double Diamond", "design framework", "discover define ideate", "scaffold a design project", "set up a product design project", or whenever the user wants a structured, opinionated way to plan and run a product design engagement end-to-end.
---

# PRCSS* — Product Design Project Framework

> A 7-phase product design workflow by Wojciech Pawlak (PRCSS\*, Paris), packaged as a reusable project template. Contact: prcss.design@gmail.com.

This skill lets Claude help users scaffold, run, and document a product design project from brief to measurement using the PRCSS* logic. It is **tracker-agnostic** — outputs are plain Markdown the user can paste into any tool (wiki, docs, kanban, issue tracker) or keep as a folder of docs.

---

## When to use this skill

Invoke this skill whenever the user asks about:

- Starting or scaffolding a **product design project** (brief, objectives, stakeholders, team, metrics).
- Planning a **design workflow** using explicit phases (Discover → Define → Ideate → Design → Test → Deliver → Measure).
- Picking or writing a **Design Action** (e.g. Brief, Objectives, research interview, ideation workshop, usability test).
- Producing deliverables that respect the PRCSS* structure: Project Info, Project Workflow, Design Actions library.

If the user already has a design framework in mind (e.g. pure Double Diamond, IBM Loop, Google Design Sprint), offer to adapt PRCSS* to it instead of forcing this template.

---

## Core mental model

PRCSS* = **Project Info** + **Project Workflow** + **Design Actions library**.

1. **Project Info** — the "who / why / what / when" of the project: Brief, Objectives, Stakeholders, Team, Metrics.
2. **Project Workflow** — an ordered/loopable list of Design Actions, each tagged with one Phase and one Status. Think of it as a kanban or roadmap grouped by phase.
3. **Design Actions library** — a reusable catalog of methods/templates tagged by phase. Users pick from the library and copy into their active project.

The 7 phases:

| Phase     | Emoji | Intent                                                   |
|-----------|-------|----------------------------------------------------------|
| Discover  | 🔍    | Understand the problem, users, and context.              |
| Define    | 🎯    | Frame the problem, set objectives, sharpen scope.        |
| Ideate    | 🧠    | Generate divergent solution options.                     |
| Design    | 🧪    | Produce tangible design artifacts (wireframes, UI, IA).  |
| Test      | 🪄    | Validate designs with users and stakeholders.            |
| Deliver   | 📦    | Hand off, ship, and document the final design.           |
| Measure   | 📏    | Track KPIs and design metrics post-launch.               |

See `references/framework-overview.md` for detailed intent, outputs, and typical methods per phase.

---

## Kickoff — clarify before building (required)

**Before doing any real work, Claude MUST use the `AskUserQuestion` tool to frame the user's objective.** PRCSS\* covers a wide surface (scaffold, phase plan, single action, full roadmap) — picking the wrong mode wastes the user's time. Ask in one `AskUserQuestion` call with the 4 questions below, then read only the source-of-truth files relevant to the selected mode.

Send these four questions together (keep the labels and options short so the UI renders as chips):

1. **Mode** — *"What do you want to produce first?"*
   - `Full project scaffold` — The complete project page (Info + Workflow + Actions library). *Recommended for new projects.*
   - `Brief + Objectives only` — Just the two canonical Discover actions. Useful to kick off a conversation with stakeholders.
   - `Single phase plan` — Propose 3–6 Design Actions for one chosen phase.
   - `Single action card` — One Design Action written in full (uses `templates/action-card-template.md`).

2. **Phase** — *"Which phase are you starting from?"* (only if Mode ≠ `Full project scaffold`)
   - `Discover` 🔍
   - `Define` 🎯
   - `Ideate` 🧠
   - `Design / Test / Deliver / Measure` — pick one when relevant.

3. **Scope** — *"How big is this project?"*
   - `Small` — 1–2 weeks, solo or pair. Keep the plan lean (3–5 actions total).
   - `Medium` — 1–2 months, small team. Expect ~2–3 actions per phase.
   - `Large` — a quarter+, cross-functional. Full depth on every phase, including Measure.

4. **Output** — *"How should Claude deliver the result?"*
   - `One Markdown file` — Everything in a single doc saved to the workspace.
   - `Folder of Markdown files` — Split into project page + one file per action for easy reuse.
   - `Paste-ready snippet` — A single formatted block the user can paste into an existing tool.

Once answers come back:

- If `Mode = Full project scaffold` → also collect, in follow-up conversation (not via the tool): project name, one-paragraph context, 1–3 objectives, stakeholders, team, 1–3 KPIs with baseline/target, Start & Deadline dates. Then proceed to step **1** below.
- If `Mode = Brief + Objectives only` → load `references/actions/brief.md` + `references/actions/objectives.md` and adapt them. No need for workflow content.
- If `Mode = Single phase plan` → proceed to step **3** below with the selected phase.
- If `Mode = Single action card` → proceed to step **2** below.

Skip the kickoff only if the user's request is already specific enough to answer all four questions unambiguously (e.g. *"write a Usability Test action card for checkout v2"*).

---

## How Claude should operate

Follow this decision tree:

**1. If the user wants to scaffold a new project →**
   - Read `references/project-template.md` to reproduce the Project Info block and the Project Workflow block.
   - Ask the user for: project name, context/brief, objectives (bullet list), stakeholders, team, KPIs, start date, target deadline.
   - Output: a Markdown project document based on `templates/project-skeleton.md`, saved in the workspace folder.

**2. If the user wants to pick or write a Design Action →**
   - Identify the phase (ask if ambiguous).
   - Read the matching file in `references/phases/<phase>.md` for intent and method suggestions.
   - Read `templates/action-card-template.md` for the card shape.
   - The full PRCSS\* **Design Actions library** lives in `references/actions/` (see `references/actions/README.md` for the index by phase). Always load the matching file verbatim so the description logic is preserved — do not paraphrase from memory.
   - Canonical actions with full verbatim content: `brief.md`, `objectives.md`. All other actions are in the same folder, one file per method (e.g. `personas.md`, `crazy-8.md`, `wireframe.md`, `user-interview.md`, …).
   - If the user asks for an action that isn't in the library yet, copy `templates/action-card-template.md`, name the new file in kebab-case, and add it to the Design Actions index.

**3. If the user wants a full project plan →**
   - Walk phase by phase, propose 2–4 Design Actions per phase, let the user pick, then output a consolidated Markdown plan.

**4. If the user asks for accessibility, UX copy, research synthesis, or design critique help inside a PRCSS\* project →**
   - Stay in PRCSS* context (preserve phase/action tagging), but defer to the appropriate `design:*` skill for the craft work.

---

## Source-of-truth files

Always read the referenced file **before** generating content about the topic — don't paraphrase from memory, the logic of the template lives in those files.

- `references/framework-overview.md` — the 7 phases, intents, outputs, loop logic.
- `references/project-template.md` — literal structure of the main Project page (Project Info, Project Workflow, Design Actions sections).
- `references/phases/` — one file per phase with purpose, typical actions, and outputs.
- `references/actions/` — the full Design Actions library, one file per action. Index and usage rules are in `references/actions/README.md`. Canonical Brief and Objectives actions (`brief.md`, `objectives.md`) are preserved verbatim from the original source.
- `templates/project-skeleton.md` — fill-in-the-blanks Markdown scaffold for a new project.
- `templates/action-card-template.md` — shape of a Design Action card (Description + Ressource blocks, plus metadata).

---

## Output conventions

- Use **phase emojis** consistent with the source: 🔍 Discover, 🎯 Define, 🧠 Ideate, 🧪 Design, 🪄 Test, 📦 Deliver, 📏 Measure.
- Keep the original voice on callouts: short, helpful, second-person ("In this section you can fill…").
- Each Design Action has two headings: `### Description` and `### Ressource` (yes, the source spells it with one `s`; we preserve it for fidelity — feel free to normalize to `### Resources` when producing English-only outputs, but flag the choice).
- Allowed Status values: `Blocked`, `To do`, `Scheduled`, `In progress`, `To review`, `Validated`, `Shipped`.
- Allowed Phase values: `Discover`, `Define`, `Ideate`, `Design`, `Test`, `Deliver`, `Measure`.
- Dates: use ISO (`YYYY-MM-DD`) internally and format on output.

---

## Attribution

Framework and skill by **Wojciech Pawlak (PRCSS\*)** — Paris. Licensed MIT. Contact for feedback: prcss.design@gmail.com.
