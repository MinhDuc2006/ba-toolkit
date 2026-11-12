# Non-functional requirements

## Purpose
Define how well the solution must perform — the quality attributes and constraints.

## Inputs
context.md › Constraints and risks, Data and metrics, Current systems, Stakeholders.

## How to write
Consider each category; include only those that apply, and say which you skipped and why:
- Performance (response time, throughput, volumes)
- Availability and reliability (uptime, opening hours, recovery)
- Security and privacy (access, data protection, regulations)
- Usability and accessibility (training time, device types, WCAG)
- Scalability (growth expected)
- Compliance and audit (logs, retention)
- Compatibility and integration (existing systems)
- Supportability (who maintains it, documentation)

Make each one measurable: "<attribute> shall be <number + unit> under <conditions>."

## Format
| ID | Category | Requirement | Measure | Source |
|---|---|---|---|---|
| NFR-01 | Performance | Order lookup shall return results … | ≤ 2 s at 200 concurrent users | context.md › Data |

## Quality checks
- Every NFR has a number or a verifiable condition.
- If a number isn't known, mark it `TBD` and add an open question rather than guessing.

## Technique note
NFRs are the most often forgotten and the most expensive to fix late. Vague ones ("must be fast") are untestable — always push for a number.
