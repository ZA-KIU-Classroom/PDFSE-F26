# Milestone 2: Quality Audit · self-grading checklist

**10 points, team. Due after Lab 9 (exact time in the Teams announcement).**

**To submit:** push the tag `m2-quality` to your team repo, then fill in the M2 form posted on Teams. Both, or it is not submitted.

```bash
git tag m2-quality
git push origin m2-quality
```

**Precondition:** the gate from Lab 7. No live product, no audit.

Grade yourselves before you tag: one teammate reads each row aloud, another says present or absent.

| # | What | Where | Present when | Common fail | Pts |
|---|---|---|---|---|---|
| 1 | Live product | Live product row of your `README.md` | The link loads on a phone and the journey completes through your north star step | A preview link; a journey that stops one step early | 1 |
| 2 | Dashboard | Analytics dashboard row of your `README.md` | Opens without a login; north star event firing on data from people who are not your team | Internal filter off, so the numbers are your own clicks | 1 |
| 3 | Event schema | `03-build/analytics/event-schema.md` | Every event marked `Live` exists in PostHog under that exact name | An event in the file that never fired | 1 |
| 4 | Eval set and results | `03-build/evals/eval-set.md`, `03-build/evals/results/` | 20 or more cases for your AI feature; at least one check decided by code and one judged; at least one failure caught and written up, or an argued case for why none was found | Cases invented at a desk; three judged checks and no code check; a judged column that never fails and was never spot-checked | 2 |
| 5 | SLO sheet | `03-build/reliability/slo-sheet.md` | One promise in your user's words, the event and property that measure it, a target with a window | "Fast and reliable"; a target with no way to measure it | 1 |
| 6 | Privacy notice and consent | `07-legal/privacy-notice.md`, and the line on your page | The notice lists what you hold, why, where, and who sees it, and matches your table columns and event properties; the consent line is live on the page | A notice that describes the product you meant to build | 1 |
| 7 | Pivot or persevere | Bottom of `DECISIONS.md` | One line: persevere, pivot the roadmap, or pivot the product, linked to your readout and experiment | A line that could have been written before the field week | 1 |
| 8 | Quality band | The whole submission | 0: audit theatre, files that exist to exist. 1: honest but shallow. 2: the eval set or the SLO would survive an engineer's scrutiny at a real company | | 2 |

Rows 1 to 3 you earned at the gate; check they still hold. Rows 4 to 6 are the Week 9 session and Lab 9. Row 7 is your Lab 8 readout, grown up.

Individual grades may be adjusted on documented non-contribution; any member may be asked about any row.
