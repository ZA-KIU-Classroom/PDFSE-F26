# Lab 7: Ship Week (the gate)

## What you leave this lab with

Four things, at exactly these paths.

| # | What | Where | Starts from |
|---|---|---|---|
| 1 | Live product and Analytics dashboard links | The table in your team `README.md` | Rows already there |
| 2 | A `Live` column on every event, and gate reconcile numbers | `03-build/analytics/event-schema.md` | `templates/gate-reconcile-block.md` |
| 3 | Sprint 2: Sprint 1 review, missing rungs, field-week people, prediction | `03-build/sprints/sprint-2.md` | `templates/sprint-2.md` |
| 4 | One decision: where you stand on the gate | Bottom of `DECISIONS.md` | Last section of `templates/sprint-2.md` |

`examples/` holds Sakhli's version of each.

## The gate is a ladder

| Rung | You are here when |
|---|---|
| 1 | Your production URL loads on a phone on mobile data |
| 2 | The journey completes there, through your north star step |
| 3 | Your north star event shows in PostHog Activity, fired from production |
| 4 | The PostHog count equals your database count, both written down |
| 5 | A dashboard with your north star trend exists, link in your README |

Start on your own rung and climb in order; never skip one. All five are due before Lab 8.

## Before you arrive

Watch-check submitted. Working logins: GitHub, host, database, PostHog. Schema and Sprint 1 plan open. A phone.

## 0:00 to 0:15. Your rung

Every team types its production URL or `none`, and its rung. Two random teams walk their journey on screen.

## 0:15 to 0:35. Live demo

I walk a volunteer team's product cold, Activity beside it, then reconcile one count and build one tile.

## 0:35 to 1:00. Checkpoint 1: the walk (rungs 1 to 3)

Rung 0? Deploy first: `Lab-6/setup/SHIP-STACK-SETUP.md` steps 1 and 4. One plain page in production is rung 1.

Then the walk. A teammate who did not build it opens the production URL on a phone, Wi-Fi off, and does the journey. A second teammate reads each row in PostHog Activity aloud: name matches the schema, every property present, fired once, from production. Add a `Live` column to your schema; write `yes` beside each event you both saw.

Optional: `resources/walking-your-own-product.md` if the page loads only for you; `resources/reading-events-and-reconciling.md` if a row is missing, doubled, or misnamed.

## 1:00 to 1:15. Checkpoint 2: reconcile and filter (rung 4)

Paste `templates/gate-reconcile-block.md` at the bottom of your schema. Count your north star event in PostHog and the matching rows in your database, same window. Write both. Different? Find why, fix, recount. Set PostHog's internal-user filter so your own clicks stop counting. Commit.

## 1:15 to 1:35. Checkpoint 3: the dashboard (rung 5)

New dashboard, three insights: Trends on your north star event; your journey steps in order (Funnels if one person does every step, step counts if two do); Retention on your north star event. Internal filter on each. Share it as a link that opens without a login, pasted into your README's Analytics dashboard row. Commit.

Optional: `resources/three-tile-dashboard.md` if a tile is empty; `resources/identify-properties-and-privacy.md` if every user shows as one person.

## 1:35 to 1:50. Checkpoint 4: Sprint 2 and the gate line

Everyone stops climbing. Copy `templates/sprint-2.md` to `03-build/sprints/sprint-2.md`. Review Sprint 1 against your definition of done. Each missing rung gets an owner and a time. Name 3 to 5 real people from your logs and how the link reaches each. Write your prediction and its "we are wrong if" line. Gate line in DECISIONS.md. Commit.

Optional: `resources/running-a-field-week.md`, for who to ask.

## 1:50 to 2:00. Homework, read aloud

**Deliverable:** TEAM GATE (no points, required): your live URL and PostHog dashboard link in your README, your north star event firing from the live URL, reconcile numbers in `03-build/analytics/event-schema.md`, and `03-build/sprints/sprint-2.md`. HOMEWORK 2 (individual, 5 pts): `members/<github-username>/hw2.md`, started from `Lab-7/templates/hw2.md`: your ship report (what you personally built and deployed, with commit links), your pattern journal for Weeks 5 to 7, and your DECISIONS.md citations.

**Deadline:** Both before your Lab 8 (exact time in the Teams announcement).

**Submission:** Gate: commit to your team repo, then post your live URL and dashboard link in your lab group's Teams channel. HW2: commit the file from your own account, then submit through the HW2 link posted on Teams; every student submits their own. Both, or it is not submitted.

**Points:** Homework 2: 5 (individual). The gate is the precondition for Milestone 2 (10 pts).

This week is your field test. Put the live URL in front of the 3 to 5 real people named in your Sprint 2 file; Lab 8 opens by reading what they did, against the prediction you wrote today. The watch-check for the next session is due before Lab 8.
