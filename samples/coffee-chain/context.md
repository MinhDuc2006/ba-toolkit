# Context: Harbour Lane Coffee Co. — Stock ordering review

- **Engagement folder:** samples/coffee-chain
- **Last updated:** 2026-11-12
- **learning_mode:** on
- **Intake mode:** `--no-questions`. Built only from `inputs/`; nothing was confirmed with the user. Missing facts are marked `TBD`. Every question I would have asked is listed under **Open questions**.
- *Fictional practice case (inputs/01-kickoff-meeting-notes.md).*

## Topic status
| Topic | Status | Main sources |
|---|---|---|
| Company overview | 🟡 📄 | inputs/01 |
| Goals and success criteria | 🟡 📄 | inputs/01, 04, 05 |
| Stakeholders | 🟡 📄 | inputs/01–04 |
| Current systems and tools | ✅ 📄 | inputs/02, 03, 04 |
| Key processes | 🟡 📄 | inputs/02, 03, 04 |
| Pain points and problems | ✅ 📄 | inputs/01–05 |
| Data and metrics | 🟡 📄 | inputs/04, 05 |
| Constraints and risks | 🟡 📄 | inputs/01, 03, 04 |
| Scope and deliverables | 🟡 📄 | inputs/01 |

Legend: ✅ filled · 🟡 partial (has `TBD` or `[Assumption]`) · ⬜ missing · 📄 pre-filled from inputs, not confirmed with the user.

## Company overview
- **What it does:** Harbour Lane Coffee Co. runs 12 coffee shops across one city. It was founded in 2015. (inputs/01-kickoff-meeting-notes.md)
- **Customers:** walk-in coffee shop customers [Assumption]. Customer segments: TBD.
- **Size:** about 140 staff and revenue of about $14M/yr. (inputs/01)
- **Supply set-up:**
  - One central warehouse with 4 staff (coordinator, 2 pickers, 1 driver) supplies stores with coffee beans, cups and lids, syrups, plant milks, packaged snacks and cleaning products. (inputs/01, inputs/03-interview-warehouse-coordinator.md)
  - Each store orders fresh dairy milk directly from Valley Dairy. (inputs/01, inputs/02-interview-store-manager.md)
  - Pastries come from Crumb & Co. on a standing daily order per store. (inputs/01, inputs/02)
- **Areas in this engagement:** stock ordering across the 12 stores and the central warehouse, under the Operations Director. (inputs/01)
- **How the area is organised:**
  - Priya Nair (Operations Director) sponsors the work.
  - Each store has a store manager plus shift leads and baristas. (inputs/01, 02)
  - The warehouse is run by Mei Chen (Warehouse & Purchasing Coordinator). (inputs/03)
  - Reporting lines, such as whether store managers and the warehouse report to Priya: TBD.
- **Recent changes:**
  - The business grew from 4 to 12 stores in the last 3 years. (inputs/01)
  - **5 more stores are planned by July 2027**, taking the total to 17. (inputs/01)
  - LedgerOne (accounting) was implemented recently. (inputs/01)

> *Why a BA asks this:* size and growth plans show what scale any solution has to cope with. Here, going from 12 to 17 stores is the main reason for the work.

## Goals and success criteria
- **Trigger:** the planned growth to 17 stores. Priya said: "The way we order stock today won't survive 17 stores." (inputs/01)
- **Other drivers** (inputs/01):
  - Stockouts during the spring promo.
  - Waste from expired syrups and over-ordered pastries.
  - Ordering depends on one person: it "fell apart" when Mei was off sick in August.
- **Objectives Priya stated** (inputs/01):
  1. Cut stockouts of core items "by at least half" before the new stores open.
  2. Reduce stock waste meaningfully: "10–20% would be great".
  3. Have a way of ordering that can scale to 17+ stores without hiring another coordinator.
  4. Managers should spend less time on paperwork and more time on the floor.
- **Success metrics (baseline → target):**

| Metric | Baseline | Target | Source |
|---|---|---|---|
| Core-item stockouts | 54 reported in 12 wks (≈ 4.5/wk), likely under-reported | ≤ ~2.25/wk ("at least half") | inputs/05, inputs/01 |
| Recorded stock waste | ≈ $182k/yr (FY2025–26) | 10–20% lower (≈ $18k–$36k/yr saved) | inputs/04, inputs/01 |
| Coordinator headcount at 17 stores | 1 | still 1 | inputs/01 |
| Store manager time on ordering | ~2.5–3.5 h/wk per store | TBD | inputs/05 |

- **Deadlines:**
  - Recommendations and a business case are due in about 6 weeks from kickoff (20 Oct 2026), so around **1 Dec 2026** [Assumption: date worked out from "~6 weeks"]. (inputs/01)
  - The improvements must be in place before the new stores open (by July 2027). (inputs/01)
- **Failure conditions:**
  - Tom (Head of Finance) does not want "another system nobody uses properly". (inputs/04-interview-finance.md)
  - Any other failure criteria from the sponsor: TBD.

> *Why a BA asks this:* goals with numbers attached are how options get ranked later and how the business case is judged.

## Stakeholders
| Stakeholder | Role | Interest | Influence | Attitude to change | Source |
|---|---|---|---|---|---|
| Priya Nair | Operations Director, **sponsor** | Scale to 17 stores, fewer stockouts, less waste | High | Champion [Assumption] | inputs/01 |
| Tom Reyes | Head of Finance, controls budget | Evidence-based savings, clear accountability, adoption | High | Supportive but sceptical: wants evidence [Assumption] | inputs/01, 04 |
| CEO + 2 investors (board) | Final audience for the business case | Return on investment, growth readiness | High | TBD | inputs/01 |
| Daniel Okafor | Store Manager, Docklands (busiest store) | Less counting and chasing, delivery confirmations | Medium | Positive: has ideas (use till data) [Assumption] | inputs/02 |
| Other 11 store managers | Count stock and place orders | Same as Daniel [Assumption] | Medium | TBD | inputs/01, 02 |
| Mei Chen | Warehouse & Purchasing Coordinator, **key SME** (subject-matter expert) and single point of failure | Less re-keying, fewer errors | High (practical) | TBD | inputs/03 |
| Pickers (2), driver (1) | Pick, pack and deliver | Clear pick lists, a rule for substitutions | Low | TBD | inputs/03 |
| Shift leads / baristas | Check deliveries, borrow stock from other stores | Fewer stockouts | Low | TBD | inputs/02 |
| Josh | IT generalist (only in-house IT) | Workload, supportability | Medium | TBD | inputs/01 |
| External IT contractor | On-call IT support | TBD | Low | TBD | inputs/01 |
| Accounts assistant | Matches supplier invoices in LedgerOne (~2 days/month) | Less manual matching | Low | TBD | inputs/04 |
| Suppliers (incl. Valley Dairy, Crumb & Co.), StockPro vendor | External | TBD | Medium | TBD | inputs/01, 02, 03 |
| Customers | Affected by stockouts ("customers walk out") | Product availability | Indirect | n/a | inputs/02 |

- **Possible conflict:** Priya estimates waste at about $250k; Tom will only stand behind $182k. Tom also wants evidence of lost sales before accepting Priya's view that they are "big". (inputs/01, 04)
- **Next people to talk to:** at least one more store manager from a quieter store, a picker, and Josh (IT). [Assumption] How they prefer to be engaged: TBD.

> *Why a BA asks this:* knowing who decides, who does the work and who can block it shapes who gets interviewed and how the findings are presented.

## Current systems and tools
| System / tool | Purpose | Owner | Users | Notes | Source |
|---|---|---|---|---|---|
| **StockPro** | Warehouse inventory, purchase orders (POs), pick lists, goods received | Warehouse (Mei) [Assumption] | Warehouse staff | About 9 years old. **Current version goes end-of-support Dec 2027.** Has a CSV import that is not set up. One shared login. | inputs/03 |
| **TillPoint POS** | Point-of-sale (till) system; sales by product | TBD | Stores, Finance | Reliable sales data, exports CSV daily. Used only for revenue reporting. | inputs/02, 04 |
| **LedgerOne** | Accounting | Finance | Finance, accounts assistant | Recently implemented. **Must keep — board won't revisit.** | inputs/01, 04 |
| Excel order files (one per store) | Store stock count and order | Each store manager | Store managers | Layout differs by store. Par levels (target stock levels) not updated since 2024. | inputs/02, 03 |
| Email (orders@ inbox) | Sending orders; supplier POs as PDFs | Warehouse | Stores, Mei, suppliers | | inputs/02, 03 |
| WhatsApp group, phone, sticky notes | Emergency and mid-week orders | — | Managers, Mei | Informal workaround | inputs/02, 03 |
| Paper stock sheet + clipboard | Sunday stock count | Stores | Store managers | | inputs/02 |
| Paper waste log → Google Sheet | Waste recording | Stores / Finance | Managers | About 8 of 12 stores complete it properly | inputs/04 |
| Valley Dairy web form / phone | Daily dairy order | Supplier | Store managers | | inputs/02 |

- **Integrations:**
  - StockPro, TillPoint and LedgerOne are **not connected**. (inputs/03)
  - Data is re-keyed by hand in three places:
    - store Excel → StockPro (Mei)
    - StockPro PO printouts → LedgerOne invoice matching (accounts assistant)
    - StockPro → Excel monthly stock report for Finance. (inputs/03, 04)
- **Who supports these systems:**
  - IT: Josh plus an on-call contractor. (inputs/01)
  - StockPro: the vendor still supports it. (inputs/03)

> *Why a BA asks this:* handoffs between systems and manual re-keying are where errors and delays usually start.

## Key processes
1. **Weekly store replenishment (store → warehouse)**. This is the core process.
   - **Trigger:** weekly cycle. Sunday after close. (inputs/02)
   - **Steps:**
     1. The manager counts stock on a paper sheet (~1–1.5 h).
     2. On Monday the manager types the counts into Excel and decides quantities "by guess".
     3. The manager emails the file to orders@ by 10am Monday.
     4. Mei re-keys about 40 lines per store into StockPro (6–8 h).
     5. On Tuesday StockPro prints pick lists and two pickers pack the orders.
     6. On Wed/Thu the van delivers on 2 routes.
     7. A shift lead checks the delivery "if they're not slammed". (inputs/02, 03)
   - **Volume:** 12 orders and about 480 lines per week. (inputs/03)
   - **Cycle time:** 3–4 days from count to delivery [Assumption, based on Sunday count → Wed/Thu delivery].
2. **Emergency / mid-week top-up.** A manager phones or WhatsApps Mei. Mei writes it down and the item goes by courier (~$85 each), or staff borrow stock from another store. About 4.3/week, more in summer. (inputs/02, 03, 05)
3. **Warehouse purchasing (warehouse → suppliers).**
   - Mei checks stock against reorder points she sets "from experience".
   - She raises POs in StockPro and emails them as PDFs.
   - Goods are received on Friday and entered into StockPro. (inputs/03)
4. **Direct supplier orders:** daily dairy orders to Valley Dairy, and the standing pastry order with Crumb & Co. The pastry order is changed by email "maybe twice a year". (inputs/02)
5. **Waste recording:** paper log, monthly Google Sheet, then Finance. (inputs/04)
6. **Invoice matching:** supplier invoices are matched by hand in LedgerOne against printed StockPro POs, about 2 days/month. (inputs/04)

- **Documentation:**
  - No documented process was mentioned.
  - New managers learn from whoever trains them. (inputs/02)
  - Reorder-point logic is known only to Mei. (inputs/03)
  - Whether any written procedure exists: TBD.
- **Variation:** each store's Excel file is different. (inputs/02, 03) How the process differs across stores beyond Docklands: TBD.

> *Why a BA asks this:* a high-level process list shows which workflow to map in detail first with `/ba-process`.

## Pain points and problems
| # | Pain point (stakeholder's words) | Who feels it | Impact | Frequency / evidence | Source |
|---|---|---|---|---|---|
| 1 | Stockouts of core items, especially oat milk and large cups: "customers walk out" | Customers, store staff | Lost sales (not measured), emergency courier costs | 54 incidents in 12 wks across 9 stores. Oat milk 21, 16oz cups 14. | inputs/02, 05 |
| 2 | Mei "spends most of Monday re-typing store orders" | Mei | 6–8 h/wk ≈ $204–$272/wk at $34/h. Single point of failure. | Weekly | inputs/01, 03, 04 |
| 3 | Re-keying errors: "I've sent 100 lids instead of 10" | Stores, warehouse | Wrong stock, rework | 31 errors in 12 wks (≈ 2.6/wk) | inputs/03, 05 |
| 4 | Waste: expired syrups and over-ordered pastries. "We bin maybe 15–20 pastries a day." | Finance, stores | **$182k/yr recorded** (pastries ~$96k, syrups ~$31k, other ~$55k). Priya estimates ~$250k including unrecorded waste. | Daily (pastries) | inputs/01, 02, 04 |
| 5 | Manual counting and ordering: "3 hours easy, plus chasing" | Store managers | ~2.5–3.5 h/wk × 12 stores at $38/h | Weekly | inputs/02, 05 |
| 6 | Emergency deliveries and borrowing between stores | Mei, stores, Finance | ~$19k/yr courier cost, plus staff time | ~4.3/wk. "Most weeks in summer." | inputs/02, 04, 05 |
| 7 | Unannounced substitutions: "Ordered 16oz cups, got 12oz — no one told us" | Stores | Wrong stock, more stockouts | 11 in 12 wks. No process for it. | inputs/02, 03, 05 |
| 8 | Stores can't see warehouse stock, so they over-order "just in case" | Stores, warehouse | Stock stuck in store back rooms while the warehouse runs out | Ongoing | inputs/02, 03 |
| 9 | Dependence on one person: when Mei was sick in August, two stores "got nothing for a week" | Whole chain | Business continuity risk | Happened in Aug 2026 | inputs/01, 03 |
| 10 | Late orders: "If I'm late, I text Mei and hope" | Mei | Delays the Monday work | 2.4 late emails/wk | inputs/02, 05 |
| 11 | Deliveries not checked against the order | Stores, Finance | Errors not caught; stock losses can't be traced ("nobody is accountable") | Often | inputs/02, 04 |
| 12 | Par levels out of date (not updated since 2024); store Excel files all different | Stores | Ordering by guesswork | Ongoing | inputs/02 |

- **Previous attempts to fix these:** none mentioned. TBD.

> *Why a BA asks this:* pain points in the stakeholders' own words, with evidence attached, are the raw material for root-cause analysis and for sizing the business case.

## Data and metrics
- **Data that exists today:**

| Metric | Current value | Source / reliability |
|---|---|---|
| Core-item stockouts | 54 / 12 wks (≈ 4.5/wk) | Self-reported on WhatsApp. **Likely under-reported.** (inputs/05) |
| Order errors reported | 31 / 12 wks | Email + WhatsApp (inputs/05) |
| Emergency courier deliveries | 52 / 12 wks. ≈ $19k last FY at ~$85 each. | Courier invoices: reliable (inputs/04, 05) |
| Late order emails | 2.4/wk | orders@ timestamps: reliable (inputs/05) |
| Unannounced substitutions | 11 / 12 wks | WhatsApp (inputs/05) |
| Manager ordering time | 2.5–3.5 h/wk per store | Interviews with 2 managers (inputs/05). Only one interview is in `inputs/`. |
| Coordinator re-keying time | 6–8 h/wk | Mei's own estimate (inputs/03) |
| Stock waste write-off | $182k FY2025–26 | Finance. 4 stores' logs are incomplete. (inputs/04) |
| Warehouse stock value | ~$210k | StockPro (inputs/04) |
| Order volume | ~480 lines/wk | Mei's estimate (inputs/03) |
| Sales by product | Daily CSV | TillPoint: reliable, but not used for ordering (inputs/04) |
| Loaded staff cost | Store manager $38/h · coordinator $34/h · barista $29/h | Finance (inputs/04) |

- **Gaps (data people want but can't get):**
  - Lost sales from stockouts
  - Stock on hand at stores
  - Complete waste data (4 stores missing)
  - A record of stockouts held at the warehouse (inputs/03, 04, 05)
- **Disagreement over "which number is right":** waste is $182k (Finance) vs ~$250k (Priya's estimate). (inputs/01, 04)
- **Samples available:** none yet. Could be requested:
  - TillPoint CSV exports
  - a StockPro reorder-point export
  - two or three store Excel order files

> *Why a BA asks this:* baselines turn "it feels bad" into numbers the business case can be built on, and data gaps become findings in their own right.

## Constraints and risks
- **Budget:**
  - **Up to ~$60k one-off** this financial year (FY ends 30 Jun 2027).
  - Ongoing costs such as subscriptions need a payback period under 18 months. (inputs/01, 04)
- **Timeline:**
  - **Change freeze 1 Dec – 31 Jan** (peak season). (inputs/01)
  - New stores open by July 2027. (inputs/01)
  - The current StockPro version goes **end-of-support Dec 2027**. (inputs/03)
  - That leaves roughly Feb–Jun 2027 to deliver changes [Assumption].
- **Mandated tools:** LedgerOne must stay. (inputs/01) Other mandated or banned tools and vendors: TBD.
- **Compliance and security:**
  - The shared StockPro login is a security and accountability concern. (inputs/03, 04)
  - Food-safety or traceability rules for stock (e.g. expiry dates): TBD.
  - Privacy requirements: TBD.
- **Resourcing:**
  - IT is one generalist (Josh) plus an on-call contractor. (inputs/01)
  - Store managers have little spare time. (inputs/02)
- **Known risks:**
  - Low adoption: "another system nobody uses properly". (inputs/04)
  - Dependence on Mei's knowledge. (inputs/03)
  - The baseline data is weak, which makes the business case harder to prove. (inputs/04, 05)
  - Any StockPro investment could be stranded when the current version reaches end-of-support [Assumption].
- **Past failed change projects:** TBD.

> *Why a BA asks this:* constraints rule options in or out early. Here, the $60k budget, the Dec–Jan freeze and StockPro's end of support narrow the choices a lot.

## Scope and deliverables
- **In scope:**
  - How ordering works today across stores and the warehouse, from store order to warehouse delivery. (inputs/01)
  - Warehouse purchasing from suppliers [Assumption: closely linked].
- **Unclear (TBD):**
  - Direct supplier ordering: dairy (Valley Dairy) and pastries (Crumb & Co.). Pastries are the largest single waste item (~$96k), so this decision matters.
  - Invoice matching in LedgerOne.
  - Waste recording.
- **Out of scope:** replacing LedgerOne. (inputs/01)
- **Deliverables:**
  - Recommendations and a **business case** for leadership in ~6 weeks.
  - A version Priya can present to the board (CEO + 2 investors). (inputs/01)
  - Format and length: TBD.
  - Analysis deliverables likely needed: system map, process map of weekly replenishment, gap analysis, requirements, and the executive pack [Assumption].
- **Assumptions recorded:**
  - A-01: the business case is due ~1 Dec 2026.
  - A-02: delivery work happens Feb–Jun 2027.
  - A-03: store stockouts are under-reported, so the real baseline is higher.
- **Parked items:** none yet.

> *Why a BA asks this:* agreeing scope early stops scope creep and makes sure the deliverables match what the audience will actually read.

## Open questions
All of these were *not asked — --no-questions*.

1. Are dairy (Valley Dairy) and pastry (Crumb & Co.) ordering in scope? Pastries are ~$96k of the $182k waste. — topic: Scope, ask: Priya
2. What is the exact due date and format for the business case and board pack (slides vs document, length)? — topic: Scope, ask: Priya
3. Which waste baseline will leadership accept: $182k recorded or ~$250k estimated? Can we sample unrecorded waste? — topic: Data and metrics, ask: Priya + Tom
4. Can lost sales from stockouts be estimated, e.g. from TillPoint sales dips on stockout days? — topic: Data and metrics, ask: Tom
5. What target is there for store manager time on ordering, and for order errors? — topic: Goals, ask: Priya
6. What are the reporting lines (do store managers and the warehouse report to Priya)? Who owns TillPoint? — topic: Company overview / Systems, ask: Priya
7. Is the StockPro vendor offering an upgrade path before the Dec 2027 end of support, and at what cost? — topic: Systems / Constraints, ask: Mei / Josh
8. Are there other mandated or banned tools, or IT security policies (e.g. shared logins, cloud SaaS)? — topic: Constraints, ask: Josh
9. Are there food-safety or traceability requirements for stock (expiry tracking, batch codes)? — topic: Constraints, ask: Priya
10. Has a past change project failed here? What happened? — topic: Constraints, ask: Priya / Tom
11. How do other stores' ordering practices differ from Docklands? Who was the second manager in the time data? — topic: Processes, ask: BA / store managers
12. What has already been tried to fix stockouts or waste? — topic: Pain points, ask: Priya / Mei
13. How do Mei, the pickers, Josh and other store managers feel about the change, and how do they prefer to be engaged? — topic: Stakeholders, ask: Priya
14. Who should own stock accountability (store vs warehouse) in future? — topic: Stakeholders, ask: Priya + Tom
15. Can we get samples for `inputs/`: TillPoint CSV, StockPro reorder-point export, 2–3 store Excel order files? — topic: Data and metrics, ask: Mei / Josh
16. Who are the customer segments, and does it matter for this work (e.g. wholesale or catering)? — topic: Company overview, ask: Priya
