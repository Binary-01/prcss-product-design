# Design Actions library

Verbatim Design Actions from the PRCSS* template, one file per action. Each action preserves the original description and points to a canonical `### Ressource` block the user can fill in with their own links.

Claude should read the relevant file **before** generating content about that action, so the original voice and structure are preserved.

Actions marked as _Stub_ are placeholders in the original template ("Coming soon…") — short context is provided so the action is usable, but full descriptions will ship in a later version of PRCSS*.

---

## Index by phase

### 🔍 Discover
- [Brief](./brief.md) — canonical kickoff action (verbatim).
- [Objectives](./objectives.md) — canonical goal-setting action (verbatim).
- [Stakeholder Interview](./stakeholder-interview.md)
- [Stakeholder Map](./stakeholder-map.md)
- [Empathy Map](./empathy-map.md)
- [Customer Journey Map](./customer-journey-map.md)
- [Shadowing](./shadowing.md)
- [Data Analysis](./data-analysis.md)
- [How Might We ?](./how-might-we.md)
- [Benchmark](./benchmark.md)
- [UX Audit](./ux-audit.md)
- [Product Vision Board](./product-vision-board.md)
- [Design Metrics](./design-metrics.md)
- [Survey](./survey.md) _(stub)_

### 🎯 Define
- [Personas](./personas.md)
- [Service Blueprint](./service-blueprint.md)
- [Card Sorting](./card-sorting.md)
- [Priority Guide](./priority-guide.md)
- [Wireflow](./wireflow.md)
- [Hypothesis Canvas](./hypothesis-canvas.md)

### 🧠 Ideate
- [Crazy 8](./crazy-8.md)
- [Sketching](./sketching.md)
- [Co-wireframing Workshop](./co-wireframing-workshop.md)
- [Mind Map](./mind-map.md)
- [Six to One](./six-to-one.md)

### 🧪 Design
- [Wireframe](./wireframe.md)
- [Brand Design](./brand-design.md)
- [Simple Prototype](./simple-prototype.md) _(stub)_
- [Advanced Prototype](./advanced-prototype.md) _(stub)_

### 🪄 Test
- [User Interview](./user-interview.md)
- [Focus Group](./focus-group.md) _(stub)_
- [MVP](./mvp.md) _(stub)_

### 📦 Deliver
- [Design Specs](./design-specs.md) _(stub)_
- [Design System](./design-system.md)

### 📏 Measure
- [Usability Test](./usability-test.md) _(stub)_

---

## How to add a new action

1. Copy [`../../templates/action-card-template.md`](../../templates/action-card-template.md) into this folder as `kebab-case-name.md`.
2. Fill the `### Description` block in plain prose. Keep the voice short and helpful.
3. Add one or more bookmark/resource URLs under `### Ressource`.
4. Add the action to the index above under its phase.
5. If the action is intended for a specific project, tag it with a Phase and Status using the conventions in `../framework-overview.md`.
