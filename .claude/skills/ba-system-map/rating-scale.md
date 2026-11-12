# Rating scale

Every component and handoff gets exactly one overall rating.

| Rating | Meaning | Typical signs | Typical response |
|---|---|---|---|
| 🟢 **Solid** | Works well, clearly owned, controlled, fit for current and expected needs. | Few complaints, reliable data, documented, one clear owner. | Leave alone; protect it during change. |
| 🟠 **Too loose** | It works, but is weakly defined or controlled — results depend on people remembering things. | No clear owner; manual re-keying or copy-paste between systems; rules in people's heads; no validation or approval step; side spreadsheets; email/phone handoffs; different teams doing it differently. | Tighten: define ownership, standardise, add controls/validation, integrate or remove manual handoffs. |
| 🟡 **Can be improved** | Well defined and reliable, but slower, costlier or clunkier than it needs to be. | Extra steps, waiting, duplicate data entry with low error rate, poor usability, reports built by hand. | Optimise: quick wins, automation, simplification. |
| 🔴 **Needs more work** | Broken, missing, at risk, or not understood well enough to judge. | Frequent failures or errors; missing capability; end-of-life or unsupported; single point of failure; no evidence available. | Fix, replace, build, or investigate further (say which). |

Tie-breaks: if a part is both loose and broken → 🔴. If it is both loose and slow → 🟠 (control before speed).

Mermaid colours (use as `classDef` in diagrams):
```
classDef solid fill:#d1fadf,stroke:#12b76a,color:#054f31
classDef loose fill:#ffead5,stroke:#f79009,color:#7a2e0e
classDef improve fill:#fef7c3,stroke:#eaaa08,color:#713b12
classDef work fill:#fee4e2,stroke:#f04438,color:#7a271a
```
