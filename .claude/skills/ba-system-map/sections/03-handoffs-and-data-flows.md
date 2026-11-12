# Handoffs and data flows

## Purpose
Detail every connection between components — this is where loose systems usually leak.

## How to write
- One row per edge in the diagram.
- Mode: automated / manual / mixed. Frequency and volume if known.

## Format
| ID | From → To | What moves | Mode | Frequency | Rating | Issue | Source |
|---|---|---|---|---|---|---|---|
| H-01 | C-02 → C-01 | Daily sales totals | Manual re-key | Daily | 🟠 | Typos, 30 min/day | inputs/notes.md |

## Technique note
Most process failures happen at handoffs, not inside components. Mapping them separately makes "too loose" areas obvious.
