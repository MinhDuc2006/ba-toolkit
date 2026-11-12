# Traceability matrix

## Purpose
Show how every business goal flows down to requirements and stories, and catch anything orphaned.

## Inputs
All IDs in the document.

## How to write
- One row per BR; list the SRs, FRs, NFRs and USs that trace to it.
- Add a row "Orphans" for any FR/US that doesn't trace to a BR.
- Add a row "Uncovered" for any BR with no FR or US.

## Format
| BR | Stakeholder reqs | Functional reqs | NFRs | User stories |
|---|---|---|---|---|
| BR-01 | SR-01 | FR-01, FR-02 | NFR-03 | US-01, US-02 |
| Orphans | | | | |
| Uncovered | | | | |

## Quality checks
- Orphans and uncovered rows are empty, or each entry is explained under Open questions.

## Technique note
A requirements traceability matrix (RTM) proves coverage and shows the impact of change: if a goal changes, you can see exactly which requirements and stories move with it.
