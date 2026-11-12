# Assumptions, decisions and open questions register

## Purpose
One place for everything that's assumed, decided, or still unknown across the engagement — so nothing is lost between documents.

## Inputs
Every `[Assumption]`, `TBD` and Open questions list across context.md and all outputs; decisions the user tells you about.

## Structure
1. **Assumptions** — ID `A-01…`, statement, where used (file + IDs), risk if wrong (H/M/L), owner to validate, status (open/confirmed/rejected).
2. **Decisions** — ID `D-01…`, decision, date, who decided, rationale, alternatives rejected, affected IDs.
3. **Open questions** — ID `Q-01…`, question, raised in, ask whom, needed by, status. Deduplicate questions repeated across outputs.

## Format
| ID | Assumption | Used in | Risk if wrong | Validate with | Status |
|---|---|---|---|---|---|
| A-01 | Staff cost ≈ $30/h | 05-exec-02-business-case | M | Finance | Open |

## Quality checks
- Every `[Assumption]` and `TBD` in the outputs appears here.
- High-risk assumptions have an owner and a date.

## Technique note
Assumption and decision logs (RAID logs: Risks, Assumptions, Issues, Dependencies) protect the BA when stakeholders later ask "why did we do it this way?".
