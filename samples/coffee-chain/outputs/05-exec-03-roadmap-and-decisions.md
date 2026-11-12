# Roadmap and decisions needed: Stock ordering

**Harbour Lane Coffee Co.** · **Date:** 12 Nov 2026 · **Prepared by:** Business Analyst, stock ordering review
**For decision:** five decisions by 30 Nov 2026 and three more by Jan–Mar 2027 (table below).

*Draft. The dates work around the 1 Dec – 31 Jan change freeze and the July 2027 store openings.*

---

## 1. Roadmap

**Now: mid-Nov 2026 to mid-Feb 2027.** Only rules, logging and role changes during the freeze.
- **By 30 Nov:**
  - Name the owners.
  - Put the shared log for stockouts, emergency orders and wrong deliveries live.
  - Give every warehouse user their own login.
  - Start writing down the coordinator's routines.
- **During the freeze:**
  - Agree the substitution and delivery rules.
  - Review winter pastry orders, if pastries are in scope.
  - Train a backup coordinator.
  - Ask the warehouse system vendor for its upgrade path and import format.
- *Expected result:* a measured baseline, no repeat of August, and the first pastry savings.

**Next: mid-Feb to mid-May 2027**
- **One order form for all stores**, loaded straight into the warehouse system. Pilot in 2 stores in February and roll out to all 12 by March.
- **A "what's coming" list** sent to each store before delivery, and a quick sign-off when the delivery arrives.
- **Stock levels reset** from recent sales, with a monthly review.
- **A monthly scorecard** from March, plus the **go/no-go check** for sales-based ordering.
- *Expected result:* retyping stops, exceptions are handled by rule, and stock rules are up to date.

**Later: mid-May 2027 onwards**
- **Till sales suggest order quantities** and warehouse stock is visible, live before the July openings. Stores 13–17 start on the new process from day one.
- **Decide whether to upgrade or replace the warehouse system** (~Sep 2027), with a supported system in place before Dec 2027.
- **Automate invoice matching** after that decision, not before.
- *Expected result:* 17 stores ordering with one coordinator, on a supported system.

## 2. How we'll measure success
- **Core-item stockouts:** about 4.5 a week (reported) → **2.25 or fewer** a week. *Check:* trending down by mid-May 2027, and holding through summer 2027.
- **Recorded waste:** ≈ $182k a year → **$146k–$164k** (10–20% lower). *Check:* all stores logging by mid-Feb 2027, then measured over FY2027–28.
- **Coordinator retyping:** 6–8 h a week → **under 1 h**. *Check:* after the March rollout.
- **Unannounced substitutions:** about 1 a week → **0**. *Check:* from the February go-live of the "what's coming" list.
- **Continuity:** the backup runs a full ordering week unaided in a test. The coordinator headcount **stays at 1 at 17 stores**. *Check:* backup test by mid-Feb 2027, headcount by July 2027.

*Early warning: reported stockouts will **rise** in the first weeks of logging, because under-reporting stops. That is expected.*[^1]

## 3. Decisions needed

| # | Decision | Options | Recommended | Needed by | If delayed |
|---|---|---|---|---|---|
| 1 | Who owns stock ordering end to end, and who owns the stock rules | Name a role for each / leave as today | Name one role for each now | **30 Nov 2026** | Stock levels stay stale, and nobody runs the log or the March check |
| 2 | Who is accountable for stock once it reaches a store | Store / warehouse until checked / undecided | Accountability passes to the store at delivery sign-off *(BA proposal)* | **30 Nov 2026** | "Nobody is accountable" continues, and the sign-off has no meaning |
| 3 | Allow logging, rules and role changes during the Dec–Jan freeze | Yes / No | Yes: low risk, no system changes | **30 Nov 2026** | The baseline starts in Feb, and evidence for the board slips to spring |
| 4 | Are pastry orders part of this work? | Yes / No / Later | Yes: the largest waste item (≈ $96k) | **30 Nov 2026** | The winter review is missed, and ≈ $14k–$19k a year of savings is deferred |
| 5 | Which waste figure we use | $182k recorded / ~$250k estimated | $182k, with $250k as an upside to prove through complete logs | **30 Nov 2026** | Disagreement on the numbers in front of the board |
| 6 | Who approves substitutions that aren't on the approved list | Coordinator / Operations Director / duty manager | Coordinator, with the Operations Director as backup *(BA proposal)* | 31 Jan 2027 | Pickers keep substituting "the closest thing" unannounced |
| 7 | What happens when a store misses the Monday 10am order deadline | Last week's order / suggested order / wait | Last week's order until sales-based suggestions are live | 31 Jan 2027 | Late orders still rely on "text the coordinator and hope" |
| 8 | Approve first-wave spend (order form, import, logins) within $60k | Yes / Partial / No | Yes, subject to quotes and the 18-month payback | 31 Jan 2027 | The February pilot slips, leaving less time before July |
| 9 | Go/no-go for sales-based ordering | Go / Delay / Stop | Go, if the import, item matching and IT time checks pass | Mar 2027 | Not ready for stores 13–17 in July |

## 4. Risks to watch
| Risk | Owner |
|---|---|
| The warehouse system's import can't take store orders, so the order-form benefits slip | Mei Chen / Josh. Answer by 31 Jan 2027 |
| IT capacity: one generalist for Feb–Jun | Priya Nair. Confirm Josh's time by 31 Jan 2027 |
| Adoption: stores drift back to their own spreadsheets and chat | End-to-end owner (decision 1). Track 12/12 stores using the form for 4 weeks in a row |

---
**Next steps**
| What | Owner | By |
|---|---|---|
| Decisions 1–5 | Priya Nair (decision 2 with Tom Reyes) | 30 Nov 2026 |
| Decisions 6–8 | Priya Nair / Mei Chen / Tom Reyes | 31 Jan 2027 |
| Decision 9: March checkpoint pack | BA, with Josh | Mar 2027 |

**Open questions that affect these decisions** *(not asked — --no-questions)*:
- Does "no big changes" in the freeze allow logging and rule changes?
- The two earlier analyses put the substitution rule at different times: before 30 Nov or during the freeze. This roadmap uses *during the freeze*.[^2]

---
[^1]: KPIs from outputs/03-gap §5–6 (R-01, R-02, R-03, R-04, R-05) and outputs/04-requirements BR-01 to BR-05.
[^2]: Decisions map to: 1 → R-08, D-03 · 2 → D-04 · 3 → A-05 · 4 → Q-01 · 5 → D-05 · 6 → D-02 · 7 → D-01 · 8 → R-04, R-03 (logins) · 9 → R-06. Timing conflict: register Q-39 (02-process §7 Phase 0 vs 03-gap §6 Now).
