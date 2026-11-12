# Step analysis table

## Purpose
Hold the detail behind the map: who, which system, how long, and what's wrong with each step.

## How to write
- One row per as-is step. Times as "touch / wait" in consistent units; ranges allowed; `TBD` if unknown.
- Value class from the value-analysis lens; waste tags from the Lean lens.
- System column uses system-map `C-` IDs where available.

## Format
| Step | Description | Who | System | Touch time | Wait before | Value | Waste | Issue | Source |
|---|---|---|---|---|---|---|---|---|---|
| P-02 | Re-key order into POS | Store staff | C-02 | 3 min | 0–2 h | NVA | Transportation, Defects | 5% typos | inputs/notes.md |

## Technique note
Separating touch time from wait time is the key insight: improvement usually comes from cutting waiting, not making people work faster.
