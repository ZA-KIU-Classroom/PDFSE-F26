# Gate reconcile block

**Paste everything below the line at the bottom of:** `03-build/analytics/event-schema.md`
**Filled-in example:** `Lab-7/examples/event-schema.md` (Sakhli)

Two edits to that file, both in Lab 7. First, add a `Live` column to your Events table and write `yes` beside an event only after one teammate did the action on a phone at the production URL and a second teammate saw the row in PostHog Activity. Second, paste this block under your Reconcile plan and fill it.

---

## Gate reconcile (Lab 7)

**Production URL walked:** [the URL] · **walked by:** [initials of a teammate who did not build the north star step] · on a phone, mobile data: [yes or no]

| Source | Count | Window | Exactly how it was counted |
|---|---|---|---|
| PostHog | | [same start and end as the row below] | Trends insight, total count of `[north star event, pasted]` |
| Database | | | `[the query you ran, pasted]` |

**Match:** [yes or no]

**If no, first:** what the two numbers were, what caused the gap, what you changed (commit link), and the two numbers after the fix. Keep the wrong numbers here; do not overwrite them.

**Silent failure we predicted in Lab 5:** [copy the line from your Reconcile plan] · **Did it happen?** [yes or no, and how you know]

**Internal filter set in PostHog:** [the exact filter, for example `host_id is not h_test` and `Host does not contain localhost`] · **our test record is:** [the id your team tests on]

**Checked by:** [initials] · **events still not Live, with owner and by when:** [list, or none]
