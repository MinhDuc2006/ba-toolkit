# Pain points and bottlenecks

## Purpose
Pull out the problems the analysis found, ranked, so the to-be design addresses the right things.

## How to write
- **Bottleneck:** the step with the longest wait in front of it or lowest capacity — name it explicitly.
- List each pain point with step IDs, lens findings, business impact (time, cost, errors, customer), and link to context.md pain points where they match.
- Rank by impact. Flag symptoms whose cause isn't clear as candidates for `/ba-gap` root-cause analysis.

## Format
**Bottleneck:** P-0x — …

| # | Pain point | Steps | Finding (lens) | Impact | Links | Root cause known? |
|---|---|---|---|---|---|---|
| 1 | | P-02, P-03 | Waiting, Defects | ~2 h delay per order | context.md › Pain points #2, H-01 | No → /ba-gap |

## Technique note
Theory of Constraints: a process can only go as fast as its bottleneck. Improving any other step first adds little.
