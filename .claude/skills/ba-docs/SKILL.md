---
name: ba-docs
description: Produce stakeholder documents from an engagement's analysis, in two packs — an executive pack for presenting to senior management (summary, business case, roadmap and decisions, slide outline) and an analyst pack for BAs (BRD, stakeholder map, RACI, assumptions/decisions register, glossary and ID index). Use when the user needs to present, hand over, or document the work.
argument-hint: <engagement-folder> [exec|analyst|both] [document-name ...]
---

# /ba-docs — executive pack and analyst pack

Arguments: `$ARGUMENTS`
- 1st argument: engagement folder (e.g. `projects/acme`). If missing, list folders under `projects/` and `samples/` and ask.
- 2nd argument (optional): `exec`, `analyst`, or `both` (default: ask).
- Further arguments (optional): document names (e.g. `business-case raci`) to produce only those.

## Modular files (next to this SKILL.md)
- `audiences/<pack>.md` — the style rules for that audience (tone, length, jargon, what to leave out). Apply them to every document in the pack.
- `documents/<pack>/` — one file per document, built in filename order.
To add a document, the user adds `NN-name.md` to a pack folder. To add a whole audience (e.g. `vendor`, `dev-team`), add `audiences/<name>.md` and `documents/<name>/`. Never hard-code the packs or document lists — the valid 2nd-argument values are the files in `audiences/`.

## Steps
1. **Read everything.** `context.md`, every file in `inputs/`, and all existing outputs (`01-system-map`, `02-process-*`, `03-gap`, `04-requirements`). These documents *assemble and translate* earlier analysis — they should add little new analysis. If key outputs are missing, say which documents will be thin and suggest the skill to run first; continue only if the user agrees.
2. **Check before writing** in one message:
   - Exec pack: who the audience is (names/roles), what decision or approval you're asking for, the meeting length/format, and any cost or benefit figures the user can provide (rates, salaries, budgets). Never invent money figures.
   - Analyst pack: who will read it (new BA joining, handover, review), and whether any decisions/assumptions need recording that aren't in the files yet.
   - Any document you plan to skip because evidence is missing.
   Wait for answers.
3. **Draft each document** following its file and the pack's audience rules. Keep IDs (`R-`, `G-`, `BR-`…) consistent with earlier outputs. In the exec pack, IDs go in footnotes or an appendix line, not the main text.
4. **Cross-check:** numbers, recommendations and priorities must match between the two packs and the source outputs. If sources conflict, raise it with the user rather than picking silently.
5. **Write** each document to `outputs/` as:
   - Exec pack: `05-exec-<NN>-<name>.md`
   - Analyst pack: `06-analyst-<NN>-<name>.md`
   (other audiences: next free number + `-<audience>-`). Use the header/footer from CLAUDE.md, adapted by the audience rules. Ask before overwriting; otherwise add `-v2`.
6. **Summarise in chat:** documents written, the one-sentence "ask" of the exec pack, open questions, and offer to turn the slide outline into a slide deck or the BRD into a shareable doc.

## Rules
- Exec pack translates; it never contradicts the analysis. Analyst pack keeps full detail and traceability.
- Money: show the formula and inputs; label estimates as estimates with a range; anything unknown is `TBD` with an open question.
- Respect `learning_mode` in context.md: analyst pack includes **Technique notes**; exec pack never does.
