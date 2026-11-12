# RACI matrix: Stock ordering change

- **Engagement:** Harbour Lane Coffee Co. — Stock ordering review (`samples/coffee-chain`)
- **Date:** 2026-11-12
- **Mode:** `--no-questions`. Roles, not names, except where context.md names the person. **Two key roles are not yet filled:** the *end-to-end replenishment owner* (R-08, D-03) and the *stock-rules owner* (D-03). Every assignment to them is provisional until Priya decides.
- **Sources used:** `outputs/03-gap.md` §5–6 (R-, roadmap); `outputs/02-process-store-replenishment.md` §6–7 (T-, CH-, D-); `outputs/01-system-map.md` §4 (ownership ratings); `06-analyst-03-stakeholder-map.md`; `context.md` › Stakeholders.
- **Open questions:** Q-06, Q-16, Q-27 and Q-20 (see the end).

**Key:** **R** Responsible (does it) · **A** Accountable (one per row; signs off) · **C** Consulted (two-way) · **I** Informed (one-way) · **A/R** both · *(p)* = provisional, pending a decision.

**Roles:**
- **OD** Operations Director (Priya)
- **FIN** Head of Finance (Tom)
- **E2E** end-to-end replenishment owner (TBD)
- **SRO** stock-rules owner (TBD)
- **CO** Coordinator (Mei)
- **BK** coordinator backup (TBD)
- **SM** store managers
- **SL** shift leads
- **PK** pickers
- **IT** Josh + contractor
- **BA** Business analyst

---

## 1. Roadmap items (R-)
| Activity | OD | FIN | E2E | SRO | CO | BK | SM | SL | PK | IT | BA |
|---|---|---|---|---|---|---|---|---|---|---|---|
| R-08 Name owners and stock accountability | **A** | C | — | — | C | — | I | I | — | — | R |
| R-01 Shared issues log + complete waste logs | I | C | **A** | I | R | R | R | I | — | C | R |
| R-02 Substitution rule, what's-coming list, delivery sign-off | C | I | **A** | — | R | C | C | R | R | — | C |
| R-03 Document coordinator routines, train backup, individual logins | I | I | **A** | — | R | R | — | — | — | R | C |
| R-04 Standard template + StockPro import + late-order rule | I | I | **A** | C | C | C | C | — | — | R | R |
| R-05 Par reset and monthly review | I | — | C | **A/R** | C | I | C | — | — | — | C |
| R-06 Sales-suggested quantities + warehouse stock view | C | I | **A** | C | C | — | C | — | — | R | R |
| R-07 Pastry orders follow demand (if in scope) | I | C | C | **A** *(p)* | — | — | R | — | — | — | C |
| R-09 KPI set reviewed monthly | C | C | **A** | C | I | — | I | — | — | — | R |
| R-10 Warehouse system upgrade/replace decision | **A** | C | C | — | R | — | — | — | — | R | C |
| R-11 Electronic PO matching (parked; revisit after R-10) | I | **A** | — | — | C | — | — | — | — | R | C |
| R-12 Record supplier short-ships | — | I | **A** | — | R | R | — | — | C | — | — |

## 2. Decisions (D-)
| Decision | OD | FIN | E2E | SRO | CO | BK | SM | SL | PK | IT | BA |
|---|---|---|---|---|---|---|---|---|---|---|---|
| D-01 Late-order default | **A** | — | I | C | C | I | C | — | — | — | R |
| D-02 Substitution rule and approver | **A** | — | I | — | R | I | C | — | C | — | C |
| D-03 Owners of stock rules, issues log, pastry order (and E2E owner) | **A** | C | — | — | C | — | I | — | — | — | R |
| D-04 Accountability for stock at the store | **A** *(p)* | C | I | — | C | — | C | I | — | — | R |
| D-05 Waste baseline for the business case ($182k) | C | **A** | — | — | — | — | — | — | — | — | R |

## 3. Component and process ownership (to-be)
| Component / process | OD | FIN | E2E | SRO | CO | BK | SM | SL | PK | IT | BA |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Weekly replenishment, end to end (T-01–T-16) | I | I | **A** | C | R | R | R | R | R | C | — |
| Order template (T-01–T-04; replaces C-03) | — | — | **A** | C | C | — | R | — | — | R | C |
| Order import into StockPro (T-06) | — | — | **A** | — | R | R | — | — | — | C | — |
| Par levels and reorder points (C-21, T-16) | I | — | C | **A/R** | R | C | C | — | — | — | — |
| Substitution list (T-09) | — | — | **A** | — | R | C | I | — | R | — | — |
| What's-coming list (T-10) | — | — | **A** | — | R | R | I | I | C | — | — |
| Delivery receipt and stock at the store (T-12, T-13) | — | I | C | — | I | — | **A** *(p)* | R | — | — | — |
| Issues log and emergency top-ups (T-14, T-15; replaces C-05, C-06) | I | I | **A** | C | R | R | R | R | — | C | — |
| Waste logging (C-17, C-18) | I | **A** *(p)* | C | C | — | — | R | R | — | — | — |
| StockPro: operation and access (C-08) | I | I | C | — | **A** *(p)* | R | — | — | — | R | — |
| TillPoint: data owner (C-13) | **A** *(p)* | C | I | C | — | — | I | — | — | R | — |
| LedgerOne (C-14), unchanged | — | **A/R** | — | — | — | — | — | — | — | C | — |
| Coordinator procedures (FR-56) | — | — | **A** | — | R | R | — | — | — | — | C |
| New-store set-up (stores 13–17) | I | I | **A** | R | R | — | R | — | — | R | — |

## 4. Sign-offs and gates
| Sign-off / gate | OD | FIN | E2E | SRO | CO | BK | SM | SL | PK | IT | BA |
|---|---|---|---|---|---|---|---|---|---|---|---|
| BRD approval (06-analyst-02) | **A** | C | C | — | C | — | C | — | — | C | R |
| Business case content and board version | **A** | C | I | — | — | — | — | — | — | C | R |
| One-off spend within the ~$60k envelope | C | **A** | I | — | — | — | — | — | — | C | R |
| R-04 two-store pilot go/no-go (Feb 2027) | I | I | **A** | C | C | C | C | — | — | C | R |
| R-06 go/no-go (Mar 2027) | **A** | C | C | C | C | — | C | — | — | C | R |
| Go-live at all 12 stores | I | I | **A** | C | R | R | R | I | I | C | C |
| Backup test week (NFR-10) | I | — | **A** | — | C | R | I | — | — | — | — |

---

## Issues found
**Rows with no single confirmed A:**
- **D-04 Stock accountability at the store.** Sources name "Priya + Tom" jointly (02-process D-04; 04-requirements Q-03). Shared accountability usually means none, so OD is shown as A and FIN as C *(p)*. Confirm (Q-16).
- **TillPoint data owner (C-13).** The owner is `TBD` in every source (system map Q-02 → Q-06). OD is shown provisionally.
- **StockPro (C-08).** "Owned by warehouse (Mei)" is an [Assumption] in the system map. Who supports it (Josh, the contractor or the vendor) is unknown (H-27).
- **Waste logging (C-17, C-18).** Ownership is split today ("stores fill it, Finance uses it"). FIN is shown provisionally as A.
- **Delivery receipt.** Store managers as A follows the BA proposal in 05-exec-03 decision 2, and is not yet decided.
- **R-07 Pastry.** The stock-rules owner is assumed to also own the pastry standing order. D-03 may name a different person.

**Roles with too many Rs:**
- **Coordinator (Mei): R on 15 of 38 rows.** She is today's single point of failure (G-01, RC-07), and the change plan loads her further during Now and Next. Mitigation: the backup (BK) shares Rs as soon as they are named (Q-20), and BA support is protected for write-up sessions.
- **BA: R on 14 rows**, all preparation (options, builds, packs). Acceptable for an engagement role. The BA holds no ongoing ownership in §3, so nothing is orphaned at handover.

**Roles with too many As:**
- **E2E owner: A on 18 rows.** This is intended (it fixes RC-04), but the role must be real and have time. If Priya takes it herself, OD and E2E merge, and her decision load rises. Raise it with Priya when making D-03.

**Ownership gaps from the system map (🟠/🔴 for Ownership), and where this RACI closes them:**

| System-map gap | Closed by row |
|---|---|
| C-01 store managers 🟠 (each does it differently) | Weekly replenishment end to end (E2E = A) |
| C-03 Excel files 🟠 | Order template |
| C-05 WhatsApp 🟠, C-06 sticky notes 🟠 | Issues log and emergency top-ups |
| C-08 StockPro 🟠 | StockPro operation and access *(p)* |
| C-11 shift leads 🟠 | Delivery receipt *(p)* |
| C-13 TillPoint 🟠 | TillPoint data owner *(p)* |
| C-17 waste log 🟠, C-18 Google Sheet 🟠 | Waste logging *(p)* |
| C-20 Crumb & Co. 🟠 | R-07 *(p)* |
| C-21 par levels / reorder points 🟠 | Par levels and reorder points (SRO) |
| H-10 discrepancy reports 🟠, H-11 substitution notice 🟠 | Issues log; substitution list; what's-coming list |

**Check:** every row has exactly one A and at least one R.

---

## Open questions
*(not asked — --no-questions)*
- **Q-27 / D-03** Who will be the end-to-end owner and the stock-rules owner? Is it one person or two?
- **Q-16 / D-04** Who is accountable for stock once it is signed for at a store? Priya and Tom are named jointly today.
- **Q-06** What are the reporting lines, and who owns TillPoint?
- **Q-20** Who will be the coordinator backup, and when can they be trained?

## Next steps
1. Take this RACI into the 30 Nov decision meeting. Filling E2E, SRO and BK removes most *(p)* marks.
2. Re-issue the RACI with names after D-03 and D-04, and add it to the store routine and to the coordinator procedures (FR-55, FR-56).
3. Check Mei's load with her during validation. Move Rs to the backup where possible.

## Technique notes
- **RACI.** A RACI fixes accountability gaps. "Exactly one A" is the rule that matters most, because shared accountability usually means none. That's why D-04's joint "Priya + Tom" is flagged rather than copied.
- **Counting Rs and As.** Counting Rs per role is a quick overload check. Here it shows that the change plan leans on the same person it is meant to de-risk (Mei).
