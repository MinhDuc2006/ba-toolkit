---
name: ba-gap
description: Gap and root-cause analysis for an engagement — current vs target state by dimension, 5 Whys, fishbone, SWOT, and prioritised recommendations with an impact/effort chart and roadmap. Use when the user wants to know why problems happen and what to do about them.
argument-hint: <engagement-folder> [section-name ...]
---

# /ba-gap — gap, root cause and recommendations

Arguments: `$ARGUMENTS`
- 1st argument: engagement folder (e.g. `projects/acme`). If missing, list folders under `projects/` and `samples/` and ask.
- Optional extra arguments: section names (e.g. `root-cause swot`) to produce or update only those sections.

## Modular files (next to this SKILL.md)
- `dimensions/` — the lenses for classifying gaps and causes (people, process, technology, data…). Used as the gap table groups AND the fishbone bones. Read all, sorted by filename.
- `sections/` — one file per section of the output document, built in filename order.
To extend, the user adds a new `NN-name.md` to either folder. Never hard-code the lists.

## Steps
1. **Read sources.** `context.md` (Goals and success, Pain points, Constraints, Data and metrics), every file in `inputs/`, and existing outputs:
   - `01-system-map.md` — 🟠 too loose and 🔴 needs more work items are gap candidates (cite `C-`/`H-` IDs).
   - `02-process-*.md` — bottlenecks and pain points flagged "root cause unknown → /ba-gap" are priority problems (cite `P-`/`CH-` IDs).
   If `context.md` is missing, suggest `/ba-intake` first.
2. **Agree the target state and the problems with the user.** In one message:
   - The target state you'll measure against, drawn from context.md goals and success metrics. Ask the user to confirm or adjust.
   - The 3–5 priority problems you propose to root-cause (largest impact first). Ask which to keep.
   - 3–6 questions from the dimensions' `Questions to ask`, where evidence is thinnest.
   Wait for answers.
3. **Analyse** following the sections in order. Gap IDs `G-01…`, root causes `RC-01…`, recommendations `R-01…`. Every finding cites a source or is `[Assumption]`.
4. **Check the logic before writing:**
   - Every priority problem has a root cause that is actionable (something the organisation controls), not a restatement of the symptom.
   - Every recommendation addresses at least one root cause or gap; every high-impact gap has a recommendation or is explicitly parked.
   - Recommendations respect context.md constraints (budget, timeline, regulation); flag any that would break one.
5. **Write** `outputs/03-gap.md` with the header/footer from CLAUDE.md. If it exists: with section arguments replace only those sections; otherwise ask to overwrite or save as `-v2`.
6. **Summarise in chat:** number of gaps by dimension, the top 3 root causes, quick wins (⚡), the big bets, and the suggested next skill (`/ba-requirements` to specify the solution, `/ba-docs` for a business case).

## Rules
- Separate **symptoms** (what people see), **gaps** (difference from target) and **root causes** (why the gap exists). Don't blame individuals — look for causes in systems, rules, incentives and information.
- Recommendations describe what to change in business terms; no vendor/product names unless a stated constraint.
- Respect `learning_mode` in context.md: when on, include each section's `Technique note` under **Technique notes**.
