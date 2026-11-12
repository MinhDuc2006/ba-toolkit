# Assumptions, decisions and open questions register

- **Engagement:** Harbour Lane Coffee Co. — Stock ordering review (`samples/coffee-chain`)
- **Date:** 2026-11-12 (live register: update the date and status on every change)
- **Mode:** `--no-questions`. No decisions have been confirmed by stakeholders. Decisions D-05 to D-13 are **BA-proposed** method or scope choices already used in the outputs, recorded so that the history is visible.
- **Sources used:** every `[Assumption]`, `TBD` and Open questions list in `context.md`, `outputs/01`–`04`, and the exec pack `05-exec-01`–`04`.
- **ID rules:**
  - A- continues from context.md (A-01–A-03) and 03-gap (A-04–A-08).
  - D-01–D-04 come from 02-process.
  - **Q-IDs here are consolidated** and supersede the local Q-numbers in each output. The *Raised in* column maps them back: `ctx#n` = context.md item n, `SM`, `PR`, `GAP`, `REQ` = Q-n in outputs 01, 02, 03, 04.

---

## 1. Assumptions
Risk if wrong: **H** = changes a recommendation or the business case · **M** = changes a size or a date · **L** = minor.

| ID | Assumption | Used in | Risk if wrong | Validate with | Status |
|---|---|---|---|---|---|
| A-01 | The business case is due ~1 Dec 2026 (from "~6 weeks" after the 20 Oct kickoff) | context.md › Goals; 05-exec-01, 03 (30 Nov deadline) | M | Priya | Open |
| A-02 | Delivery work happens Feb–Jun 2027 (between the freeze and the openings) | context.md; 03-gap roadmap; 04-req NFR-27 | M | Priya | Open |
| A-03 | Store stockouts are under-reported, so the real baseline is higher | context.md; 02-process §5; BR-01; 05-exec-01 | L (direction known) | R-01 log data | Open |
| A-04 | Syrup waste is driven mainly by "just in case" ordering and no expiry view | 03-gap Problem 2 | M | 2–3 store managers (Q-31) | Open |
| A-05 | Logging, rules and role decisions are allowed during the Dec–Jan freeze | 03-gap §5, §6; 04-req NFR-27; 05-exec-03 decision 3 | **H**: the whole "Now" horizon depends on it | Priya, **by 30 Nov 2026** | Open |
| A-06 | Impact/effort scores are BA judgement; costs not yet estimated | 03-gap §5 | M | Tom, Josh | Open |
| A-07 | Pastry waste can fall 15–20% by matching standing orders to sales | 03-gap R-07; 05-exec-01, 02 (≈ $14k–$19k) | **H**: the largest cash benefit in Option 1 | 2-store pilot, Priya | Open |
| A-08 | The StockPro upgrade or replacement (R-10) is funded outside this FY's $60k | 03-gap R-10; 05-exec-02 | **H** | Tom | Open |
| A-09 | Coordinator re-keying falls from 6–8 h to < 1 h/wk once orders are imported | 03-gap R-04; 04-req NFR-01; 05-exec-01, 02, 03 | **H**: coordinator benefit and BR-03 | 2-store pilot (Feb 2027) | Open |
| A-10 | Coordinator review of flagged lines takes ≤ 5 min per store | 02-process §5; 04-req NFR-02 | L | Pilot | Open |
| A-11 | Store managers need ≤ 1 h of training on the template | 02-process CH-01; 04-req NFR-17; 05-exec-02 (≈ $0.5k) | L | Pilot | Open |
| A-12 | The stock-rules review takes 1–2 h a month | 02-process CH-12; 03-gap R-05; 05-exec-02 (≈ $0.5k–$0.9k/yr) | L | Stock-rules owner | Open |
| A-13 | Cycle time is 3–4 days (Sunday count → Wed/Thu delivery) | context.md; 02-process §5 | L | Mei | Open |
| A-14 | StockPro's CSV import can accept store order lines, and StockPro can export available stock | 02-process §6; 03-gap R-04, R-06; 04-req FR-14, FR-20 | **H**: gates R-04 and R-06 | Mei, Josh, vendor (Q-08), **by 31 Jan 2027** | Open |
| A-15 | TillPoint products can be converted to stock-item usage (e.g. oat milk per drink) | 02-process §6; 04-req FR-17–19 | **H**: gates R-06 | Josh (Q-09), by Mar 2027 | Open |
| A-16 | Store managers have a usable device for counting on the floor | 02-process §6; 04-req NFR-20 | M | Managers (Q-29) | Open |
| A-17 | Courier use falls roughly in proportion to stockouts (target ≈ 2.2/wk) | 02-process §5; 05-exec-02 (25–50% → $5k–$10k) | M | R-01 log + courier invoices | Open |
| A-18 | Process efficiency (VA ÷ cycle time) is < 5% | 02-process §5 | L | Timings (Q-24) | Open |
| A-19 | Delayed entry of emergency orders leaves StockPro stock levels wrong in the meantime | 01-system-map H-06; 02-process P-15; 03-gap G-06 | L | Mei | Open |
| A-20 | Untracked borrowing between stores distorts counts and waste figures | 01-system-map H-13; 03-gap G-12 | L | Store managers | Open |
| A-21 | Any money spent on StockPro could be stranded at end of support | context.md › Risks; 02-process §7; 05-exec-02 | M | Vendor (Q-07) | Open |
| A-22 | Crumb & Co. may accept flexible or seasonal orders | 03-gap SWOT | M | Supplier, via the pastry owner | Open |
| A-23 | Customers who meet stockouts may go to competitors | 03-gap SWOT | L | — (not needed for the case) | Open |
| A-24 | The suggested quantity = par − on hand, rounded up to a pack, never below 0 | 04-req FR-19 | M | Stock-rules owner (Q-33) | Open |
| A-25 | Requirement-level design assumptions: one active order per store per cycle (FR-13); a supply over-commit flag (FR-21); an unsigned-delivery alert (FR-36); a written load-failure fallback (NFR-11); duplicate stockouts counted once (US-31 AC2) | 04-req | L | Mei, during the requirements review | Open |
| A-26 | Staff time savings are capacity released, not cash, unless hours are reduced | 05-exec-02 §4 | M | Tom | Open |
| A-27 | Finance's 18-month payback rule (stated for ongoing costs) is used as the ceiling for one-off spend | 05-exec-01, 02, 04 (≈ $27k–$42k / $40k–$68k) | M | Tom | Open |
| A-28 | Illustration: a second coordinator ≈ 38 h/wk × $34 × 52 ≈ $67k/yr (**not counted** in totals) | 05-exec-02 §4 | M | Tom (Q-40) | Open |
| A-29 | Pastry savings are counted only if pastries are in scope | 05-exec-02 | **H** | Priya (Q-01) | Open |
| A-30 | The exec audience is Priya + Tom now, with a board version later; 8 slides, ~15–20 min | 05-exec-01, 04 | L | Priya (Q-38) | Open |
| A-31 | Other stores work much like Docklands (one manager interviewed; time data from 2) | All outputs; 02-process Q-16 | M | 1–2 more managers (Q-14) | Open |
| A-32 | Customers are walk-in coffee shop customers (no wholesale or catering) | context.md › Company | L | Priya (Q-18) | Open |
| A-33 | Ownership assumptions: orders@ and StockPro are owned by the warehouse; pickers and driver report to Mei; shift leads report to store managers | 01-system-map C-04, C-08–C-11 | L | Priya (Q-06) | Open |
| A-34 | The driver, van and 2 routes can handle 17 stores | 01-system-map C-10; 02-process T-11 | M | Mei, driver (Q-22) | Open |
| A-35 | Stakeholder attitudes: Priya is a champion; Tom is supportive but sceptical; Daniel is positive | context.md; 06-analyst-03 | M | Priya (Q-15) | Open |
| A-36 | Warehouse purchasing is in scope because it is closely linked | context.md › Scope | L | Priya | Open |
| A-37 | BR-06 (accountability and measures) is an implied business requirement from Tom's concerns | 03-gap TS-5; 04-req BR-06 | M | Priya, Tom (Q-30, Q-35) | Open |
| A-38 | An R-10 decision by ~Sep 2027 leaves enough time for a supported system before Dec 2027 | 03-gap R-10; 04-req BR-07 | M | Vendor, Josh | Open |

**`TBD` values** in the outputs are not assumptions. They are gaps, and each is covered by an open question:

| TBD area | Where | Question |
|---|---|---|
| Manager-time and order-error targets | context.md; BR-04; 03-gap TS-4 | Q-05 |
| One-off costs (template, import, logins, data feed) | 05-exec-01, 02 | Q-37 |
| Lost sales | context.md; BR-01; 05-exec-02 | Q-04 |
| Timings (P-02–P-17, NFR-05, 06, 18, 19, FR-36, US-25) | 02-process §3; 04-req | Q-24 |
| Over-par threshold; suggested-quantity rule | FR-04, FR-19 | Q-33 |
| Uptime; access removal; history retention | NFR-09, 13, 15 | Q-34, Q-11 |
| Expiry / food-safety traceability | NFR-16 | Q-12 |
| Growth beyond 17; new-store set-up time | NFR-07, 08 | Q-22 |
| Owners: TillPoint, stock rules, issues log, pastry order, end to end | C-13, C-20, D-03, R-08 | Q-06, Q-27 |
| Reporting lines; customer segments; past attempts | context.md | Q-06, Q-18, Q-13 |
| StockPro upgrade path and import format | C-08; BR-07 | Q-07, Q-08 |

## 2. Decisions
| ID | Decision | Date | Who decided | Rationale | Alternatives rejected | Affected IDs | Status |
|---|---|---|---|---|---|---|---|
| D-01 | Late-order default: if no order by 10:00 Mon, use last week's order until suggested orders are live, then the suggested order | — | Priya (pending) | Keeps Monday on schedule; removes "text Mei and hope" | Wait for the store; Mei chases | CH-06, T-05, FR-11, FR-12, US-06 | **Pending.** Needed by 31 Jan 2027 |
| D-02 | Substitution rule: approved substitutes per item; a named approver for anything else | — | Mei + Priya (pending) | Stops unannounced swaps (11 in 12 wks) | Status quo ("closest thing") | CH-07, T-09, FR-27, FR-28, US-19 | **Pending.** Timing conflict, see Q-39 |
| D-03 | Owners of the stock rules, the issues log and the pastry standing order (and the end-to-end owner, R-08) | — | Priya (pending) | RC-01, RC-04, RC-05 are ownership gaps | — | CH-10, CH-12, R-05, R-07, R-08, FR-24, FR-55 | **Pending.** Needed by 30 Nov 2026 |
| D-04 | Accountability for stock once signed for at the store | — | Priya + Tom (pending; RACI flags the joint A) | "Nobody is accountable" (Tom) | — | CH-09, T-12, FR-34, FR-55, US-23, US-34 | **Pending.** Needed by 30 Nov 2026 |
| D-05 | Use **$182k recorded waste** as the baseline; ~$250k is an upside to prove with complete logs | 2026-11-12 | BA (proposed; 03-gap next step 5) | Finance will only stand behind $182k; an evidence-first approach for the board | Use $250k; use a midpoint | BR-02, TS-2, 05-exec-01–04 | **Proposed.** Tom to confirm by 30 Nov |
| D-06 | Park electronic invoice matching (R-11, FR-57 Won't) until after R-10 | 2026-11-12 | BA (proposed) | Any link to an end-of-support system may be wasted | Build it now | R-11, FR-57, SR-21, G-09 | Proposed |
| D-07 | Dairy ordering is not in this release (FR-58 Won't) | 2026-11-12 | BA (proposed) | No problems reported; scope `TBD` | Include | FR-58, C-19, H-25 | Proposed; depends on Q-01 |
| D-08 | No new core system before the R-10 decision; reuse the StockPro import and the TillPoint export | 2026-11-12 | BA (proposed) | Budget, IT capacity, end of support, the adoption concern | Buy a stock-ordering SaaS now | NFR-23, 02-process §7, R-04, R-06 | Proposed |
| D-09 | R-10 is "decide now, spend later" (likely FY2027–28) | 2026-11-12 | BA (proposed) | Likely to exceed $60k; must not collide with the July openings | Replace StockPro in Feb–Jun 2027 | R-10, BR-07, FR-59, A-08 | Proposed |
| D-10 | Weekly replenishment is the first process mapped; pastry ordering may need its own map | 2026-11-12 | BA | It carries most 🟠/🔴 handoffs (system map) | Map pastries first | 02-process; Q-01 | Done (method) |
| D-11 | Business case options: 0 Do nothing / 1 Quick wins / 2 Full staged. **Option 2 recommended**, with the R-06 step behind a March 2027 go/no-go | 2026-11-12 | BA (proposed) | Option 1 delivers most cash; Option 2 makes the stockout and manager-time goals hold at 17 stores | Big-bang Option 2 | 05-exec-02; R-01–R-09 | Proposed; Priya and Tom to decide |
| D-12 | All analysis was produced in `--no-questions` mode from inputs only; outputs are Draft (unvalidated) | 2026-11-12 | BA / user | Practice case | — | All outputs | Done |
| D-13 | The consolidated Q-IDs in this register supersede the local Q-numbers in outputs 01–04 | 2026-11-12 | BA | Local numbering collides (e.g. five different "Q-05"s) | Renumber the source files | All Q- references in 05/06 | Done |

## 3. Open questions (consolidated)
All are *(not asked — --no-questions)*. "Needed by" is set from the decision or roadmap item each one gates.

| ID | Question | Raised in | Ask | Needed by | Status |
|---|---|---|---|---|---|
| Q-01 | Are pastries (Crumb & Co.) and dairy (Valley Dairy) in scope? | ctx#1; SM Q-09; GAP Q-03; REQ Q-06 | Priya | **30 Nov 2026** | Open |
| Q-02 | Are waste recording (beyond completeness) and invoice matching in scope? | context.md › Scope; REQ Q-07 | Priya, Tom | 31 Jan 2027 | Open |
| Q-03 | Which waste baseline will leadership use ($182k or ~$250k)? Can unrecorded waste be sampled? | ctx#3; REQ Q-18 | Priya + Tom | **30 Nov 2026** | Open (D-05 proposed) |
| Q-04 | Can lost sales be estimated (e.g. from till sales dips on stockout days)? | ctx#4; REQ FR-51 | Tom | Mar 2027 | Open |
| Q-05 | What targets do you want for manager ordering time and for order errors? | ctx#5; GAP Q-02; REQ Q-08 | Priya | 31 Jan 2027 | Open |
| Q-06 | What are the reporting lines? Who could be the end-to-end owner? Who owns TillPoint? | ctx#6; SM Q-02; GAP Q-13; GAP Q-09; REQ Q-05 | Priya | 30 Nov 2026 | Open |
| Q-07 | What upgrade path and cost does the StockPro vendor offer before Dec 2027? | ctx#7; SM Q-05; GAP Q-15; REQ Q-04 | Mei, Josh, vendor | 31 Jan 2027 | Open |
| Q-08 | What file format does StockPro's import accept? Can it export available stock daily? | SM Q-05; PR Q-10; GAP Q-07; REQ Q-04 | Mei, Josh, vendor | **31 Jan 2027** | Open |
| Q-09 | Can TillPoint products be matched to stock items? | PR Q-11; GAP Q-09; REQ Q-05 | Josh, Tom | Mar 2027 | Open |
| Q-10 | How much of Josh's time is available Feb–Jun 2027? What monthly support effort is acceptable? | GAP Q-14; REQ Q-15 | Josh, Priya | 31 Jan 2027 | Open |
| Q-11 | Are there mandated or banned tools or security policies (shared logins, SaaS, personal phones)? How fast must leavers' access be removed? How long should history be kept? Any privacy rules? | ctx#8; SM Q-04; REQ Q-13 | Josh, Tom | 31 Jan 2027 | Open |
| Q-12 | Are there food-safety or expiry-tracking rules for stock? | ctx#9; PR Q-09; REQ Q-14 | Priya | 31 Jan 2027 | Open |
| Q-13 | Has a past change project failed here? What has already been tried for stockouts or waste? | ctx#10; ctx#12 | Priya, Tom, Mei | 30 Nov 2026 | Open |
| Q-14 | How do other stores differ from Docklands? Who was the second manager in the time data? | ctx#11; SM Q-03; PR Q-16 | 1–2 more store managers | 31 Jan 2027 | Open |
| Q-15 | How do Mei, the pickers, Josh and the other managers feel about the change, and how do they prefer to be engaged? | ctx#13 | Priya | 30 Nov 2026 | Open |
| Q-16 | Who is accountable for stock once it reaches a store (D-04)? Does that person have authority over par levels? | ctx#14; SM Q-10; GAP Q-05; REQ Q-03 | Priya + Tom | **30 Nov 2026** | Open |
| Q-17 | Can we get samples: a TillPoint CSV, a StockPro reorder-point export, 2–3 store Excel files? | ctx#15; SM Q-12; GAP Q-08 | Mei, Josh | 15 Dec 2026 | Open |
| Q-18 | What are the customer segments (any wholesale or catering)? | ctx#16 | Priya | — | Open |
| Q-19 | Is anything missing from the system map or the process steps (put-away, complaint fixes, short with no substitute)? | SM Q-01; PR Q-01 | Mei, Daniel | 15 Dec 2026 | Open |
| Q-20 | If Mei were away for a month, what would break? Who will be the backup, and when can they be trained? | SM Q-06; REQ Q-20 | Priya, Mei | 30 Nov 2026 | Open |
| Q-21 | How often do suppliers short-ship, and which ones? Who approves substitutions today (D-02)? | SM Q-07; PR Q-07; GAP Q-11; REQ Q-02 | Mei, a picker, Priya | 31 Jan 2027 | Open |
| Q-22 | Can pickers, the van and 2 routes handle 17 stores? Growth beyond 17? How fast must a new store be set up? | SM Q-08; PR Q-17; GAP Q-12; REQ Q-16 | Mei, driver, Priya | Mar 2027 | Open |
| Q-23 | How are invoice-matching errors found, and how often do they occur? | SM Q-11 | Accounts assistant | After R-10 | Open (low priority) |
| Q-24 | Timings: touch and wait times (P-02–P-17), the emergency path, NFR-05/06/18/19, overdue thresholds | PR Q-02, Q-03, Q-04, Q-06, Q-08; REQ Q-10 | Mei, Daniel, a picker, the driver, a shift lead | 31 Jan 2027 | Open |
| Q-25 | Of the 31 order errors, how many come from re-keying vs picking vs the store's own order? | PR Q-05; GAP Q-06 | Mei; complaint emails | 31 Jan 2027 | Open |
| Q-26 | D-01: what is the late-order default, and which order stands if the store submits late? | PR Q-12; REQ Q-01 | Priya | 31 Jan 2027 | Open |
| Q-27 | D-03: who owns the stock rules, the issues log and the pastry order? Who is the end-to-end owner? | PR Q-13; REQ Q-03 | Priya | **30 Nov 2026** | Open |
| Q-28 | Once Monday re-keying is gone, could deliveries move a day earlier? | PR Q-14 | Mei, driver | Mar 2027 | Open |
| Q-29 | How do managers react to the proposed changes? Is the store laptop usable for counting on the floor? | PR Q-15; REQ Q-11 | Daniel + 1–2 managers | 31 Jan 2027 | Open |
| Q-30 | Are the target state (TS-1 to TS-5) and the five priority problems right? | GAP Q-01, Q-04 | Priya, Tom | 30 Nov 2026 | Open |
| Q-31 | How do stores handle syrup expiry and rotation? | GAP Q-10 | Store managers | 31 Jan 2027 | Open |
| Q-32 | What are managers praised or measured for? Does it reward over-ordering? | GAP Q-16 | Priya, managers | 31 Jan 2027 | Open |
| Q-33 | What over-par multiple should trigger a flag? Is the suggested-quantity rule right (seasonality, in-transit stock)? | REQ Q-09, Q-17 | Stock-rules owner, Mei | 31 Jan 2027 | Open |
| Q-34 | What availability hours and uptime are needed for ordering and the issues log? | REQ Q-12 | Priya, Josh | 31 Jan 2027 | Open |
| Q-35 | Do you agree the Must list (59%), BR-06 and BR-07, and the handling of the stakeholder conflicts? | REQ Q-18 | Priya, Tom | BRD sign-off | Open |
| Q-36 | Do any staff need accessibility support? | REQ Q-19 | Priya, managers | 31 Jan 2027 | Open |
| Q-37 | What do the one-off items cost (template build, import set-up, logins, data feed)? What is the accounts assistant's rate? | 05-exec-01, 02 | Josh, vendor, Tom | **31 Jan 2027** | Open |
| Q-38 | Who is in the exec meeting, when, how long, and in what format? Is a separate board version needed? What is the exact due date? | ctx#2; 05-exec-01, 04 | Priya | 20 Nov 2026 | Open |
| Q-39 | **Source conflict:** 02-process §7 puts the substitution rule (CH-07) in Phase 0, before 30 Nov. 03-gap §6 puts "R-02 rules agreed" during the freeze. The exec pack uses *during the freeze*. Which is right? | 02-process; 03-gap; 05-exec-03 | Priya, Mei | 30 Nov 2026 | Open |
| Q-40 | What would a second coordinator cost (hours, loaded rate, on-costs)? | 05-exec-02 | Tom | 30 Nov 2026 | Open |
| Q-41 | Who is the analyst pack for: a new BA, a handover, or a review? | ba-docs step 2 | User | — | Open |
| Q-42 | Are there decisions or assumptions not yet in the files that should be recorded? | ba-docs step 2 | User | — | Open |
| Q-43 | Have any outputs been reviewed with stakeholders? Who signs off the BRD? | ba-docs step 2 | User, Priya | — | Open |

**Deduplication:** 81 local questions (ctx 16, SM 12, PR 17, GAP 16, REQ 20) were merged into Q-01 to Q-36. Q-37 to Q-43 are new from the doc packs.

---

## Open questions
See §3. The most urgent are the five due **30 Nov 2026**: Q-01, Q-03, Q-16, Q-27 and Q-39. A-05 also needs confirming by then.

## Next steps
1. Take the 30 Nov items to Priya and Tom, and update the statuses here the same day.
2. After each validation session, mark assumptions as Confirmed or Rejected and add a dated line to the change history below.
3. Point every new output at these consolidated Q-IDs.

**Change history**
| Date | Change | By |
|---|---|---|
| 2026-11-12 | Register created. A-09 to A-38 added; D-05 to D-13 recorded; 81 local questions consolidated into Q-01 to Q-36; Q-37 to Q-43 added | BA |

## Technique notes
- **RAID-style logs.** Assumption and decision logs (RAID logs: Risks, Assumptions, Issues, Dependencies) protect the BA when stakeholders later ask "why did we do it this way?". Recording *rejected alternatives* is what makes a decision log useful a year later.
- **Assumptions vs TBDs.** An assumption is a belief you are acting on. A TBD is a gap you are *not* acting on yet. Keeping them separate stops gaps from quietly turning into "facts".
- **Deduplicating questions.** The same question asked in five documents gets five answers, or none. One consolidated list, with an owner and a date, is what turns questions into progress.
