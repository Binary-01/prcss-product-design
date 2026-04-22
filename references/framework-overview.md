# PRCSS* — Framework Overview

PRCSS* is a 7-phase product design workflow derived from the Double Diamond, extended with explicit **Deliver** and **Measure** phases so the framework covers end-to-end product design — not just ideation.

## The 7 phases

| # | Phase    | Emoji | One-line intent                                       |
|---|----------|-------|-------------------------------------------------------|
| 1 | Discover | 🔍    | Understand users, context, and the real problem.      |
| 2 | Define   | 🎯    | Frame the problem statement, goals, and scope.        |
| 3 | Ideate   | 🧠    | Generate divergent solution options.                  |
| 4 | Design   | 🧪    | Produce tangible artifacts (IA, wireframes, UI).      |
| 5 | Test     | 🪄    | Validate with users and stakeholders.                 |
| 6 | Deliver  | 📦    | Hand off, ship, document.                             |
| 7 | Measure  | 📏    | Track KPIs and design metrics post-launch.            |

## Canonical shape of the framework

A PRCSS* project is three things wired together:

1. **Project Info** — context block with Brief, Objectives, Stakeholders, Team, Metrics.
2. **Project Workflow** — a list of Design Actions, each tagged with one Phase and one Status. The same list can be viewed three ways:
   - **Design Phases** — grouped by phase, for kickoff planning.
   - **Project Roadmap** — laid out on a timeline using Start → Deadline.
   - **Design Actions Status** — grouped by status, for execution tracking.
3. **Design Actions library** — a catalog of reusable method/template cards. Users pick from the library and bring them into their active project.

## Workflow logic (the rules)

- Every unit of work is a **Design Action**, tagged with exactly one `Phase` and one `Status`.
- An action lives in one of two states: *library template* (reusable, not yet in the plan) or *active project task* (part of the current project). Keep the two separate; don't pollute the library with project-specific edits.
- Phases are **not strictly sequential** — the framework supports looping, e.g. Discover → Define → Ideate → Test → back to Define. The phase tag is about the *nature* of the work, not its position in a linear timeline.
- Status progression: `Blocked` / `To do` / `Scheduled` → `In progress` / `To review` → `Validated` / `Shipped`.
- The timeline view uses `Start` (begin date) and `Deadline` (end date) — these are the timeline anchors.

## Customization guidance

The source template explicitly invites customization:

> "The PRCSS* template comes with a pre-built Design workflow, feel free to customize it!"

Safe changes: rename phases, add sub-statuses, add properties (Priority, Effort, Impact). Risky changes: collapsing the library/active-project distinction, or dropping the `Phase` tag — both are load-bearing for grouping and planning.
