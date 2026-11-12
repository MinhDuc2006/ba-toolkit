# Functional requirements

## Purpose
Define what the solution must do — the behaviours and functions.

## Inputs
Business and stakeholder requirements above; context.md › Processes, Current systems.

## How to write
- "The system shall <verb> <object> [condition]."
- Group by feature area or process step (use process names from context.md).
- Include data, reporting, integration and notification needs, not just screens.
- Record business rules (calculations, validations, approvals) as their own FRs.

## Format
### <Feature area>
| ID | Requirement | Traces to | Priority | Source |
|---|---|---|---|---|
| FR-01 | The system shall … | BR-01, SR-02 | Must | context.md › Processes |

## Quality checks
- Single behaviour per FR; testable; unambiguous (no "fast", "easy", "user-friendly" — those belong in NFRs with numbers).
- No implementation detail unless it is a stated constraint.
- Each FR traces to at least one BR or SR.

## Technique note
Good FRs are atomic and testable. A tester should be able to write a pass/fail check from each one without asking the author.
