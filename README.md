# PRCSS* — Product Design Skill for Claude

A Claude skill that lets product & UX designers kickstart and run end-to-end design projects using the **PRCSS\*** framework — a 7-phase, Double-Diamond-inspired workflow by Wojciech Pawlak (PRCSS*, Paris).

Ask Claude for a project scaffold, a phase plan, or a single Design Method card, and you get back a clean Markdown deliverable that follows the PRCSS* conventions (phases, statuses, method card shape) — ready to paste into any tool (wiki, kanban, docs, Figma), with no tool lock-in.

---

## What it gives you

- A tracker-agnostic **project scaffold**: Project Info (Brief, Objectives, Stakeholders, Team, Metrics) + Project Workflow grouped by phase + reusable Design Methods library.
- **Phase-level plans** with 3–6 recommended Design Methods each, drawn from the original PRCSS* method set.
- **Canonical Design Methods preserved verbatim** from the source template: ✅ Brief and ✅ Objectives (steps, wording, structure).
- An **interactive kickoff**: Claude asks 4 multiple-choice questions (Mode, Phase, Scope, Output) before producing anything, so you don't get a 2,000-word scaffold when you wanted a single method card.
- Hooks into the rest of the `design:*` skill family (research synthesis, accessibility review, UX copy, design critique, developer handoff) while keeping PRCSS* phase/method tagging.

The 7 phases:

| | Phase | Intent |
|---|---|---|
| 🔍 | Discover | Understand users, context, and the real problem. |
| 🎯 | Define | Frame the problem, goals, scope. |
| 🧠 | Ideate | Generate divergent solution options. |
| 🧪 | Design | Produce tangible artifacts (IA, wireframes, UI). |
| 🪄 | Test | Validate with users and stakeholders. |
| 📦 | Deliver | Hand off, ship, document. |
| 📏 | Measure | Track KPIs and design metrics post-launch. |

---

## Install

Pick the option that matches how you run Claude.

### Option A — Cowork desktop app (recommended)

Open `prcss-product-design.skill` in Finder. Claude for desktop surfaces an **"Install skill"** button. Confirm and the skill is available immediately in any new conversation.

### Option B — Claude Code or local skills folder

```bash
# Unzip the skill next to your other skills
unzip prcss-product-design.skill -d ~/.claude/skills/prcss-product-design
```

Restart your session.

### Option C — Cowork plugin (marketplace-ready)

`prcss-product-design.plugin` bundles the skill with a plugin manifest. Open it in Cowork and click **"Install plugin"**. Useful if you plan to ship this to a team alongside other skills/commands.

### Option D — From source (GitHub)

```bash
git clone <this-repo>
cd prcss-product-design
# Either zip it into a .skill yourself…
zip -r ../prcss-product-design.skill . -x "*.DS_Store" -x "README.md" -x "LICENSE" -x "NOTICE"
# …or drop the folder directly into ~/.claude/skills/
cp -R . ~/.claude/skills/prcss-product-design
```

---

## How to use it

Once installed, any message that mentions PRCSS or a product design workflow triggers the skill. Claude opens with a single multiple-choice kickoff:

> **Mode** — Full project scaffold / Brief + Objectives / Single phase plan / Single method card
> **Phase** — Discover / Define / Ideate / Design|Test|Deliver|Measure
> **Scope** — Small (1–2 weeks) / Medium (1–2 months) / Large (quarter+)
> **Output** — One Markdown file / Folder of Markdown files / Paste-ready snippet

Your answers decide which files Claude loads and what it produces.

### Example prompts

**1. Full project scaffold**
> *Use PRCSS to scaffold a project to redesign the mobile checkout for a B2C marketplace. Deadline end of Q3.*

Claude asks the 4 kickoff questions, then asks for context/brief, objectives, stakeholders, team, and KPIs. Outputs a Markdown project page with Project Info, a Project Workflow grouped by phase, and a seeded Design Methods library.

**2. Phase-level plan**
> *Give me a Discover plan for a B2B SaaS onboarding redesign.*

Claude reads `references/phases/discover.md`, proposes 3–6 Design Methods (stakeholder interviews, desk research, heuristic audit…), and returns them as method cards ready to drop into your plan.

**3. Single method card**
> *Write me the Brief method for Project Atlas following PRCSS.*

Claude reads `references/methods/brief.md` (verbatim content from the original Notion template) and fills in the 6 steps with your project's specifics.

**4. Non-trigger check**
> *Explain OAuth.*

The skill should NOT load. If it does, sharpen the `description:` frontmatter.

---

## What's in the box

```
prcss-product-design/
├── SKILL.md                          # Skill entry point + kickoff logic
├── README.md                         # You are here
├── LICENSE                           # MIT — covers this skill packaging
├── references/
│   ├── framework-overview.md         # 7 phases + rules + loop logic
│   ├── project-template.md           # The canonical Project page structure
│   ├── phases/
│   │   ├── discover.md · define.md · ideate.md
│   │   ├── design.md · test.md · deliver.md
│   │   └── measure.md
│   └── methods/                      # Design Methods library (35 cards)
│       ├── README.md                 # Index by phase
│       ├── brief.md · objectives.md  # Canonical (verbatim from source)
│       └── …                         # 33 more methods across the 7 phases
└── templates/
    ├── project-skeleton.md           # Fill-in-the-blanks Markdown scaffold
    └── method-card-template.md       # Shape of a Design Method card
```

---

## Design principles behind the skill

- **Tracker-agnostic.** Outputs are plain Markdown — no Notion or Jira dependency. Paste where you like.
- **Progressive disclosure.** `SKILL.md` stays under 3k words; detailed knowledge lives in `references/`. Claude only loads what the current mode needs.
- **Preserve the original voice.** Callouts, section titles, and the two canonical methods (Brief, Objectives) are reproduced verbatim from the original PRCSS* template.
- **Loopable, not waterfall.** Phases are tags, not steps. The framework assumes Discover ↔ Define ↔ Ideate ↔ Test cycles.

---

## Credits

Framework and skill by **Wojciech Pawlak (PRCSS\*)** — Paris. Version 0.5.0. Licensed MIT (see `LICENSE`).

> **v0.5.0 highlights**
> - **Design Actions → Design Methods** rename (aligns with IDEO / NN/g vocabulary; the Notion source still uses "Actions").
> - Tool-agnostic kickoff: works in Cowork (chips via `AskUserQuestion`) **and** claude.ai web / Claude Code (numbered Markdown list).
> - Method card template adds a project-instance metadata block, numbered steps, and a feedback footer.

## Feedback

- About the **framework** (phases, methods, conventions): [prcss.design@gmail.com](mailto:prcss.design@gmail.com).
- About the **skill** (install, triggers, output format): open an issue on this repository.
