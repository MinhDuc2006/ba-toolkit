# Health assessment

## Purpose
Show how each component and handoff scores against every criterion, with evidence.

## How to write
- One row per component (and per handoff with an issue); one column per file in `criteria/` (the example below shows the default nine — add/remove columns to match).
- Cell = rating emoji; leave blank if not relevant. Final column = overall rating + one-line reason.
- Below the table, a short evidence list for every 🟠 and 🔴 rating.

## Format
| ID | Part | Ownership | Integration | Data | Controls | Usability | Reliability | Knowledge | Security | Cost | Overall | Why |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C-01 | Order spreadsheet | 🟠 | 🟠 | 🟠 | 🟠 | 🟡 | 🟢 | 🟠 | 🟠 | 🟡 | 🟠 Too loose | No validation; re-keyed daily; shared file |

## Technique note
Scoring against fixed criteria keeps the assessment fair and repeatable; it also shows *why* a part is weak, which points to the right fix.
