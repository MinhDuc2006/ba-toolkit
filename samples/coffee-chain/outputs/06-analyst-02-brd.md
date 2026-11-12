# Business Requirements Document (BRD): Stock ordering

- **Engagement:** Harbour Lane Coffee Co. — Stock ordering review (`samples/coffee-chain`)
- **Date:** 2026-11-12
- **Mode:** `--no-questions`. Assembled from earlier outputs. No new analysis, and nothing was confirmed with the user or stakeholders.
- **Sources used:** `context.md`; `inputs/01`–`05`; `outputs/01-system-map.md` (C-, H-); `02-process-store-replenishment.md` (P-, T-, CH-, D-); `03-gap.md` (TS-, G-, RC-, R-); `04-requirements.md` (BR-, SR-, FR-, NFR-, US-), which is the **main source**; `05-exec-02-business-case.md`.
- **Open questions:** key ones are listed in §11. The full set is in [06-analyst-05](06-analyst-05-assumptions-decisions-register.md) (consolidated Q-IDs).

---

## 1. Document control
| Item | Value |
|---|---|
| Version | 0.1 (draft for review) |
| Date | 2026-11-12 |
| Author | Business Analyst |
| Reviewers | Priya Nair (sponsor), Tom Reyes (Finance), Mei Chen (SME), Josh (IT), a store manager. Not yet reviewed |
| Approval status | **Not approved.** Sign-off table in §12 |
| Change log | 0.1, 2026-11-12: first assembly from outputs 01–04 |

## 2. Executive summary
Ordering across 12 stores and one warehouse runs on paper counts, 12 different Excel files, email, WhatsApp and StockPro. One coordinator re-keys ~480 lines a week.

**Outcomes:**
- **Stockouts:** 4.5/wk reported, likely under-reported (BR-01).
- **Recorded waste:** ≈ $182k/yr (BR-02).
- **Couriers:** ≈ $19k/yr.
- **Ordering effort:** 36–50 h/wk (≈ $70k–$97k/yr of staff time).
- **Continuity:** a failure in Aug 2026 when the coordinator was away (BR-05).

**Root causes** (03-gap §2):
- unowned stock rules (RC-01)
- unused demand and stock data (RC-02)
- no standard order format (RC-03)
- no end-to-end owner (RC-04)
- unowned pastry orders (RC-05)
- no measurement (RC-06)
- undocumented coordinator knowledge (RC-07)

**What is required:** rules, owners, a standard template loaded through StockPro's existing import, a shared issues log, and sales data at the point of ordering. **No new core system** is required in this release (NFR-23, D-08).

**Scale of the requirements:** 7 BRs, 23 SRs, 59 FRs (33 Must, 18 Should, 5 Could, 3 Won't), 28 NFRs and 35 user stories.

The recommended delivery is Option 2, staged ([05-exec-02](05-exec-02-business-case.md)).

## 3. Business objectives and success metrics
| ID | Objective | Baseline → target | Goal / TS | Source |
|---|---|---|---|---|
| BR-01 | Keep core items in stock | 4.5/wk → ≤ 2.25/wk by July 2027 | Objective 1 / TS-1 | inputs/01, 05 |
| BR-02 | Cut stock waste | ≈ $182k/yr → $146k–$164k/yr | Objective 2 / TS-2 | inputs/01, 04 |
| BR-03 | Scale to 17+ stores with one coordinator | 1 → 1; ~480 → ~680 lines/wk | Objective 3 / TS-3 | inputs/01, 03 |
| BR-04 | Less manager ordering time | 2.5–3.5 h/wk per store → `TBD` (Q-05) | Objective 4 / TS-4 | inputs/02, 05 |
| BR-05 | Ordering continues when the coordinator is away | Aug 2026 failure → backup runs a full week in a test | Driver / TS-3 | inputs/01, 03 |
| BR-06 | Accountability and trusted measures | "Nobody is accountable" → named owners; 12/12 stores logging | TS-5 [Assumption] | inputs/04 |
| BR-07 | Supported warehouse system after Dec 2027 | End of support Dec 2027 → supported system before then | Constraint-derived | inputs/03 |

The full wording is in [04-requirements §1](04-requirements.md). BR-06 and BR-07 are not among the sponsor's stated objectives and need confirming (Q-35).

## 4. Scope
| | Items |
|---|---|
| **In scope** | Weekly store replenishment (store → warehouse → store); mid-week emergency top-ups; warehouse reorder points; the measures needed for the business case |
| **In, scope `TBD`** | Pastry standing orders (R-07, FR-46, FR-47; Q-01); waste recording beyond completeness (FR-44; Q-02) |
| **Out** | Replacing LedgerOne (mandated); invoice matching (R-11, FR-57 Won't, D-06); dairy ordering (FR-58 Won't, D-07); selecting or implementing a new warehouse system (R-10, FR-59 Won't this release, D-09) |
| **Parked** | R-11 electronic PO matching until after the R-10 decision |

**Constraints** (context.md › Constraints; NFR-22, 26, 27):
- One-off spend ≤ ~$60k by 30 Jun 2027, and ongoing costs must pay back in < 18 months.
- Change freeze from 1 Dec 2026 to 31 Jan 2027.
- Live before the new stores open (July 2027).
- LedgerOne must stay.
- IT is one generalist plus a contractor.
- StockPro reaches end of support in Dec 2027.

**Key assumptions** (full list in 06-analyst-05):
- **A-05:** logging and rules are allowed during the freeze.
- **A-09:** re-keying falls below 1 h/wk.
- **A-14:** the StockPro import and export are usable.
- **A-15:** till items can be mapped to stock items.
- **A-31:** other stores work like Docklands.

**Dependencies:**
- R-08 → R-02, R-05, R-09
- R-03 → R-05
- R-04 → R-06
- R-01 → R-09
- R-10 → R-11
- The Q-08 import format gates FR-14.
- Q-09 item mapping gates FR-17 to FR-19.

## 5. Stakeholders
Summary of [06-analyst-03](06-analyst-03-stakeholder-map.md).
- **Decision-makers:**
  - Priya Nair (sponsor)
  - Tom Reyes (budget; sceptical, wants evidence)
  - CEO + 2 investors (final audience)
- **Key SME and single point of failure:** Mei Chen.
- **Users:**
  - 12 store managers (one interviewed)
  - shift leads and baristas
  - 2 pickers and 1 driver
  - accounts assistant
- **Enablers:** Josh (IT, not yet interviewed), the on-call contractor, the StockPro vendor.
- **External:** Crumb & Co., Valley Dairy, warehouse suppliers, the courier.
- **Main conflicts:**
  - waste figure: $182k vs $250k
  - lost sales: "big" vs needs evidence
  - "just in case" stock vs waste
  - busy shifts vs delivery sign-off

## 6. Current state
Detail is in [01-system-map](01-system-map.md) and [02-process §2–5](02-process-store-replenishment.md).
- **23 components and 27 handoffs.**
  - Components: 🟢 2 · 🟠 8 · 🟡 7 · 🔴 6.
  - Handoffs: 🟢 3 · 🟠 9 · 🟡 8 · 🔴 7.
  - Only 2 flows are system-generated.
- **The 🔴 components are:**
  - Mei (C-07)
  - StockPro (C-08)
  - the paper waste log (C-17)
  - the Crumb & Co. standing order (C-20)
  - par levels and reorder points (C-21)
  - IT support (C-22)
- **Weekly replenishment** has 17 steps (P-01–P-17): 3 VA, 3 BVA and 11 NVA. Seven of them are failure-driven.
  - The bottleneck is P-06 (re-keying).
  - None of the 4 decision points has a written rule.
- **Four flows are missing:**
  - substitution notice (H-11)
  - par levels in use (H-14)
  - sales to ordering (H-23)
  - warehouse stock to stores (H-24)

## 7. Future state
Detail is in [02-process §6–7](02-process-store-replenishment.md) and [03-gap §5–6](03-gap.md).
- **To-be process:** 16 steps (T-01–T-16) with 5 NVA. 1 unstructured handoff remains (down from 8), and all 4 decision points have written rules.
- **Changes CH-01 to CH-14** are grouped into recommendations:

| R | Recommendation | CH- | Horizon |
|---|---|---|---|
| R-01 | Shared issues log and complete waste logs | CH-10 | Now |
| R-02 | Substitution rule, what's-coming list, delivery sign-off | CH-07, CH-08, CH-09 | Now (rules) → Next (live) |
| R-03 | Document coordinator routines, train a backup, individual logins | CH-13, CH-14 | Now |
| R-04 | Standard template + StockPro import + late-order rule | CH-01, CH-02, CH-06 | Next |
| R-05 | Stock-rules owner, par reset, monthly review | CH-12 | Next |
| R-06 | Sales-suggested quantities, warehouse stock view, lighter counting | CH-03, CH-04, CH-05 | Next → Later (go/no-go Mar 2027) |
| R-07 | Pastry orders follow demand | — (outside the mapped process) | Now (if in scope) |
| R-08 | End-to-end owner and stock accountability | D-03, D-04 | Now |
| R-09 | KPI set reviewed monthly | — | Next |
| R-10 | Warehouse system upgrade or replacement decision | — | Later (~Sep 2027) |
| R-11 | Electronic PO matching | — | Parked |
| R-12 | Supplier short-ships recorded | — (folded into CH-10 / CH-07) | Later / ongoing |

CH-11 (emergency borrow-vs-courier rule) sits under R-01/R-02 in practice. It has no separate R- in 03-gap; see 06-analyst-06 § ID notes.

## 8. Requirements
The full tables are in [04-requirements §2–4](04-requirements.md). They are summarised here rather than duplicated.

| Area | FRs | Musts | Key NFRs |
|---|---|---|---|
| 3.1 Order capture (template) | FR-01–08 | 01–04, 08 | NFR-17, 20 |
| 3.2 Order submission | FR-09–13 | 09–12 | NFR-05, 09 |
| 3.3 Order import | FR-14–16 | 14, 15 | NFR-01, 02, 07, 11 |
| 3.4 Demand and stock data | FR-17–21 | — (all Should/Could) | NFR-03, 04 |
| 3.5 Stock rules | FR-22–26 | 22–24, 26 | NFR-15 |
| 3.6 Picking and substitutions | FR-27–30 | 27–29 | — |
| 3.7 Dispatch notice and receipt | FR-31–36 | 31, 32, 34, 35 | NFR-06, 18 |
| 3.8 Issues log and emergencies | FR-37–43 | 37–39, 42 | NFR-14, 19, 21 |
| 3.9 Waste and pastry (scope TBD) | FR-44–47 | 45 | NFR-16 |
| 3.10 Reporting and KPIs | FR-48–52 | 48, 49 | — |
| 3.11 Access, ownership, continuity | FR-53–56 | 53–56 | NFR-10, 12, 13 |
| 3.12 Not this release | FR-57–59 | Won't | NFR-23, 24, 28 |

**Stakeholder requirements:** SR-01 to SR-23 (04-requirements §2). The orphan is SR-21 (accounts assistant → R-11, parked).

**Constraint NFRs:**
- NFR-22: LedgerOne unchanged.
- NFR-26: budget.
- NFR-27: delivery window.

**MoSCoW:** Musts are 33 of 56 active FRs (59%). The costliest items (FR-17–20) are deliberately Should (04-requirements §7). Confirm with Priya and Tom (Q-35).

## 9. User stories and acceptance criteria
- There are **35 user stories in 9 epics.** 23 are Must and 12 are Should ([04-requirements §5](04-requirements.md)).
- Every Must story has Given/When/Then acceptance criteria, with at least one exception path ([04-requirements §6](04-requirements.md)).
- **Musts:** US-01–03, 05, 06, 08–10, 15, 16, 18–21, 23–25, 28, 31–35.
- **Gated stories:**
  - US-09 (import) by Q-08.
  - US-12 and US-14 by Q-08 and Q-09.
  - US-06 by D-01.
  - US-19 by D-02.
  - US-23 and US-34 by D-04.

## 10. Traceability (extended back to gaps and root causes)
The forward matrix (BR → SR, FR, NFR, US) is in [04-requirements §8](04-requirements.md). The table below extends it **backwards** to the analysis.

| BR | Gaps (G-) | Root causes (RC-) | Recommendations (R-) | Process changes (CH-) | Must FRs |
|---|---|---|---|---|---|
| BR-01 Stockouts | G-04, G-05, G-06, G-10, G-11, G-16, G-20 | RC-01, RC-02, RC-04, RC-06 | R-01, R-02, R-05, R-06, R-12 | CH-04, CH-05, CH-07, CH-08, CH-09, CH-10, CH-11, CH-12 | FR-04, 22, 23, 27–29, 31, 32, 37, 39, 48 |
| BR-02 Waste | G-11, G-14, G-17, G-19 | RC-01, RC-05, RC-06 | R-01, R-05, R-07 | CH-12 | FR-22, 23, 45 |
| BR-03 Scale | G-03, G-07 | RC-03 | R-04 | CH-01, CH-02, CH-06 | FR-01–03, 08, 09, 11, 12, 14, 15 |
| BR-04 Manager time | G-02, G-10 | RC-02, RC-03 | R-04, R-06 | CH-01, CH-03, CH-04 | FR-01, 10 |
| BR-05 Continuity | G-01 | RC-07 | R-03 | CH-14 | FR-11, 14, 26, 39, 42, 56 |
| BR-06 Accountability and measures | G-12, G-13, G-15, G-16, G-17, G-18 | RC-04, RC-06 | R-01, R-03, R-08, R-09 | CH-09, CH-10, CH-13 | FR-24, 29, 34, 35, 37, 38, 45, 48, 49, 53–55 |
| BR-07 Supported warehouse system | G-08 | — (constraint/risk, not a root cause) | R-10 | — | none (FR-59 Won't; protected by NFR-23, 24, 28) |
| *No BR* | G-09 | — | R-11 (parked) | — | FR-57 (Won't) |

**Coverage checks:**
- Every RC (01–07) reaches at least one BR.
- Every High gap is covered. The list is G-01, 03, 04, 07, 08, 10, 11, 13, 14, 16, 17, 19.
- Every Must FR traces to BR-01 to BR-06.
- Not covered (explained): BR-07 has no active FR, and G-09/FR-57 have no BR.

## 11. Risks, issues and open questions
| Type | Item | Mitigation / owner |
|---|---|---|
| Risk | The StockPro import can't load store orders (A-14) | Vendor answer by 31 Jan (Q-08), Mei/Josh |
| Risk | Till items can't be mapped to stock items (A-15) | March go/no-go for R-06 (Q-09), Josh |
| Risk | IT capacity Feb–Jun (Q-10) | Priya to confirm Josh's time |
| Risk | Adoption (Tom: "another system nobody uses properly") | Pilot in 2 stores; NFR-21 adoption measure |
| Risk | Reported stockouts rise once logging starts | Agree with Priya and Tom before go-live |
| Risk | StockPro end of support (Dec 2027) | R-10 decision by ~Sep 2027; NFR-24 portability |
| Issue | Waste baseline disputed ($182k vs ~$250k) | D-05 (proposed): use $182k; Q-03 |
| Issue | The analysis rests on one store-manager interview | Validate with a second manager (Q-14, A-31) |
| Issue | Substitution rule timing differs (02-process Phase 0 vs 03-gap Now/freeze) | Q-39 |

**Top open questions** (consolidated IDs):
- Q-01 pastry scope
- Q-03 waste baseline
- Q-08 import format
- Q-09 item mapping
- Q-16 stock accountability (D-04)
- Q-26 late-order default (D-01)
- Q-27 owner of stock rules (D-03)
- Q-35 agree Musts, BR-06 and BR-07

## 12. Glossary and sign-off
The glossary is in [06-analyst-06](06-analyst-06-glossary-and-id-index.md).

| Role | Name | Signs off | Decision | Date |
|---|---|---|---|---|
| Sponsor / Operations Director | Priya Nair | Objectives, scope, Musts, D-01–D-04 | Pending | |
| Head of Finance | Tom Reyes | BR-02, BR-06, budget constraint, business case basis | Pending | |
| Warehouse & Purchasing Coordinator (SME) | Mei Chen | FR-14–16, FR-26–30, FR-39–43, procedures | Pending | |
| IT | Josh | NFR-09, 12–15, 23–25; feasibility of FR-14, FR-17–20 | Pending | |
| Store manager representative | Daniel Okafor (or nominee) | FR-01–13, FR-31–36, NFR-17–20 | Pending | |

---

## Open questions
*(not asked — --no-questions)*
- **Q-35** Do Priya and Tom agree the Must list, BR-06 and BR-07, and the handling of the stakeholder conflicts?
- **Q-43** Who are the actual reviewers, and is this BRD the sign-off document, or are the exec pack decisions enough?
- **Q-39** Should the substitution rule be agreed before 30 Nov or during the freeze?

## Next steps
1. Circulate v0.1 to the reviewers in §1 after the 30 Nov decision meeting, with D-01–D-04 filled in.
2. Update §4 scope once Q-01 and Q-02 are answered, and move FR-44–47 to Must or Won't accordingly.
3. Re-baseline §3 with the first 6–8 weeks of issues-log data (R-01) before sign-off.

## Technique notes
- **The BRD as a contract.** The BRD consolidates the "what and why" for sign-off. It is a contract between business and delivery, and ambiguity here becomes cost later. Linking rather than duplicating (§8, §9) keeps one source of truth: 04-requirements.
- **Backward traceability.** Forward traceability (BR → FR) proves coverage. Backward traceability (BR → G → RC → R) proves every requirement exists because of a real, evidenced problem. That is the defence when a stakeholder asks "why do we need this?".
