# As-is process map

## Purpose
Show how the process really works today, who does each step, and where it goes wrong.

## How to write
- Mermaid `flowchart LR` with one `subgraph` per lane (role, team, or system) to act as swimlanes.
- Nodes: `P-01 verb + object` (e.g. "P-03 Re-key order"). Start/end as rounded nodes `([ ])`, decisions as `{ }`.
- Show exception paths and rework loops — they're usually the point.
- Dashed edges (`-.->`) for manual handoffs (email, phone, paper, re-keying).
- Highlight problem steps with `classDef pain fill:#fee4e2,stroke:#f04438,color:#7a271a` and add a legend.
- Over ~20 steps: draw a high-level map plus a detailed map of the worst sub-process.

## Format
```mermaid
flowchart LR
  subgraph Customer
    S([Places order])
  end
  subgraph Store staff
    P01[P-01 Write order on paper] --> P02[P-02 Re-key into POS]
    P02 --> D1{Stock ok?}
  end
  S --> P01
  D1 -- no --> P03[P-03 Phone supplier]
  classDef pain fill:#fee4e2,stroke:#f04438,color:#7a271a
  class P02 pain
```
Legend: red = pain point · dashed = manual handoff

## Technique note
Swimlane diagrams make handoffs visible: every time the flow crosses a lane, ownership changes — and that's where delays and errors cluster.
