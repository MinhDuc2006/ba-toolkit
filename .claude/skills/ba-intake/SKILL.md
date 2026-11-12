---
name: ba-intake
description: Interview the user topic by topic to build an engagement's context.md (company, goals, stakeholders, systems, processes, pain points, data, constraints, scope). Use when starting a new BA engagement or filling gaps in an existing context.md.
argument-hint: <engagement-folder> [topic-name ...]
---

# /ba-intake — build the engagement context

Arguments: `$ARGUMENTS`
- 1st argument: engagement folder (e.g. `projects/acme`, `samples/coffee-chain`). If missing, list folders under `projects/` and `samples/` and ask.
- Optional extra arguments: topic names (e.g. `stakeholders pain-points`) to run only those topics.

## Topics are modular
Each file in `topics/` (next to this SKILL.md) is one interview topic. Read all of them, sorted by filename. To add a topic, the user just adds a new `NN-name.md` file in the same format — do not hard-code the topic list anywhere.

Each topic file has: `Goal`, `Core questions`, `Follow-up probes`, and `Captures` (what goes into context.md under that topic's heading).

## Steps
1. **Set up the folder.** If the engagement folder doesn't exist, create it with `inputs/` and `outputs/`, after confirming the name with the user.
2. **Read what already exists.**
   - `context.md` (if present): note which topic sections are filled, partial (contains `TBD` or `[Assumption]`), or missing.
   - Every file in `inputs/`: pre-fill answers you can find there, citing the file.
3. **Show a topic checklist** to the user: each topic with status (✅ filled / 🟡 partial / ⬜ missing / 📄 pre-filled from inputs). Ask which to cover now. Default: all missing and partial topics, in file order. Let the user skip any.
4. **Interview one topic at a time.**
   - Ask that topic's core questions in a single message (max ~5). Skip ones already answered by inputs; instead state what you found and ask the user to confirm.
   - Use follow-up probes only where answers are vague, contradictory, or important.
   - Accept "don't know" — record it as `TBD` and add it to Open questions.
   - After each topic, give a 2–3 line summary and ask for corrections before moving on.
   - The user can say "stop" at any time; save progress so far.
5. **Write `context.md`** using `context-template.md` (next to this SKILL.md):
   - One `##` section per topic, in topic-file order, heading = the topic's title.
   - Mark the source of each fact: `(user)`, `(inputs/<file>)`, or `[Assumption]`.
   - When updating an existing file, change only the sections covered in this session and keep everything else as-is.
   - Update the header (last updated date, topic status table) and the Open questions list.
6. **Finish** with: topics still missing/partial, the top 3 open questions, and which `/ba-*` skill makes sense next (usually `/ba-system-map` next; pain points heavy → `/ba-gap`; process described → `/ba-process`).

## Rules
- Never invent company facts. If the user asks you to "make up something plausible" (e.g. for practice), mark all of it `[Assumption]`.
- Keep the user's own wording for goals and pain points; you may tidy it but don't change the meaning.
- Respect `learning_mode` in context.md: when on, after each topic add one line on *why* a BA asks about this.
