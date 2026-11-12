---
name: ba-requirements
description: Turn an engagement's context.md and inputs (notes, transcripts, docs) into a requirements document — business, functional and non-functional requirements, user stories, acceptance criteria, MoSCoW priorities and a traceability matrix. Use when the user needs requirements or user stories.
argument-hint: <engagement-folder> [section-name ...]
---

# /ba-requirements — requirements document

Arguments: `$ARGUMENTS`
- 1st argument: engagement folder (e.g. `projects/acme`). If missing, list folders under `projects/` and `samples/` and ask.
- Optional extra arguments: section names (e.g. `user-stories acceptance-criteria`) to produce or update only those sections.

## Sections are modular
Each file in `sections/` (next to this SKILL.md) defines one section of the document: its `Purpose`, `Inputs`, `How to write`, `Format`, `Quality checks`, and `Technique note`. Read all of them, sorted by filename, and build the document in that order. To add a section, the user adds a new `NN-name.md` file in the same format — never hard-code the section list.

Later sections may depend on earlier ones (e.g. acceptance criteria need user stories). If the user asks for a section whose dependency is missing from the existing document, produce the dependency too and say so.

## Steps
1. **Read sources.** `context.md` (goals, stakeholders, processes, pain points, constraints, scope), every file in `inputs/`, and any existing `outputs/` deliverables (the system map's focus areas, process maps and gap analyses are good sources of requirements — cite their IDs, e.g. `C-03`, `H-02`, `CH-04`; every process change `CH-` and every recommendation `R-` in Now/Next should become at least one requirement). If `context.md` is missing, suggest `/ba-intake` first; continue only if the user agrees, flagging the gaps.
2. **Confirm scope with the user** in one message:
   - The in-scope area and main user roles you found.
   - Which sections you'll produce (default: all).
   - 3–6 clarifying questions where the sources are thin or contradictory (e.g. volumes for performance NFRs, who approves what).
   Wait for answers before drafting.
3. **Draft section by section** following each section file. Give every item a stable ID (`BR-01`, `SR-01`, `FR-01`, `NFR-01`, `US-01`) and a source (`context.md › Pain points`, `inputs/<file>`, `user`, or `[Assumption]`).
4. **Run the quality checks** listed in each section file. Fix what you can; list the rest under Open questions.
5. **Write the file** `outputs/04-requirements.md` using the header and footer from CLAUDE.md (title, engagement, date, sources, open questions, next steps). If it already exists:
   - With section arguments: replace only those sections; keep IDs of unchanged items stable.
   - Without: ask whether to overwrite or save as `04-requirements-v2.md`.
6. **Summarise in chat:** counts per section (e.g. 6 BR, 18 FR, 7 NFR, 12 US), the Must-haves, top open questions, and the suggested next skill.

## Rules
- Requirements say **what**, not **how**: no vendor or technology choices unless they're a stated constraint.
- One requirement per line; testable; no "and/or" bundling.
- Never drop a pain point or goal silently — every goal in context.md must trace to at least one requirement, or be listed as an open question.
- Respect `learning_mode` in context.md: when on, include each section's `Technique note` at the end of the document under **Technique notes**.
