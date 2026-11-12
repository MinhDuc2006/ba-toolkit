# Glossary and ID index

- **Engagement:** Harbour Lane Coffee Co. — Stock ordering review (`samples/coffee-chain`)
- **Date:** 2026-11-12
- **Mode:** `--no-questions`. Terms are defined from how they are used in the inputs and outputs, and have not been checked with the company.
- **Sources used:** `context.md`; `outputs/01-system-map.md`, `02-process-store-replenishment.md`, `03-gap.md`, `04-requirements.md`; `05-exec-*`; `06-analyst-*`.
- **Size rule applied:** the engagement has well over 150 IDs (≈ 330). Section 3 indexes **C-, G-, RC-, R-, BR-** in full, plus the short sets TS- and D-. Every other prefix is given as a range with a link to its defining file.
- **Open questions:** Q-06 (who owns TillPoint, which affects the glossary entry) and Q-41.

---

## 1. Glossary

### Company, systems and people
| Term | Definition |
|---|---|
| **Harbour Lane Coffee Co.** | A fictional 12-store coffee chain (≈ 140 staff, ≈ $14M/yr), growing to 17 stores by July 2027 |
| **Docklands** | The busiest store. Its manager, Daniel Okafor, is the only store manager interviewed |
| **Central warehouse** | One site with 4 staff (coordinator, 2 pickers, 1 driver). It supplies beans, cups and lids, syrups, plant milks, snacks and cleaning products |
| **Coordinator** | The Warehouse & Purchasing Coordinator, Mei Chen. She re-keys orders, sets reorder points, raises POs and books couriers. She is the single point of failure (C-07) |
| **Coordinator backup** | A new role (R-03): a trained person who can run a full ordering week without Mei. Not yet named (Q-20) |
| **Stock-rules owner** | A new role (D-03, R-05): owns par levels and reorder points and reviews them monthly. Not yet named |
| **End-to-end (E2E) owner** | A new role (R-08): accountable for the whole replenishment process from store order to signed-off delivery. Not yet named |
| **StockPro** | The warehouse inventory system (~9 years old): stock, POs, pick lists, goods received. It has an unused CSV import and one shared login. The current version reaches end of support in Dec 2027 (C-08) |
| **TillPoint (POS)** | The point-of-sale (till) system. It records sales by product and exports a CSV daily. Used only for revenue reporting today (C-13). Owner `TBD` (Q-06) |
| **LedgerOne** | The accounting system. Recently implemented and mandated: it must not change (C-14, NFR-22) |
| **orders@** | The shared inbox where stores email their weekly Excel order files (C-04) |
| **Valley Dairy** | The fresh dairy milk supplier. Each store orders daily by phone or web form (C-19). Scope `TBD` |
| **Crumb & Co.** | The partner bakery. A standing daily pastry order per store, changed "maybe twice a year" (C-20). Pastries ≈ $96k of waste |
| **Core items** | The items whose stockouts are tracked: oat milk (1L), 16oz cups, 16oz lids, vanilla syrup, decaf beans (inputs/05) |
| **Change freeze** | No big changes from 1 Dec to 31 Jan (peak season). Assumed to allow logging and rule changes (A-05) |

### Stock and ordering terms
| Term | Definition |
|---|---|
| **Par level** | The target quantity of an item a store should hold. The order tops stock up to par. In the store Excel files but not updated since 2024 (C-21) |
| **Reorder point** | The warehouse stock level at which a new purchase order is raised. Set by Mei "from experience" (C-21, H-15) |
| **Stockout** | An item running out at a store. Today self-reported in WhatsApp, so under-reported (A-03) |
| **Emergency order / top-up** | A mid-week request when a store runs out. It is met by courier (~$85) or by borrowing from another store |
| **Borrowing** | A barista fetches stock from another store. Untracked today (H-13) |
| **Substitution** | A picker sends a different item when the ordered one is short (e.g. 12oz cups for 16oz). Unannounced today (H-11) |
| **Short-ship** | A supplier delivers less than was ordered to the warehouse (G-20, R-12) |
| **Re-keying** | Typing data again from one place into another. Here, store Excel → StockPro (H-03) |
| **What's-coming list** | A new dispatch notice sent to each store before delivery, showing items, quantities, substitutions and shortages (CH-08, FR-31) |
| **Delivery sign-off** | A new step: the shift lead checks the highlighted lines and signs for the delivery (CH-09, FR-34) |
| **Issues log** | A new shared log for stockouts, emergency requests, borrowings, discrepancies and substitutions (CH-10, R-01) |
| **Suggested order** | A proposed quantity per item worked out from par levels, stock on hand and sales (FR-19). Not live until R-06 |
| **Default order** | The order created automatically for a store that misses the 10:00 Monday cut-off (D-01, FR-11) |
| **PO** | Purchase order: the warehouse's order to a supplier |
| **Loaded staff cost** | Hourly wage plus on-costs. Store manager $38, coordinator $34, barista $29 (inputs/04) |
| **Recorded waste** | Stock written off by Finance: $182k in FY2025–26. ~$250k is Priya's estimate including unrecorded waste (D-05) |

### BA and method terms used
| Term | Definition |
|---|---|
| **As-is / to-be** | The current process and the proposed future process |
| **SIPOC** | Suppliers, Inputs, Process, Outputs, Customers: a one-page scope of a process |
| **Swimlane** | A process map with one lane per role, so handoffs show where the flow crosses lanes |
| **VA / BVA / NVA** | Value-adding (the customer would pay for it), business value-adding (needed by the business), non-value-adding (waste) |
| **DOWNTIME** | The 8 Lean wastes: Defects, Overproduction, Waiting, Non-utilised talent, Transportation, Inventory, Motion, Extra processing |
| **ECRS** | Eliminate, Combine, Rearrange, Simplify: the order in which to try improvements |
| **Touch time / wait time / cycle time** | Time actively working on a step / time waiting before it / total elapsed time from start to end |
| **Bottleneck** | The step that limits the whole process (here P-06, re-keying) |
| **5 Whys / fishbone** | Root-cause techniques: repeated "why?", and a cause diagram by category (Ishikawa) |
| **SWOT / TOWS** | Strengths, Weaknesses, Opportunities, Threats; TOWS pairs them into strategies (SO, ST, WO, WT) |
| **MoSCoW** | Must, Should, Could, Won't (this time): requirement priority |
| **BR / SR / FR / NFR** | Business, stakeholder, functional and non-functional requirements |
| **User story / AC / Given-When-Then** | "As a…, I want…, so that…" plus acceptance criteria written as testable scenarios |
| **INVEST** | Independent, Negotiable, Valuable, Estimable, Small, Testable: the checks for a good story |
| **RTM** | Requirements traceability matrix |
| **RACI** | Responsible, Accountable, Consulted, Informed |
| **Power/interest grid** | Mendelow's stakeholder grid: manage closely, keep satisfied, keep informed, monitor |
| **Quick win ⚡ / Big bet 🎯 / Fill-in 🧩 / Park ⛔** | Impact/effort categories in 03-gap |
| **Now / Next / Later** | Roadmap horizons: to mid-Feb 2027, mid-Feb to mid-May 2027, mid-May 2027 onwards |
| **Payback ceiling** | The largest one-off cost that pays back within 18 months: 1.5 × net annual cash benefit (05-exec-02, A-27) |
| **`--no-questions`** | The toolkit mode used here: built from files only, gaps marked `TBD`, questions listed but not asked |
| **🟢 / 🟠 / 🟡 / 🔴** | System-map health ratings: solid / too loose / can be improved / needs more work |

## 2. ID prefix key
| Prefix | Meaning | Range | Defined in |
|---|---|---|---|
| C- | System component | C-01–C-23 | [01-system-map](01-system-map.md) §1 |
| H- | Handoff / data flow | H-01–H-27 | [01-system-map](01-system-map.md) §3 |
| P- | As-is process step | P-01–P-17 | [02-process](02-process-store-replenishment.md) §3 |
| T- | To-be process step | T-01–T-16 | [02-process](02-process-store-replenishment.md) §6 |
| CH- | Process change | CH-01–CH-14 | [02-process](02-process-store-replenishment.md) §7 |
| D- | Decision | D-01–D-04 (process), D-05–D-13 (register) | [02-process](02-process-store-replenishment.md) §7; [06-analyst-05](06-analyst-05-assumptions-decisions-register.md) §2 |
| TS- | Target state | TS-1–TS-5 | [03-gap](03-gap.md) (target state) |
| G- | Gap | G-01–G-20 | [03-gap](03-gap.md) §1 |
| RC- | Root cause | RC-01–RC-07 | [03-gap](03-gap.md) §2 |
| R- | Recommendation | R-01–R-12 | [03-gap](03-gap.md) §5 |
| BR- | Business requirement | BR-01–BR-07 | [04-requirements](04-requirements.md) §1 |
| SR- | Stakeholder requirement | SR-01–SR-23 | [04-requirements](04-requirements.md) §2 |
| FR- | Functional requirement | FR-01–FR-59 | [04-requirements](04-requirements.md) §3 |
| NFR- | Non-functional requirement | NFR-01–NFR-28 | [04-requirements](04-requirements.md) §4 |
| US- | User story | US-01–US-35 | [04-requirements](04-requirements.md) §5 |
| A- | Assumption | A-01–A-38 | context.md (A-01–03); 03-gap (A-04–08); [06-analyst-05](06-analyst-05-assumptions-decisions-register.md) (A-09–38, plus the full list) |
| Q- | Open question | Q-01–Q-43 (consolidated) | [06-analyst-05](06-analyst-05-assumptions-decisions-register.md) §3. ⚠ Outputs 01–04 use **local** Q-numbers; see the mapping there |
| S- | Stakeholder (register row) | S1–S15 | [06-analyst-03](06-analyst-03-stakeholder-map.md) §1 |

**ID notes:**
- **SR-23** is listed out of numeric order in 04-requirements §2, after SR-03. It is not missing.
- **CH-11** (emergency borrow-vs-courier rule) has no matching R- in 03-gap. It is delivered alongside R-01 and R-02.
- **R-07** (pastry) has no CH-, because pastry ordering is outside the mapped process.
- **TS-** uses single digits (TS-1), unlike the other prefixes.

## 3. ID index
*C-, G-, RC-, R-, BR- in full, plus TS- and D-. For other prefixes, see §2.*

### C- System components ([01-system-map](01-system-map.md))
| ID | Title | Rating |
|---|---|---|
| C-01 | Store managers (×12) | 🟠 |
| C-02 | Paper stock sheet + clipboard | 🟡 |
| C-03 | Store Excel order files (×12) | 🟠 |
| C-04 | orders@ email inbox | 🟠 |
| C-05 | WhatsApp group + phone calls | 🟠 |
| C-06 | Mei's sticky notes / notepad | 🟠 |
| C-07 | Warehouse & Purchasing Coordinator (Mei Chen) | 🔴 |
| C-08 | StockPro | 🔴 |
| C-09 | Pickers (2) | 🟠 |
| C-10 | Driver + van (2 routes) | 🟢 |
| C-11 | Store shift leads / baristas | 🟠 |
| C-12 | Warehouse suppliers | 🟡 |
| C-13 | TillPoint POS | 🟡 |
| C-14 | LedgerOne | 🟢 |
| C-15 | Finance team | 🟡 |
| C-16 | Monthly stock report (Excel) | 🟡 |
| C-17 | Paper waste log | 🔴 |
| C-18 | Waste Google Sheet | 🟠 |
| C-19 | Valley Dairy (daily direct order) | 🟡 |
| C-20 | Crumb & Co. (standing pastry order) | 🔴 |
| C-21 | Stock rules: par levels and reorder points | 🔴 |
| C-22 | IT support (Josh + on-call contractor) | 🔴 |
| C-23 | Courier service | 🟡 |

### TS- Target state ([03-gap](03-gap.md))
| ID | Title |
|---|---|
| TS-1 | Fewer core-item stockouts (≤ 2.25/wk) |
| TS-2 | Less recorded waste (−10–20%) |
| TS-3 | Scale to 17+ stores with one coordinator; survives absence |
| TS-4 | Less manager ordering time (target TBD) |
| TS-5 | Accountability and a trusted baseline *(implied)* |

### G- Gaps ([03-gap](03-gap.md) §1)
| ID | Title | Dimension | Size |
|---|---|---|---|
| G-01 | Single point of failure; knowledge held by one person | People | H |
| G-02 | No standard manager routine or training | People | M |
| G-03 | No single order format or entry point | Process | H |
| G-04 | No rules for the four decision points | Process | H |
| G-05 | No advance notice; receipt check optional | Process | M |
| G-06 | Informal, untracked emergency path | Process | M |
| G-07 | Existing import unused; no data links | Technology | H |
| G-08 | No decided future for the warehouse system | Technology | H |
| G-09 | Manual invoice matching | Technology | L |
| G-10 | Decision data doesn't reach the ordering decision | Data | H |
| G-11 | Stale, undocumented stock rules | Data | H |
| G-12 | No store-level stock record | Data | M |
| G-13 | Ownership and accountability undefined | Policy & governance | H |
| G-14 | Rule ownership missing | Policy & governance | H |
| G-15 | Shared login, no audit trail | Policy & governance | M |
| G-16 | No reliable stockout measure | Measurement | H |
| G-17 | Incomplete waste data; disputed baseline | Measurement | H |
| G-18 | No KPI targets or review loop | Measurement | M |
| G-19 | Pastry order not linked to demand | Customers & partners | H |
| G-20 | No supplier short-ship tracking | Customers & partners | M |

### RC- Root causes ([03-gap](03-gap.md) §2)
| ID | Title | Confidence |
|---|---|---|
| RC-01 | Stock rules have no owner, method or review cycle | High |
| RC-02 | Demand and warehouse data never reach the ordering decision | High |
| RC-03 | No standard order format or procedure, so the import is unused | High |
| RC-04 | No end-to-end owner; exceptions have no rules; no stock accountability | High |
| RC-05 | Pastry standing order not owned or linked to sales | Medium |
| RC-06 | Stockouts, errors and waste not measured or reviewed | High |
| RC-07 | Coordinator knowledge undocumented; no backup | High |

### R- Recommendations ([03-gap](03-gap.md) §5)
| ID | Title | Category | Horizon |
|---|---|---|---|
| R-01 | Start measuring now: issues log + complete waste logs | ⚡ | Now |
| R-02 | Rules for exceptions: substitutions, what's-coming list, sign-off | ⚡ | Now → Next |
| R-03 | Remove the single point of failure: document, backup, logins | ⚡ | Now |
| R-04 | Capture orders once: standard template + StockPro import | ⚡ (if import works) | Next |
| R-05 | Give stock rules an owner; reset and review par levels | ⚡ | Next |
| R-06 | Put data in front of the decision: suggested quantities, warehouse stock | 🎯 | Next → Later |
| R-07 | Make pastry orders follow demand | ⚡ (if in scope) | Now |
| R-08 | Name an end-to-end owner; decide stock accountability | ⚡ | Now |
| R-09 | Agree a small KPI set, reviewed monthly | 🧩 | Next |
| R-10 | Decide the warehouse system's future | 🎯 | Later |
| R-11 | Electronic PO matching for invoices | ⛔ Park | Later |
| R-12 | Record supplier short-ships; review quarterly | 🧩 | Later / ongoing |

### BR- Business requirements ([04-requirements](04-requirements.md) §1)
| ID | Title |
|---|---|
| BR-01 | Keep core items in stock (≤ 2.25 stockouts/wk) |
| BR-02 | Cut stock waste (−10–20% vs $182k) |
| BR-03 | Scale to 17+ stores with one coordinator |
| BR-04 | Less manager time on ordering (target TBD) |
| BR-05 | Ordering continues when the coordinator is away |
| BR-06 | Accountability and one trusted set of measures |
| BR-07 | Supported warehouse system after Dec 2027 |

### D- Decisions ([02-process](02-process-store-replenishment.md) §7; [06-analyst-05](06-analyst-05-assumptions-decisions-register.md) §2)
| ID | Title | Status |
|---|---|---|
| D-01 | Late-order default | Pending |
| D-02 | Substitution rule and approver | Pending |
| D-03 | Owners of stock rules, issues log, pastry order (and E2E) | Pending |
| D-04 | Stock accountability at the store | Pending |
| D-05 | Waste baseline = $182k recorded | Proposed |
| D-06 | Park invoice matching | Proposed |
| D-07 | Dairy not in this release | Proposed |
| D-08 | No new core system before R-10 | Proposed |
| D-09 | R-10: decide now, spend later | Proposed |
| D-10 | Map weekly replenishment first | Done |
| D-11 | Business case options; Option 2 staged | Proposed |
| D-12 | `--no-questions` mode; outputs unvalidated | Done |
| D-13 | Consolidated Q-IDs supersede local ones | Done |

---

## Open questions
*(not asked — --no-questions)*
- **Q-06** Who owns TillPoint? The glossary entry says `TBD`.
- **Q-41** Who is the reader of this pack? If it is for a new BA, should the method glossary be expanded?
- Are there company terms we haven't heard yet (e.g. internal names for stores, routes or item codes)? This would be asked of Mei and Daniel during validation.

## Next steps
1. Add company jargon heard in the validation sessions.
2. When IDs are added or retired in any output, update §2 and §3 in the same change.
3. If outputs 01–04 are re-run, adopt the consolidated Q-IDs from 06-analyst-05 so the ⚠ in §2 can be removed.

## Technique notes
- **Shared vocabulary.** A shared vocabulary avoids the most common BA failure: two stakeholders agreeing on words while meaning different things. "Par level" vs "reorder point" is a live example here. One is a store target, the other a warehouse trigger, and both sit in C-21.
- **ID hygiene.** Stable, unique IDs make traceability possible. Colliding local numbers (the Q-IDs in outputs 01–04) are a common drift. Fix them in one register rather than renumbering every file.
