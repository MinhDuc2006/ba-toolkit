---
name: ba-system-map
description: Map an engagement's current system (people, tools, data, handoffs) and rate each part as solid, too loose, can be improved, or needs more work. Produces a colour-coded Mermaid map and a focus list. Use after /ba-intake and before process, gap or requirements work.
argument-hint: <engagement-folder> [section-name ...]
---

# /ba-system-map — map and assess the current system

Arguments: `$ARGUMENTS`
- 1st argument: engagement folder (e.g. `projects/acme`). If missing, list folders under `projects/` and `samples/` and ask.
- Optional extra arguments: section names (e.g. `health-assessment focus-areas`) to produce or update only those sections.

"System" means the whole socio-technical system in scope: software, spreadsheets, paper, people/teams, and the handoffs and data flows between them — not just IT.

## Modular files (next to this SKILL.md)
- `rating-scale.md` — the four ratings and what each means. Always use it; never invent other ratings.
- `criteria/` — one file per assessment criterion (ownership, integration, data quality…). Assess every part against every criterion file, sorted by filename. To add a criterion, the user adds a new `NN-name.md`.
- `sections/` — one file per section of the output document, built in filename order. To add a section, the user adds a new `NN-name.md`.
Never hard-code the criteria or section lists.

## Steps
1. **Read sources.** `context.md` (especially Current systems, Processes, Stakeholders, Pain points, Data and metrics), every file in `inputs/`, and existing `outputs/`. If `context.md` is missing, suggest `/ba-intake` first.
2. **Draft the parts list** — every component (system, tool, spreadsheet, team/role, external party, data store) and every handoff between them. Show it to the user as a short list and ask:
   - Is anything missing or wrong (especially workarounds, side spreadsheets, email/phone steps)?
   - 3–6 targeted questions drawn from the criteria files' `Questions to ask`, focused on the parts where evidence is thinnest.
   Wait for answers before rating.
3. **Assess each part** against every criterion. For each part, decide one overall rating from `rating-scale.md` (worst relevant criterion usually wins, but use judgement and explain). Every rating needs evidence — a source (`context.md › …`, `inputs/<file>`, `user`) or it's `[Assumption]`. If there's no evidence at all, rate it 🔴 Needs more work with reason "unknown — investigate".
4. **Build the document** section by section following `sections/`. Write it to `outputs/01-system-map.md` using the header/footer from CLAUDE.md. If it exists: with section arguments replace only those sections; otherwise ask to overwrite or save as `-v2`.
5. **Summarise in chat:** count of parts per rating, the top 3 "too loose" and top 3 "needs more work" items, quick wins, and the suggested next skill (`/ba-process` for messy handoffs, `/ba-gap` for root causes, `/ba-requirements` once the target picture is clear).

## Rules
- Map what **is**, not what should be. Note documented-vs-actual differences when users describe workarounds.
- Don't propose specific products or vendors; describe the improvement in business terms.
- Use component IDs `C-01…` and handoff IDs `H-01…` so later skills (gap, requirements) can trace to them.
- Respect `learning_mode` in context.md: when on, include each section's `Technique note` under **Technique notes**.
