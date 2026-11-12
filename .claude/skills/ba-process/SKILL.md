---
name: ba-process
description: Map one business process in detail — scope (SIPOC), as-is swimlane, step table with timings, waste and bottlenecks, metrics, to-be swimlane, and the list of changes. Use when the user wants to analyse, map, or improve a workflow.
argument-hint: <engagement-folder> [process-name] [section-name ...]
---

# /ba-process — as-is / to-be process analysis

Arguments: `$ARGUMENTS`
- 1st argument: engagement folder (e.g. `projects/acme`). If missing, list folders under `projects/` and `samples/` and ask.
- 2nd argument (optional): which process (e.g. `order-to-delivery`). If missing, list the processes in context.md › Key processes and ask which one. One process per run.
- Further arguments (optional): section names to produce or update only those sections.

## Modular files (next to this SKILL.md)
- `sections/` — one file per section of the output document, built in filename order.
- `lenses/` — one file per improvement method (Lean waste, ECRS, value analysis…). Apply every lens, sorted by filename, when analysing the as-is and designing the to-be.
To extend, the user adds a new `NN-name.md` to either folder. Never hard-code the lists.

## Steps
1. **Read sources.** `context.md` (Processes, Stakeholders, Pain points, Data and metrics, Constraints), every file in `inputs/`, and `outputs/01-system-map.md` if present — reuse its component (`C-`) and handoff (`H-`) IDs, and treat its 🟠/🔴 handoffs in this process as priority areas.
2. **Walk through the process with the user.** Show a draft step list (trigger → steps → outcome, with who does each) and ask in one message:
   - Is the order right? Anything missing — especially exceptions, rework loops, approvals, waiting?
   - Times: how long each step takes (touch time) and how long work waits before it (wait time). Ranges are fine.
   - Volumes: how many times per day/week; how often each exception happens.
   - 1–3 questions from the lenses' `Questions to ask` where evidence is thin.
   Wait for answers before drafting. Missing numbers → `TBD` + open question; never invent timings.
3. **Analyse the as-is** using every lens. Tag steps with what each lens finds (e.g. waste type, value class).
4. **Design the to-be.** Only propose changes that address something found in step 3, and that respect context.md constraints. Describe changes in business terms; no vendor/product names. Show the user the main proposed changes and ask for a quick reaction before writing it up.
5. **Build the document** following `sections/`. Write it to `outputs/02-process-<process-slug>.md` using the header/footer from CLAUDE.md. If it exists: with section arguments replace only those sections; otherwise ask to overwrite or save as `-v2`.
6. **Summarise in chat:** step count as-is → to-be, cycle time and process efficiency as-is → to-be (or TBD), top 3 changes, and suggested next skill (`/ba-gap` for root causes, `/ba-requirements` to specify what the to-be needs).

## Rules
- Step IDs: `P-01…` for as-is, `T-01…` for to-be. Change IDs: `CH-01…`. Each to-be step notes which as-is step(s) it replaces, or "new".
- Map what really happens (including workarounds), not what the procedure manual says. Note differences.
- Respect `learning_mode` in context.md: when on, include each section's and each lens's `Technique note` under **Technique notes**.
