# Requirements: Stock ordering

- **Engagement:** Harbour Lane Coffee Co. — Stock ordering review (`samples/coffee-chain`)
- **Date:** 2026-11-12
- **Mode:** `--no-questions`. Built only from `context.md`, `inputs/` and existing outputs. The scope check in skill step 2 (in-scope area, roles, clarifying questions) was **not** done with the user. Missing facts are `TBD`. Every question I would have asked is under **Open questions**, tagged *(not asked — --no-questions)*.
- **Sources used:** `context.md`, `inputs/01-kickoff-meeting-notes.md`, `inputs/02-interview-store-manager.md`, `inputs/03-interview-warehouse-coordinator.md`, `inputs/04-interview-finance.md`, `inputs/05-ops-data-summary.md`, `outputs/01-system-map.md` (`C-`/`H-`), `outputs/02-process-store-replenishment.md` (`P-`/`T-`/`CH-`/`D-`), `outputs/03-gap.md` (`G-`/`RC-`/`R-`/`TS-`).
- **Sections:** all 8 (business, stakeholder, functional, non-functional, user stories, acceptance criteria, MoSCoW, traceability).
- **Open questions:** 20. The most important are the four owner and rule decisions (Q-01 to Q-03), whether the warehouse system's import and export can do what FR-14 and FR-20 need (Q-04), and whether pastries are in scope (Q-06).

**Scope used** (from context.md › Scope and `03-gap`, not confirmed):
- **In scope:** weekly store replenishment (store → warehouse → store), the mid-week emergency top-up, warehouse reorder points, and the measures needed for the business case.
- **Included but scope `TBD`:** pastry standing orders (R-07) and waste recording (R-01). They are the largest waste lever and the waste baseline, so they are written as Should, pending Q-06 and Q-07.
- **Out of scope:** replacing LedgerOne; invoice matching (R-11, parked); dairy ordering (scope `TBD`); choosing or buying a new warehouse system (R-10 is a separate decision).
- **Main user roles:** store managers, shift leads and baristas, the Warehouse & Purchasing Coordinator (Mei Chen), pickers, the Operations Director (Priya Nair), the Head of Finance (Tom Reyes). Two **new roles** come from earlier decisions: a *stock-rules owner* (D-03) and a *coordinator backup* (R-03). Who fills them is `TBD`.

**What "the solution" means here.** The earlier analysis recommends rules, owners, a standard template, a shared log and better use of the existing warehouse system and till data, not a new system (`02-process` › Business-first note). So "the solution shall…" covers the process, rules and tools together. Requirements say *what* is needed. Where a tool is named (the warehouse system's import, the till's daily export) it is because it already exists and is a stated constraint (budget, end of support).

---

## 1. Business requirements

| ID | Business requirement | Success metric | Source |
|---|---|---|---|
| BR-01 | The business needs to keep core items (e.g. oat milk, 16oz cups and lids, vanilla syrup, decaf beans) in stock in every store, so that customers don't walk out and emergency courier costs fall. | Core-item stockouts 4.5/wk reported (likely under-reported) → ≤ 2.25/wk before the new stores open (July 2027) | context.md › Goals (objective 1); inputs/01, 05; TS-1 |
| BR-02 | The business needs to cut stock waste, so that less money is written off. | Recorded waste ≈ $182k/yr → 10–20% lower (≈ $146k–$164k/yr) | context.md › Goals (objective 2); inputs/01, 04; TS-2 |
| BR-03 | The business needs an ordering process that works for 17+ stores with one coordinator, so that growth doesn't require another hire. | Coordinator headcount 1 → still 1 at 17 stores; order volume ~480 → ~680 lines/wk handled | context.md › Goals (objective 3); inputs/01, 03; TS-3 |
| BR-04 | The business needs store managers to spend less time on ordering paperwork, so that they spend more time on the floor. | Manager ordering time 2.5–3.5 h/wk per store → target `TBD` (Q-08) | context.md › Goals (objective 4); inputs/02, 05; TS-4 |
| BR-05 | The business needs ordering to keep running when the coordinator is away, so that no store goes without stock. | Aug 2026: two stores got nothing for a week → a named backup runs a full ordering week in a test | context.md › Goals › Other drivers; inputs/01, 03; TS-3 |
| BR-06 | The business needs clear accountability for stock at each stage and one trusted set of ordering measures, so that problems are owned and the business case rests on evidence. | "Nobody is accountable" → named owners for each stage; stockouts and waste logged at 12/12 stores | inputs/04; TS-5 [Assumption: implied by Tom's concerns, `03-gap` Q-01] |
| BR-07 | The business needs a supported warehouse stock system after Dec 2027 that copes with 17+ stores, so that ordering doesn't depend on unsupported software. | Supported system in place before Dec 2027 (decision by ~Sep 2027 [Assumption, `03-gap` R-10]) | context.md › Constraints; inputs/03; G-08 [derived from a constraint, not a stated goal] |

**Quality checks.**
- All four goals Priya stated map to a BR: objective 1 → BR-01, 2 → BR-02, 3 → BR-03 (and BR-05), 4 → BR-04.
- Each BR is an outcome, not a feature.
- BR-06 and BR-07 are not among Priya's four objectives. They come from Tom's concerns and the StockPro end of support. Both need confirming (Q-18).

---

## 2. Stakeholder requirements

| ID | Stakeholder | Need | Traces to | Source |
|---|---|---|---|---|
| SR-01 | Operations Director (Priya) | Needs to see core-item stockouts each week by store and item, against the halving target. | BR-01, BR-06 | inputs/01 |
| SR-02 | Operations Director (Priya) | Needs ordering to keep working when the coordinator is off. | BR-05 | inputs/01 |
| SR-03 | Operations Director (Priya) | Needs the 5 new stores to start on the standard ordering process from opening day. | BR-03 | inputs/01; `03-gap` SWOT (SO) |
| SR-23 | Operations Director (Priya) | Needs pastry orders to follow demand so fewer pastries are binned. | BR-02 | inputs/01, 02 |
| SR-04 | Head of Finance (Tom) | Needs one complete waste figure by store and category from all 12 stores. | BR-02, BR-06 | inputs/04 |
| SR-05 | Head of Finance (Tom) | Needs a named person accountable for stock at each stage (warehouse, in transit, store). | BR-06 | inputs/04 |
| SR-06 | Head of Finance (Tom) | Needs evidence, not estimates, of stockouts and lost sales before accepting them as benefits. | BR-01, BR-06 | inputs/04 |
| SR-07 | Head of Finance (Tom) | Needs the solution to fit ~$60k one-off, and to be used properly ("not another system nobody uses properly"). | All BRs (constraint) | inputs/01, 04 |
| SR-08 | CEO + 2 investors (board) | Need a business case with measured baselines and targets. | BR-06 | inputs/01 |
| SR-09 | Store managers | Need to count and order in one pass, without writing on paper and typing it again. | BR-04 | inputs/02 |
| SR-10 | Store managers | Need to see what was sold since the last order when deciding quantities. | BR-01, BR-02, BR-04 | inputs/02 ("If the till knows what we sold…") |
| SR-11 | Store managers | Need to see what the warehouse has available when ordering. | BR-01, BR-02 | inputs/02, 03 |
| SR-12 | Store managers | Need confirmation that their order has arrived. | BR-04 | inputs/02 ("text Mei and hope"); H-02 |
| SR-13 | Store managers | Need to know what is coming, including substitutions, before the delivery arrives. | BR-01 | inputs/02 |
| SR-14 | Store managers | Need a quick, reliable way to raise an emergency request and see what happens to it. | BR-01 | inputs/02, 03 |
| SR-15 | Coordinator (Mei) | Needs to load store orders without re-typing them. | BR-03 | inputs/03 |
| SR-16 | Coordinator (Mei) | Needs emergency requests in one place instead of calls, chat and sticky notes. | BR-03, BR-05 | inputs/03 |
| SR-17 | Coordinator (Mei) / backup | Needs a trained backup who can run her routines, including reorder points. | BR-05 | inputs/03 |
| SR-18 | Pickers | Need a clear rule for what may be substituted and who approves anything else. | BR-01 | inputs/03 |
| SR-19 | Shift leads / baristas | Need a delivery check that can be done on a busy shift. | BR-01, BR-06 | inputs/02 ("if they're not slammed") |
| SR-20 | IT (Josh + contractor) | Needs anything set up to be supportable by one generalist and an on-call contractor. | BR-03, BR-07 | inputs/01 |
| SR-21 | Accounts assistant | Needs less manual invoice matching (~2 days/month). | — (parked: R-11) | inputs/04 |
| SR-22 | Customers (indirect) | Need core items available when they order. | BR-01 | inputs/02 ("customers walk out") |

*Groups with no SR:* driver (no need raised; van capacity at 17 stores is an open question, Q-16); suppliers incl. Crumb & Co. and the StockPro vendor (needs not gathered; R-07 and R-10 will need conversations with them).

**Conflicting needs** (all listed under Open questions, Q-18):
- **"Just in case" stock vs waste.** Managers over-order on items that ran out before (SR-11). That protects BR-01 but works against BR-02 and leaves the warehouse short. Visible warehouse stock and current par levels are meant to resolve this. It needs agreement on who may override a suggested quantity.
- **Busy shifts vs accountability.** Shift leads check deliveries only when not busy (SR-19), while Tom needs signed-for stock (SR-05). FR-33 limits the check to flagged and core lines. The time allowed is `TBD` (NFR-18).
- **Which waste number.** Priya ≈ $250k, Tom stands behind $182k. BR-02 uses $182k until FR-45 data shows otherwise.
- **Lost sales.** Priya thinks they are "big"; Tom wants evidence (SR-06). FR-51 is a Could until agreed.
- **Reported stockouts will rise at first.** The new log (FR-37) ends under-reporting, so the BR-01 baseline will move up. Agree this with Priya and Tom before go-live.

---

## 3. Functional requirements

Priorities are explained in §7. "Source" names the earlier change (`CH-`) or recommendation (`R-`) where one exists.

### 3.1 Order capture (standard template)
| ID | Requirement | Traces to | Priority | Source |
|---|---|---|---|---|
| FR-01 | The solution shall provide one order template that every store uses, with the same layout and item list. | BR-03, BR-04, SR-09, SR-15 | Must | CH-01, R-04; inputs/02, 03 |
| FR-02 | The template shall identify each item by the same item code used in the warehouse system. | BR-03, SR-15 | Must | CH-01, R-04 |
| FR-03 | The template shall reject an item code that is not on the current item list. | BR-03 | Must | CH-01; inputs/05 (31 order errors) |
| FR-04 | The template shall flag any order line whose quantity is more than `TBD`× the store's par level for that item (Q-09). | BR-01, BR-02 | Must | CH-01; inputs/03 ("100 lids instead of 10") |
| FR-05 | The template shall let a manager enter stock counts directly, without a separate paper count sheet. | BR-04, SR-09 | Should | CH-03 (phase 1); inputs/02 |
| FR-06 | The solution shall store each count with store, item, quantity on hand and count date. | BR-04, BR-01 | Should | CH-03; G-12 |
| FR-07 | The solution shall support a weekly count of core and fast-moving items only, with a full count at a frequency set by the stock-rules owner. | BR-04 | Could | CH-03 (phase 2) |
| FR-08 | The solution shall allow a new store to be added to the template and the import by setting it up, without creating a new layout. | BR-03, SR-03 | Must | context.md › Company (17 stores by July 2027) |

### 3.2 Order submission
| ID | Requirement | Traces to | Priority | Source |
|---|---|---|---|---|
| FR-09 | The solution shall record the date and time each store order is submitted. | BR-03 | Must | CH-06; inputs/05 (2.4 late/wk) |
| FR-10 | The solution shall send the store manager a confirmation when their order is received. | BR-04, SR-12 | Must | CH-06; H-02 |
| FR-11 | **Business rule.** If a store has not submitted its order by 10:00 Monday, the solution shall create that store's order from the default agreed in D-01 (suggested order, or last week's order until suggestions are live). | BR-03, BR-05, SR-15 | Must | CH-06, D-01 |
| FR-12 | The solution shall notify the store manager and the coordinator when a default order has been created for a store. | BR-03 | Must | CH-06 |
| FR-13 | The solution shall keep one active order per store per weekly cycle; a resubmission before the cut-off replaces the earlier one. | BR-03 | Should | [Assumption: avoids duplicate orders once orders are imported] |

### 3.3 Order import
| ID | Requirement | Traces to | Priority | Source |
|---|---|---|---|---|
| FR-14 | The solution shall load all submitted store orders into the warehouse system without anyone re-typing them. | BR-03, BR-05, SR-15 | Must | CH-02, R-04; inputs/03 (import "nobody has set up") |
| FR-15 | The solution shall produce an exception list after each load, showing every rejected or flagged line with store, item and reason. | BR-03 | Must | CH-02; T-06 |
| FR-16 | The solution shall show which stores' orders have been loaded for the current cycle and which are missing. | BR-05 | Should | T-06; inputs/03 (August failure) |

### 3.4 Demand and stock data at the point of ordering
| ID | Requirement | Traces to | Priority | Source |
|---|---|---|---|---|
| FR-17 | The solution shall show, for each item, the quantity used since the store's last order, worked out from till sales. | BR-01, BR-04, SR-10 | Should | CH-04, R-06; H-23 |
| FR-18 | The solution shall hold a conversion from each relevant till product to stock-item usage (e.g. oat milk per drink), with a named owner. | BR-01 | Should | CH-04; `03-gap` Q-09 |
| FR-19 | **Business rule.** The solution shall calculate a suggested order quantity per item as par level minus counted stock on hand, rounded up to a whole pack, and never below zero. [Assumption: rule to confirm with the stock-rules owner, Q-17] | BR-01, BR-04 | Should | CH-04; T-02 |
| FR-20 | The solution shall show warehouse available stock for each item, with the date and time the figure was taken, while a manager is ordering. | BR-01, BR-02, SR-11 | Should | CH-05, R-06; H-24 |
| FR-21 | The solution shall flag to the coordinator any item where the total ordered by all stores exceeds warehouse available stock. | BR-01 | Could | inputs/03 (warehouse runs out) [Assumption] |

### 3.5 Stock rules (par levels and reorder points)
| ID | Requirement | Traces to | Priority | Source |
|---|---|---|---|---|
| FR-22 | The solution shall hold a par level for each item at each store, with its owner and last-reviewed date. | BR-01, BR-02, SR-01 | Must | CH-12, R-05; inputs/02 (stale since 2024) |
| FR-23 | The solution shall calculate proposed par levels from at least the last 12 weeks of usage (sales or orders) for the stock-rules owner to approve. | BR-01, BR-02 | Must | R-05 |
| FR-24 | The solution shall allow only the stock-rules owner, or their named delegate, to change a par level, and shall record the old value, new value, who and when. | BR-06 | Must | CH-12, D-03 |
| FR-25 | The solution shall flag any par level not reviewed in the last 31 days. | BR-01 | Should | CH-12 (monthly review) |
| FR-26 | The solution shall hold each warehouse reorder point with its reason, owner and last-reviewed date. | BR-05, SR-17 | Must | R-03; H-15; inputs/03 ("from experience") |

### 3.6 Picking and substitutions
| ID | Requirement | Traces to | Priority | Source |
|---|---|---|---|---|
| FR-27 | The solution shall hold a list of approved substitutes for each item. | BR-01, SR-18 | Must | CH-07, R-02, D-02 |
| FR-28 | **Business rule.** A picker shall send a substitute only if it is on the approved list; any other substitution needs approval from the named approver (D-02) before dispatch. | BR-01, SR-18 | Must | CH-07, D-02; inputs/03 |
| FR-29 | The solution shall record every substitution and every short-picked line: item ordered, item sent, quantities, reason and approver. | BR-01, BR-06 | Must | CH-07, R-02; inputs/05 (11 unannounced in 12 wks) |
| FR-30 | The solution shall record supplier short-shipments at goods receipt, by supplier and item. | BR-01 | Should | R-12; G-20 |

### 3.7 Dispatch notice and delivery receipt
| ID | Requirement | Traces to | Priority | Source |
|---|---|---|---|---|
| FR-31 | The solution shall produce a "what's coming" list for each store from the packed order, showing items, quantities, substitutions and shortages. | BR-01, SR-13 | Must | CH-08, R-02; inputs/02 (Daniel's request) |
| FR-32 | The solution shall send the what's-coming list to the store before the delivery arrives (lead time: NFR-06). | BR-01, SR-13 | Must | CH-08 |
| FR-33 | The what's-coming list shall highlight core items, substitutions and shortages as the lines to check. | BR-06, SR-19 | Should | CH-09 |
| FR-34 | The solution shall let a shift lead sign off a delivery, recording their name and the date and time. | BR-06, SR-05 | Must | CH-09, D-04; inputs/04 |
| FR-35 | The solution shall let the shift lead record each discrepancy at sign-off as missing, wrong item, wrong quantity or damaged. | BR-06, BR-01 | Must | CH-09, CH-10 |
| FR-36 | The solution shall alert the store manager if a delivery has not been signed off within `TBD` hours of arrival (Q-10). | BR-06 | Could | CH-09 [Assumption] |

### 3.8 Issues log and emergency top-ups
| ID | Requirement | Traces to | Priority | Source |
|---|---|---|---|---|
| FR-37 | The solution shall provide one shared issues log for stockouts, emergency requests, borrowings, delivery discrepancies and substitutions. | BR-01, BR-06, SR-01, SR-16 | Must | CH-10, R-01 |
| FR-38 | Each issue shall record store, item, quantity, date and time, issue type, reason and who logged it; an issue without store, item, type or date shall not be saved. | BR-06 | Must | CH-10 |
| FR-39 | The solution shall give each emergency request a status (open, fulfilled by borrowing, fulfilled by courier, cancelled) and record the date and time of each change. | BR-01, BR-05, SR-14, SR-16 | Must | CH-10, CH-11; inputs/03 (sticky notes) |
| FR-40 | **Business rule.** The solution shall apply the agreed borrow-vs-courier rule to each emergency request and record which route was used and why. | BR-01 | Should | CH-11; inputs/04 (~$19k/yr couriers) |
| FR-41 | The solution shall record each borrowing with the lending store, receiving store, item and quantity. | BR-06 | Should | CH-10, CH-11; H-13 |
| FR-42 | The solution shall show all open emergency requests to the coordinator and the named backup. | BR-05, SR-16, SR-17 | Must | CH-10, CH-14 |
| FR-43 | An emergency order fulfilled from the warehouse shall be entered in the warehouse system on the same working day. | BR-06 | Should | CH-11; H-06 |

### 3.9 Waste and pastry orders (scope `TBD`, Q-06, Q-07)
| ID | Requirement | Traces to | Priority | Source |
|---|---|---|---|---|
| FR-44 | The solution shall record waste per store by item, quantity, value and reason (expired, over-supplied, damaged, other). | BR-02, SR-04 | Should | R-01; G-17 |
| FR-45 | The solution shall flag each store that has not submitted waste records for a month by the `TBD` day of the following month. | BR-02, BR-06, SR-04 | Must | R-01; inputs/04 ("maybe 8 of 12") |
| FR-46 | The solution shall report pastry sales by store and weekday against the standing pastry order for the same period. | BR-02, SR-23 | Should | R-07; G-19 |
| FR-47 | The solution shall record each store's standing pastry order with its owner and last-reviewed date, and flag it if not reviewed in the last month. | BR-02, SR-23 | Should | R-07; G-14 |

### 3.10 Reporting and KPIs
| ID | Requirement | Traces to | Priority | Source |
|---|---|---|---|---|
| FR-48 | The solution shall report core-item stockouts per week by store and item, from the issues log. | BR-01, BR-06, SR-01, SR-06 | Must | R-01, R-09 |
| FR-49 | The solution shall produce a monthly KPI report against target for: stockouts per week, recorded waste ($), order errors, courier deliveries, late orders, unannounced substitutions and manager ordering time. | BR-06, SR-08 | Must | R-09; G-18 |
| FR-50 | The solution shall record how long each store manager spends on the weekly order (from first count entry to submission). | BR-04 | Should | TS-4; Q-08 |
| FR-51 | The solution shall estimate lost sales on stockout days by comparing the item's sales with its usual sales for that store and weekday. | BR-06, SR-06 | Could | context.md › Open question #4 |
| FR-52 | The solution shall produce the monthly warehouse stock-position report without manual re-keying, by someone other than the coordinator. | BR-05 | Could | C-16, H-19 |

### 3.11 Access, ownership and continuity
| ID | Requirement | Traces to | Priority | Source |
|---|---|---|---|---|
| FR-53 | The solution shall give every person who loads, enters or changes orders in the warehouse system their own login. | BR-06, SR-05 | Must | CH-13, R-03; inputs/03 (one shared login) |
| FR-54 | The solution shall record who created or changed each order line, and when. | BR-06 | Must | CH-13 |
| FR-55 | The solution shall record a named owner for: end-to-end replenishment, stock rules, the issues log, the substitution list, the pastry standing order and stock at each stage (warehouse, in transit, store). | BR-06, SR-05 | Must | R-08, D-03, D-04 |
| FR-56 | The solution shall include written procedures for the weekly order load, emergency requests, substitutions and reorder points, kept where the backup can reach them. | BR-05, SR-02, SR-17 | Must | CH-14, R-03 |

### 3.12 Not in this release (recorded so they aren't lost)
| ID | Requirement | Traces to | Priority | Source |
|---|---|---|---|---|
| FR-57 | The solution shall match supplier invoices in LedgerOne against electronic purchase orders. | SR-21 (no BR) | Won't | R-11 (parked until R-10) |
| FR-58 | The solution shall support daily dairy ordering with Valley Dairy. | — (no BR) | Won't | Scope `TBD`; no problems reported (C-19) |
| FR-59 | The solution shall replace or upgrade the warehouse stock system. | BR-07 | Won't (this release) | R-10: decide by ~Sep 2027, likely outside the $60k |

**Quality checks.**
- Each FR is one behaviour and traces to a BR or SR. FR-57 and FR-58 have no BR and are Won't (see Orphans).
- Vague words were moved to NFRs with numbers or `TBD` (e.g. "before delivery" → NFR-06).
- **Every `CH-` has an FR:** CH-01 → FR-01–04 · CH-02 → FR-14, 15 · CH-03 → FR-05, 07 · CH-04 → FR-17–19 · CH-05 → FR-20 · CH-06 → FR-09–12 · CH-07 → FR-27–29 · CH-08 → FR-31, 32 · CH-09 → FR-33–35 · CH-10 → FR-37, 38 · CH-11 → FR-40, 43 · CH-12 → FR-22, 24, 25 · CH-13 → FR-53, 54 · CH-14 → FR-56.
- **Every Now/Next `R-` has a requirement:** R-01 → FR-37, 45, 48 · R-02 → FR-27–35 · R-03 → FR-26, 53, 56, NFR-10 · R-04 → FR-01, 14 · R-05 → FR-22–25 · R-06 → FR-17–20 · R-07 → FR-46, 47 · R-08 → FR-55 · R-09 → FR-49 · R-10 (vendor path requested Now) → BR-07, NFR-24, NFR-28. Later: R-11 → FR-57 (Won't), R-12 → FR-30.
- **Every pain point is covered:** #1 BR-01 · #2 FR-14 · #3 FR-03, 14 · #4 BR-02 · #5 FR-05, 19 · #6 FR-39, 40 · #7 FR-27–31 · #8 FR-20 · #9 FR-56, NFR-10 · #10 FR-11 · #11 FR-34 · #12 FR-01, 22.

---

## 4. Non-functional requirements

| ID | Category | Requirement | Measure | Traces to | Source |
|---|---|---|---|---|---|
| NFR-01 | Performance (effort) | Coordinator time to load all weekly store orders | ≤ 1 h/wk in total at 17 stores (~680 lines) [Assumption: R-04 target] | BR-03 | `03-gap` R-04 |
| NFR-02 | Performance (effort) | Coordinator review of flagged lines after a load | ≤ 5 min per store [Assumption: test in the 2-store pilot] | BR-03 | `02-process` §5 |
| NFR-03 | Performance (data freshness) | Sales-based usage shown at ordering time | No older than the previous trading day | BR-01 | inputs/04 (daily till export) |
| NFR-04 | Performance (data freshness) | Warehouse available stock shown at ordering time | No older than `TBD` h (depends on what the warehouse system can export, Q-04) | BR-01, BR-02 | CH-05 |
| NFR-05 | Performance | Order receipt confirmation (FR-10) | Within `TBD` min of submission (Q-10) | BR-04 | CH-06 |
| NFR-06 | Performance | What's-coming list (FR-32) reaches the store | At least `TBD` h before the delivery (Q-10) | BR-01 | CH-08 |
| NFR-07 | Scalability | Volume handled without a second coordinator | At least 17 stores and ~680 lines/wk by July 2027; growth beyond 17: `TBD` (Q-16) | BR-03 | inputs/01; `02-process` §1 |
| NFR-08 | Scalability | Setting up a new store (FR-08) | ≤ `TBD` working days, without IT development (Q-16) | BR-03 | SR-03 |
| NFR-09 | Availability | Order template, submission and issues log available | Sunday after close → Monday 10:00, and all store trading hours; uptime target `TBD` (Q-12) | BR-03, BR-04 | inputs/02 |
| NFR-10 | Reliability (continuity) | A named backup can run the weekly cycle without the coordinator | Backup completes one full week (load, emergencies, substitutions) unaided in a test before 1 Jul 2027 | BR-05 | R-03; inputs/03 |
| NFR-11 | Reliability (recovery) | If the order load fails, a written fallback lets every order be processed in time | All orders loaded before pick lists are due on Tuesday | BR-05 | [Assumption] |
| NFR-12 | Security | No shared logins in the warehouse system | Shared logins 1 → 0 | BR-06 | CH-13; inputs/03, 04 |
| NFR-13 | Security | Access removed when someone leaves | Within `TBD` of leaving (Q-13) | BR-06 | system map Q-04 |
| NFR-14 | Security and privacy | Ordering and issue data held in a business-controlled location, not only in personal chat apps | 100% of emergency requests and stockouts recorded in the issues log after go-live | BR-06 | C-05; system map Q-04 |
| NFR-15 | Compliance and audit | Change history for orders and par levels kept | ≥ `TBD` months (Q-13) | BR-06 | FR-24, FR-54 |
| NFR-16 | Compliance | Expiry or food-safety traceability for stock | `TBD`: depends on rules not yet known (Q-14) | BR-02 | context.md › Constraints |
| NFR-17 | Usability | Store managers can use the template after a short briefing | ≤ 1 h of training per manager [Assumption: CH-01] | BR-04 | CH-01 |
| NFR-18 | Usability | Delivery check of highlighted lines and sign-off | ≤ `TBD` min per delivery on a busy shift (Q-10) | BR-06 | inputs/02 |
| NFR-19 | Usability | Logging an issue (FR-37) | ≤ `TBD` min per entry from a store device (Q-10) | BR-06 | R-01 |
| NFR-20 | Usability (devices) | Template and issues log work on the existing store laptop; use on a tablet or phone on the floor `TBD` | Works on the store laptop at 12/12 stores; other devices per Q-11 | BR-04 | `02-process` Q-15 |
| NFR-21 | Usability (adoption) | Stores actually use the new routine | 12/12 stores submit via the template for 4 weeks in a row after rollout; 12/12 log waste and stockouts | BR-06 (and Tom's failure condition) | inputs/04; R-01 KPI |
| NFR-22 | Compatibility | LedgerOne is not changed | No changes to LedgerOne set-up or data | All BRs (constraint) | inputs/01 |
| NFR-23 | Compatibility | Use what already exists before adding systems | Uses the till's daily export and the warehouse system's existing import/export; no new core system before the R-10 decision | BR-07 | context.md › Constraints; `02-process` §6 |
| NFR-24 | Compatibility (portability) | Order, issue and stock-rule data can move to a future warehouse system | Exportable in a documented, system-independent file format | BR-07 | `03-gap` SWOT (ST), R-10 |
| NFR-25 | Supportability | Supportable by the in-house IT generalist and the on-call contractor | Written runbook exists; IT effort ≤ `TBD` h/month (Q-15) | BR-03 | inputs/01 |
| NFR-26 | Cost (constraint) | Budget | One-off ≤ $60k by 30 Jun 2027; ongoing costs pay back in < 18 months | All BRs (constraint) | inputs/01, 04 |
| NFR-27 | Delivery window (constraint) | Timing of changes | No go-live 1 Dec 2026 – 31 Jan 2027 except logging and rules; live at all 12 stores before the new stores open (July 2027) | BR-01, BR-03 | inputs/01; A-05 |
| NFR-28 | Supportability (lifecycle) | Warehouse stock system supported after Dec 2027 | Supported version or replacement live before Dec 2027 | BR-07 | inputs/03 |

**Categories:**
- Covered: performance, availability and reliability, security and privacy, usability, scalability, compliance and audit, compatibility, supportability, plus cost and timing constraints.
- **Skipped:** accessibility (WCAG). No evidence of a need in the sources. Raised as Q-19 rather than assumed.

**Quality checks.**
- Every NFR has a number or a checkable condition.
- 11 measures are `TBD`. Each has an open question (Q-04, Q-10 to Q-16) rather than a guessed figure.
- The figures marked [Assumption] (NFR-01, 02, 11, 17) come from earlier outputs and need confirming in the pilot.

---

## 5. User stories

Roles come from context.md › Stakeholders. "Stock-rules owner" and "coordinator backup" are new roles from D-03 and R-03; who fills them is `TBD` (Q-03, Q-20).

### Epic: Order capture and submission
| ID | User story | Traces to | Priority | Notes |
|---|---|---|---|---|
| US-01 | As a store manager, I want one order template with the same item list as every other store, so that the warehouse can load my order without re-typing it. | FR-01, FR-02 | Must | |
| US-02 | As a store manager, I want the template to stop me entering an item code that doesn't exist, so that the warehouse doesn't pick the wrong item. | FR-03 | Must | |
| US-03 | As a store manager, I want lines far above par flagged before I submit, so that a typo like 100 instead of 10 is caught before it ships. | FR-04 | Must | Threshold Q-09 |
| US-04 | As a store manager, I want to enter counts straight into the template while I walk the store, so that I don't count on paper and then type it all again. | FR-05, FR-06 | Should | Device Q-11 |
| US-05 | As a store manager, I want a confirmation when my order is received, so that I don't have to chase Mei. | FR-09, FR-10 | Must | |
| US-06 | As the coordinator, I want a store that misses the 10:00 Monday cut-off to get its default order automatically, so that Monday stays on schedule and no store goes without. | FR-11, FR-12 | Must | Needs D-01 |
| US-07 | As a store manager, I want to resubmit my order before the cut-off and have it replace the first one, so that I can fix a mistake without a duplicate order. | FR-13 | Should | |
| US-08 | As the Operations Director, I want a new store set up on the standard template without a new layout, so that stores 13–17 start on the standard process from day one. | FR-08 | Must | |

### Epic: Order import
| ID | User story | Traces to | Priority | Notes |
|---|---|---|---|---|
| US-09 | As the coordinator, I want to load all store orders into the warehouse system in one go, so that I stop spending 6–8 hours every Monday re-typing them. | FR-14 | Must | Gated by Q-04 |
| US-10 | As the coordinator, I want a list of rejected and flagged lines after each load, so that I only deal with the exceptions. | FR-15 | Must | |
| US-11 | As the coordinator backup, I want to see which stores' orders are loaded this cycle and which are missing, so that no store is missed when Mei is away. | FR-16 | Should | |

### Epic: Demand and stock data at the point of ordering
| ID | User story | Traces to | Priority | Notes |
|---|---|---|---|---|
| US-12 | As a store manager, I want to see how much of each item we used since the last order, so that I order from real demand rather than a guess. | FR-17, FR-18 | Should | Gated by Q-05 |
| US-13 | As a store manager, I want a suggested quantity for each item, so that I start from a sensible order and finish faster. | FR-19 | Should | Rule Q-17 |
| US-14 | As a store manager, I want to see what the warehouse has available, so that I don't over-order "just in case". | FR-20 | Should | Gated by Q-04 |

### Epic: Stock rules
| ID | User story | Traces to | Priority | Notes |
|---|---|---|---|---|
| US-15 | As the stock-rules owner, I want proposed par levels worked out from the last 12 weeks of usage, so that I can replace the 2024 levels quickly and with evidence. | FR-22, FR-23 | Must | |
| US-16 | As the stock-rules owner, I want only approved people to change par levels, with every change recorded, so that the rules stay trusted. | FR-24 | Must | |
| US-17 | As the stock-rules owner, I want par levels that are overdue for their monthly review flagged, so that they don't go stale again. | FR-25 | Should | |
| US-18 | As the coordinator backup, I want each reorder point recorded with the reason behind it, so that I can run warehouse purchasing when Mei is away. | FR-26 | Must | |

### Epic: Substitutions and deliveries
| ID | User story | Traces to | Priority | Notes |
|---|---|---|---|---|
| US-19 | As a picker, I want a list of approved substitutes for each item, so that I know what I can send without asking and when I must ask. | FR-27, FR-28 | Must | Needs D-02 |
| US-20 | As the coordinator, I want every substitution, short-picked line and supplier short-ship recorded, so that stores are told and short-ships can be raised with suppliers. | FR-29, FR-30 | Must | |
| US-21 | As a store manager, I want a what's-coming list before the van arrives, including substitutions and shortages, so that I can act before we run out. | FR-31, FR-32 | Must | |
| US-22 | As a shift lead, I want the list to highlight the lines I must check, so that I can check a delivery even on a busy shift. | FR-33 | Should | |
| US-23 | As a shift lead, I want to sign off a delivery and record any discrepancy, so that problems are caught on the day and someone is accountable for the stock. | FR-34, FR-35 | Must | Needs D-04 |

### Epic: Issues and emergency top-ups
| ID | User story | Traces to | Priority | Notes |
|---|---|---|---|---|
| US-24 | As a store manager, I want to log a stockout or emergency request in one shared place, so that it is acted on even if Mei is away and it counts in the stockout figures. | FR-37, FR-38, FR-42 | Must | |
| US-25 | As the coordinator, I want each emergency request to show its status, so that nothing is left on a sticky note. | FR-39 | Must | |
| US-26 | As the coordinator, I want the borrow-vs-courier rule applied and recorded, so that we only pay ~$85 for a courier when borrowing won't do. | FR-40, FR-43 | Should | Rule agreed by Priya + Mei |
| US-27 | As a store manager, I want stock borrowed between stores recorded, so that both stores' stock and waste figures stay right. | FR-41 | Should | |

### Epic: Waste and pastry orders
| ID | User story | Traces to | Priority | Notes |
|---|---|---|---|---|
| US-28 | As the Head of Finance, I want stores with missing waste records flagged each month, so that the waste figure covers all 12 stores. | FR-45 | Must | Scope Q-07 |
| US-29 | As the Head of Finance, I want waste recorded by item, value and reason, so that we can see where the money is lost. | FR-44 | Should | Scope Q-07 |
| US-30 | As the pastry-order owner, I want pastry sales by weekday compared with the standing order, so that I can cut quantities that end up binned. | FR-46, FR-47 | Should | Scope Q-06; owner Q-03 |

### Epic: Reporting
| ID | User story | Traces to | Priority | Notes |
|---|---|---|---|---|
| US-31 | As the Operations Director, I want weekly core-item stockouts by store and item, so that I can track progress toward halving them. | FR-48 | Must | |
| US-32 | As the Head of Finance, I want a monthly KPI report against targets, including manager ordering time, so that the board sees evidence rather than estimates. | FR-49, FR-50 | Must | |

### Epic: Access, ownership and continuity
| ID | User story | Traces to | Priority | Notes |
|---|---|---|---|---|
| US-33 | As the Head of Finance, I want every warehouse user to have their own login with changes recorded, so that we can see who changed an order. | FR-53, FR-54 | Must | Licence cost `TBD` |
| US-34 | As the Operations Director, I want a named owner recorded for each part of ordering and for stock at each stage, so that someone is accountable when stock goes missing. | FR-55 | Must | Needs D-03, D-04 |
| US-35 | As the coordinator backup, I want written procedures for the weekly routines, so that I can run a full week without Mei. | FR-56 | Must | |

**Quality checks.**
- **Every Must and Should FR has a story.** The Could FRs (FR-07, 21, 36, 51, 52) and the Won't FRs have none, by design.
- **INVEST:**
  - US-20 bundles substitutions and supplier short-ships. It is kept as one story because both are recorded in the same place. Split it if the team estimates it as large.
  - US-12 depends on the till-to-item conversion (Q-05). It is not Independent until that is answered.

---

## 6. Acceptance criteria

At least one happy path and one exception for every Must story. Values come from context.md where known.

#### US-01 — One standard template
- **AC1** Given the template is live, When any of the 12 stores opens it, Then it shows the same layout and item list, with warehouse item codes.
- **AC2 (exception)** Given a manager has added a column or changed the layout, When the order is loaded, Then the load rejects the file and tells the manager and coordinator why.

#### US-02 — Invalid item codes blocked
- **AC1** Given an item code on the current item list, When the manager enters a quantity, Then the line is accepted.
- **AC2 (exception)** Given an item code not on the list, When the manager tries to enter or submit it, Then the line is rejected with the message "unknown item code" and the order can't be submitted until it is fixed or removed.

#### US-03 — Over-par lines flagged
- **AC1** Given a par level of 10 for 16oz lids, When the manager orders 8, Then the line is not flagged.
- **AC2 (exception)** Given a par level of 10 for 16oz lids and a threshold of `TBD`× (Q-09), When the manager enters 100, Then the line is flagged and the manager must confirm or correct it before submitting.
- **AC3 (exception)** Given an item has no par level yet, When the manager enters any quantity, Then the line is flagged "no par level" for the coordinator to review.

#### US-05 — Order receipt confirmation
- **AC1** Given a manager submits at 09:20 Monday, When the order is received, Then the manager gets a confirmation showing store, date and time, and number of lines, within `TBD` min (NFR-05).
- **AC2 (exception)** Given submission fails, When the manager submits, Then no confirmation is sent and the manager sees an error telling them the order was not received.

#### US-06 — Late-order default
- **AC1** Given Docklands has not submitted by 10:00 Monday, When the cut-off passes, Then a default order is created for Docklands as agreed in D-01, and the store manager and coordinator are both notified.
- **AC2 (exception)** Given a store submitted at 09:59, When the cut-off passes, Then no default order is created.
- **AC3 (exception)** Given a default order was created, When the manager submits their own order at 10:30, Then the coordinator is alerted and decides which order stands (rule `TBD` in D-01).

#### US-08 — New store set-up
- **AC1** Given store 13 is set up with its item list and par levels, When its manager opens the template, Then it has the same layout as the other stores and its orders load with no layout changes.
- **AC2 (exception)** Given store 13 has no par levels yet, When its first order is entered, Then every line is flagged "no par level" until the stock-rules owner sets them.

#### US-09 — Load orders without re-typing
- **AC1** Given all 12 stores have submitted, When the coordinator loads the orders, Then every valid line appears in the warehouse system with the same store, item and quantity as submitted, and no line was typed by hand.
- **AC2 (exception)** Given one file can't be read, When the load runs, Then the other 11 orders still load and the unreadable file is reported by store name.

#### US-10 — Exception list after load
- **AC1** Given a load with 480 lines of which 3 are rejected, When the load finishes, Then the exception list shows those 3 lines with store, item and reason.
- **AC2 (exception)** Given a load with no rejected or flagged lines, When it finishes, Then the exception list says "0 exceptions".

#### US-15 — Proposed par levels
- **AC1** Given at least 12 weeks of usage for oat milk at a store, When the owner asks for proposed par levels, Then a proposed level is shown next to the current one with the weeks of data used.
- **AC2 (exception)** Given fewer than 12 weeks of usage (e.g. a new store), When proposals are produced, Then the item is marked "not enough history" and no proposed level is given.
- **AC3** Given the owner approves a proposal, When it is saved, Then the par level, owner and last-reviewed date are updated.

#### US-16 — Controlled par-level changes
- **AC1** Given the stock-rules owner changes oat milk par at Docklands from 24 to 30, When it is saved, Then the change history shows 24 → 30, who and when.
- **AC2 (exception)** Given a store manager who is not a named delegate, When they try to change a par level, Then the change is refused.

#### US-18 — Reorder points with reasons
- **AC1** Given a reorder point for 16oz cups, When the backup opens it, Then they see the level, the reason, the owner and the last-reviewed date.
- **AC2 (exception)** Given a reorder point with no reason recorded, When the monthly review runs, Then it is listed as "reason missing" for the owner.

#### US-19 — Approved substitutes
- **AC1** Given 16oz cups are short and the approved list has none for 16oz cups, When a picker wants to send 12oz cups, Then the picker must get approval from the named approver before dispatch.
- **AC2** Given an item is short and an approved substitute exists, When the picker sends it, Then it is recorded as a substitution with no further approval.
- **AC3 (exception)** Given the approver can't be reached before dispatch, When the van is due to leave, Then the line is sent short (no substitute) and shown as a shortage on the what's-coming list.

#### US-20 — Substitutions and short-ships recorded
- **AC1** Given a picker sends an approved substitute, When packing is finished, Then a record shows item ordered, item sent, quantities, reason and approver.
- **AC2** Given a supplier delivers 20 cases instead of 30 on Friday, When goods are received, Then a short-ship of 10 cases is recorded against that supplier and item.
- **AC3 (exception)** Given a substitution was made without a record, When the delivery is signed off with a "wrong item" discrepancy, Then it appears in the monthly count of unannounced substitutions.

#### US-21 — What's-coming list
- **AC1** Given a store's order is packed on Tuesday, When packing is finished, Then the store gets a list of items and quantities, with substitutions and shortages marked, at least `TBD` h before delivery (NFR-06).
- **AC2 (exception)** Given nothing was substituted or short, When the list is sent, Then it says "no substitutions or shortages".
- **AC3 (exception)** Given a line is short with no substitute, When the list is sent, Then the line shows "0 sent — short" so the store can raise an emergency request.

#### US-23 — Delivery sign-off and discrepancies
- **AC1** Given a delivery arrives Wednesday, When the shift lead checks the highlighted lines and signs off, Then their name, date and time are recorded.
- **AC2 (exception)** Given 12oz cups arrived instead of 16oz cups, When the shift lead signs off, Then a "wrong item" discrepancy is recorded and appears in the issues log.
- **AC3 (exception)** Given a delivery has not been signed off by `TBD` h after arrival, Then it is shown as "not signed off" in the weekly report (alert in FR-36 is a Could).

#### US-24 — Log stockouts and emergency requests
- **AC1** Given oat milk runs out on Thursday, When the manager logs it, Then the record holds store, item, quantity, date and time, type "stockout", reason and who logged it, and it appears in the weekly stockout count.
- **AC2 (exception)** Given an entry has no item, When the manager tries to save it, Then it is refused with "item is required".
- **AC3 (exception)** Given Mei is away, When an emergency request is logged, Then the named backup sees it in the open list.

#### US-25 — Emergency request status
- **AC1** Given an open request is filled by courier, When the coordinator updates it, Then the status is "fulfilled by courier" with the date and time.
- **AC2 (exception)** Given a request has been open for more than `TBD` h, When the open list is viewed, Then it is highlighted as overdue.

#### US-28 — Missing waste records flagged
- **AC1** Given 12 stores and 4 with no waste records for October, When the `TBD` day of November passes, Then those 4 stores are listed by name to the waste-log owner.
- **AC2** Given all 12 stores have submitted, When the check runs, Then the result is "12/12 complete".

#### US-31 — Weekly stockout report
- **AC1** Given 5 stockouts logged in a week, When the report is run, Then it shows 5 stockouts, split by store and item.
- **AC2 (exception)** Given a stockout logged twice for the same store, item and day, When the report is run, Then it is counted once and the duplicate is listed for review [Assumption: rule to confirm].

#### US-32 — Monthly KPI report
- **AC1** Given a full month of data, When the report is produced, Then it shows each KPI in FR-49 with its baseline, target and actual value.
- **AC2 (exception)** Given a KPI has no target yet (e.g. manager ordering time, Q-08), When the report is produced, Then the target shows "TBD" rather than being left out.

#### US-33 — Individual logins and change history
- **AC1** Given every warehouse user has their own login, When anyone changes an order line, Then the history shows who and when.
- **AC2 (exception)** Given someone tries to use a shared or generic login, Then access is refused.

#### US-34 — Named owners
- **AC1** Given the owners are agreed (D-03, D-04), When anyone looks up "stock at the store", Then the accountable role is shown.
- **AC2 (exception)** Given an area in FR-55 has no owner, When the monthly KPI report is produced, Then the missing owner is listed.

#### US-35 — Written procedures
- **AC1** Given the procedures are written, When the backup follows them in a test week, Then they complete the load, emergency requests and substitutions without help from Mei (NFR-10).
- **AC2 (exception)** Given a step fails in the test, When the test ends, Then the gap is recorded and the procedure updated before the next test.

**Quality checks.**
- Every Must story has a happy path and at least one exception.
- Today's pain points appear as edge cases: 100 vs 10 lids (US-03), 16oz → 12oz cups (US-19, US-23), Mei away (US-24, US-35), late orders (US-06) and missing waste logs (US-28).
- ACs that use a `TBD` value become fully testable once Q-09 and Q-10 are answered.

---

## 7. Prioritisation (MoSCoW)

| Priority | Count | IDs | Rationale (key items) |
|---|---|---|---|
| Must | 33 FR · 23 US | FR-01–04, 08–12, 14, 15, 22–24, 26–29, 31, 32, 34, 35, 37–39, 42, 45, 48, 49, 53–56 · US-01–03, 05, 06, 08–10, 15, 16, 18–21, 23–25, 28, 31–35 | **Standard template + load (FR-01–03, 14, 15):** without them BR-03 fails: re-keying grows to 8.5–11.3 h/wk at 17 stores. **Over-par flag (FR-04):** the cheapest guard against "100 lids instead of 10". **New-store set-up (FR-08):** stores 13–17 open July 2027. **Late-order rule (FR-09–12):** Monday can't run on "text Mei and hope". **Par reset + owner (FR-22–24):** stale par levels are the main cause of stockouts (RC-01). **Reorder points, procedures (FR-26, 56):** BR-05, repeat of August. **Substitution rule + list + sign-off (FR-27–29, 31–35):** a direct cause of stockouts (RC-04) and Tom's accountability need. **Issues log + reports (FR-37–39, 42, 45, 48, 49):** no baseline, no business case (RC-06). **Logins, audit, owners (FR-53–55):** accountability (BR-06). |
| Should | 18 FR · 12 US | FR-05, 06, 13, 16–20, 25, 30, 33, 40, 41, 43, 44, 46, 47, 50 · US-04, 07, 11–14, 17, 22, 26, 27, 29, 30 | Important but with a workaround. **Suggested quantities and warehouse view (FR-17–20):** the par reset helps first; these depend on Q-04 and Q-05 and on IT time. **Pastry review (FR-46, 47):** biggest waste lever but scope `TBD`. |
| Could | 5 FR | FR-07, 21, 36, 51, 52 | Core-only counting, over-commit flag, unsigned-delivery alert, lost-sales estimate, auto stock report. |
| Won't (this time) | 3 FR | FR-57, 58, 59 | **FR-57** invoice matching: any link to an end-of-support system may be wasted (R-11). **FR-58** dairy: scope `TBD`, no problems reported. **FR-59** warehouse system replacement: a separate decision (R-10) likely over the $60k and after the July openings. |

**Effort check.** Musts are 33 of 56 FRs (59%), at the limit of the ~60% guide. Most are low effort (rules, owners, a template, a log: ⚡ in `03-gap`). The costliest items (FR-17–20, suggested quantities and warehouse view) were kept as Should on purpose. Confirm with Priya and Tom (Q-18).

**Quality checks.**
- The priorities match the FR and US tables.
- Every Must FR traces to a BR (see §8).

---

## 8. Traceability matrix

| BR | Stakeholder reqs | Functional reqs | NFRs | User stories |
|---|---|---|---|---|
| BR-01 Stockouts | SR-01, 06, 10, 11, 13, 14, 18, 19, 22 | FR-04, 06, 17–23, 25, 27–32, 35, 37, 39, 40, 48 | NFR-03, 04, 06, 27 | US-03, 04, 12–15, 17, 19–21, 23–26, 31 |
| BR-02 Waste | SR-04, 10, 11, 23 | FR-04, 20, 22, 23, 44–47 | NFR-04, 16 | US-03, 14, 15, 28–30 |
| BR-03 Scale with one coordinator | SR-03, 15, 16, 20 | FR-01–03, 08, 09, 11–15 | NFR-01, 02, 07–09, 25, 27 | US-01, 02, 05–10 |
| BR-04 Manager time | SR-09, 10, 12 | FR-01, 05–07, 10, 17, 19, 50 | NFR-05, 09, 17, 20 | US-01, 04, 05, 12, 13, 32 |
| BR-05 Continuity | SR-02, 16, 17 | FR-11, 14, 16, 26, 39, 42, 52, 56 | NFR-10, 11 | US-06, 09, 11, 18, 24, 25, 35 |
| BR-06 Accountability and measures | SR-01, 04–06, 08, 19 | FR-24, 29, 33–38, 41, 43, 45, 48, 49, 51, 53–55 | NFR-12–15, 18, 19, 21 | US-16, 20, 22–24, 26–28, 31–34 |
| BR-07 Supported warehouse system | SR-20 | FR-59 (Won't) | NFR-23, 24, 28 | — |
| *All (constraints)* | SR-07 | — | NFR-22, 26 | — |
| **Orphans** | SR-21 | FR-57, FR-58 | — | — |
| **Uncovered** | — | BR-07 has no active FR or US | — | — |

**Explanations.**
- **Orphans.** SR-21 and FR-57 (invoice matching) and FR-58 (dairy) have no BR. They are recorded as Won't so they aren't forgotten. If dairy or invoice matching come into scope, they need a BR first (Q-06).
- **Uncovered.** BR-07 is met by a decision (R-10), not by functions in this release. NFR-23, 24 and 28 protect it. The real requirements for a future warehouse system should be a separate pass once the vendor's upgrade path is known (Q-04).

**Quality checks.**
- Every Must FR and Must US traces to BR-01 to BR-06.
- The orphan and uncovered rows are explained above and listed under Open questions.

---

## Open questions

All *not asked — --no-questions*. Q-IDs are local to this document.

| ID | Question | Affects | Ask |
|---|---|---|---|
| Q-01 | **D-01:** if a store misses 10:00 Monday, is the default its suggested order or last week's order? If the store then submits late, which order stands? | FR-11, US-06 | Priya |
| Q-02 | **D-02:** who approves substitutions that aren't on the approved list, and how are they reached before the van leaves? | FR-28, US-19 | Mei, Priya |
| Q-03 | **D-03 / D-04:** who owns stock rules, the issues log and the pastry standing order? Who is accountable for stock at the store once signed for? | FR-24, 55, US-34 | Priya, Tom |
| Q-04 | What file format does the warehouse system's import accept, and can it export available stock daily? What upgrade path and cost has the vendor offered? | FR-14, 20, NFR-04, BR-07 | Mei, Josh, vendor |
| Q-05 | Can till products be converted to stock-item usage (e.g. oat milk per drink)? Who owns TillPoint? | FR-17–19, US-12 | Josh, Tom |
| Q-06 | Are pastries (Crumb & Co.) and dairy (Valley Dairy) in scope? | FR-46, 47, 58 | Priya |
| Q-07 | Is waste recording in scope beyond completeness (FR-45)? Should waste be recorded by item and reason? | FR-44, 45 | Priya, Tom |
| Q-08 | What target do you want for manager ordering time (BR-04) and for order errors? | BR-04, FR-49 | Priya |
| Q-09 | What over-par multiple should trigger a flag (e.g. 2× or 3×)? | FR-04, US-03 | Stock-rules owner, Mei |
| Q-10 | Timings: order confirmation (NFR-05), what's-coming lead time (NFR-06), sign-off time on a busy shift (NFR-18), time to log an issue (NFR-19), when an unsigned delivery or an open emergency is overdue (FR-36, US-25)? | NFRs, ACs | Mei, Daniel, a shift lead |
| Q-11 | Is the store laptop usable for counting on the floor, or is a tablet or phone needed? | FR-05, NFR-20 | Daniel, 1–2 other managers |
| Q-12 | What hours must ordering and the issues log be available, and what uptime is acceptable? | NFR-09 | Priya, Josh |
| Q-13 | How fast must leavers' access be removed? How long must change history be kept? Any privacy rules for staff names in the log? | NFR-13–15 | Josh, Tom |
| Q-14 | Are there food-safety or expiry-tracking rules for stock (e.g. syrups, plant milks)? | NFR-16, FR-07 | Priya |
| Q-15 | How much of Josh's time is available Feb–Jun 2027, and what monthly support effort is acceptable? | NFR-25, FR-17–20 | Josh, Priya |
| Q-16 | Growth beyond 17 stores: what should the process cope with? How fast must a new store be set up? Can the van and 2 routes handle 17 stores? | NFR-07, 08 | Priya, Mei, driver |
| Q-17 | Is "par minus stock on hand, rounded up to a pack" the right suggested-quantity rule? Should stock in transit or seasonality be included? | FR-19, US-13 | Stock-rules owner, Mei |
| Q-18 | Do you agree the Must list (59% of FRs), BR-06 and BR-07, and how to handle the conflicts in §2: "just in case" ordering vs waste, busy shifts vs sign-off, $182k vs ~$250k waste, lost-sales evidence, and reported stockouts rising once logging starts? | §1, §2, §7 | Priya, Tom |
| Q-19 | Do any staff need accessibility support (e.g. screen size, reading aids) when using the template or log? | NFRs (skipped category) | Priya, store managers |
| Q-20 | Who will be the coordinator backup (R-03), and when can they be trained? | FR-42, 56, NFR-10 | Priya, Mei |

## Next steps
1. **Review the Musts and the conflicts** with Priya and Tom in one 45-minute session (Q-18). Get decisions D-01 to D-04 (Q-01 to Q-03) and the pastry and waste scope (Q-06, Q-07).
2. **Close the feasibility gates** with Mei, Josh and the vendor: import format and stock export (Q-04), till-to-item conversion (Q-05), IT capacity (Q-15). These decide whether FR-14 is a quick win and whether FR-17–20 stay in the Feb–Jun window.
3. **Fill the `TBD` numbers** (Q-09, Q-10) in a short walk-through with Mei, Daniel and a shift lead, then update NFR-05, 06, 18, 19 and the ACs.
4. **Start the Phase 0 items before 1 Dec** (subject to Priya's OK, A-05): issues log (FR-37–39), substitution list (FR-27, 28), individual logins (FR-53), written procedures (FR-56).
5. **Run `/ba-docs samples/coffee-chain`** to build the executive pack (business case, roadmap, decisions) and the analyst pack (BRD, RACI, glossary and ID index) from this document and `03-gap`.

## Technique notes
- **Business requirements.** Business requirements anchor the "why". If a later requirement can't trace to a BR, it is either scope creep or a missing goal. Both are worth raising. Here, FR-57 and FR-58 have no BR, which is why they are Won't.
- **Stakeholder requirements.** Stakeholder requirements keep the user's voice visible. They are where conflicting priorities usually surface first. Here, "just in case" ordering vs waste, and busy shifts vs sign-off.
- **Functional requirements.** Good FRs are atomic and testable. A tester should be able to write a pass/fail check from each one without asking the author. Business rules (FR-11, 19, 28, 40) are written as separate FRs so they can be changed without rewriting the features around them.
- **Non-functional requirements.** NFRs are the most often forgotten and the most expensive to fix late. Vague ones ("must be fast") are untestable, so always push for a number. Where no number exists yet, `TBD` plus an open question is better than a guess.
- **User stories.** User stories are a conversation starter, not a full spec. INVEST (Independent, Negotiable, Valuable, Estimable, Small, Testable) is the checklist BAs use to tell whether a story is ready for a team to estimate.
- **Acceptance criteria.** Given/When/Then (Gherkin) comes from Behaviour-Driven Development. Writing the failure cases is where a BA adds the most value, because that's where today's pain points hide (100 vs 10 lids, 16oz → 12oz cups, Mei being away).
- **Prioritisation (MoSCoW).** MoSCoW forces trade-offs. The "Won't" list is as valuable as the "Must" list: it protects scope and records decisions.
- **Traceability matrix.** A requirements traceability matrix (RTM) proves coverage and shows the impact of change. If a goal changes, you can see exactly which requirements and stories move with it.
