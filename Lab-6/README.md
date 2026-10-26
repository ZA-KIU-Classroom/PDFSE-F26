# Lab 6: MVP Boundary and Sprint 1

## What you leave this lab with

Five things in your team repo, at exactly these paths. Nothing else today.

| # | What | Where | Starts from |
|---|---|---|---|
| 1 | MVP boundary: journey, cut list, event mapping | `03-build/mvp-boundary.md` | `templates/mvp-boundary.md` |
| 2 | Architecture: one diagram, one line of why per layer | `03-build/architecture/architecture.md` | `templates/architecture.md` |
| 3 | Sprint 1 plan: definition of done, stories, owners, hours, slip rule | `03-build/sprints/sprint-1.md` | `templates/sprint-1.md` |
| 4 | New schema rows for any step that had no event | `03-build/analytics/event-schema.md` | Your Lab 5 file |
| 5 | Two decisions: the boundary, and your prototype track | Bottom of `DECISIONS.md` | Line shape at the bottom of each template |

Templates name their destination at the top; `examples/` holds a Sakhli version of each. Copy the shape, not the content.

## Before you arrive

Your feature list and three cuts from the Week 6 session. Your event schema open. Your real hours before the Week 7 lab, per teammate. Watch-check submitted. No prototype? Come.

## 0:00 to 0:20. Where you actually are

Every team types one chat line: prototype link or `none`, sessions run out of 5, north star sentence. That sorts you:

- **Track A:** prototype, 3+ sessions. Normal lab.
- **Track B:** prototype, under 3 sessions. Sessions get booked in the studio block.
- **Track C:** no prototype. In the studio block you pick a route, written as a DECISIONS.md line (shape at the bottom of `templates/sprint-1.md`).

Then two random teams read their north star aloud; the room attacks it with the Week 5 tests. Defend or change it; a change is a DECISIONS.md line.

## 0:20 to 0:35. Live demo

I cut a volunteer team's feature list to a journey in ten minutes, narrating every cut. Every reason points at logs or the hypothesis, never difficulty.

## 0:35 to 0:55. Checkpoint 1: the boundary

Copy `templates/mvp-boundary.md` to `03-build/mvp-boundary.md`. Value hypothesis at the top. Journey: five to seven numbered steps, who does what. Cut list: every feature you did not keep, a reason, when it comes back. Mapping: each step beside its event name, copied from the schema. A step with no event: add it to `03-build/analytics/event-schema.md` in the same commit, or cut the step. Boundary line in DECISIONS.md. Commit.

Optional: `resources/drawing-the-mvp-boundary.md` if the journey will not fit on one slide or a reason says "too hard"; `resources/mapping-steps-to-events.md` if torn between add and cut.

## 0:55 to 1:20. Checkpoint 2: architecture

Copy `templates/architecture.md` to `03-build/architecture/architecture.md`. A diagram of the journey's path through your system: phone, app, database, analytics, anything that sends messages. One line per layer: what you chose, and why you can deploy it by Week 7; "a teammate has deployed this before" is the best reason. Name where secrets live; confirm `.env` is in `.gitignore`. Commit.

Optional, if the team cannot agree on a stack: `resources/choosing-a-stack-you-can-deploy.md`. To stand the stack up tonight, step by step: `setup/SHIP-STACK-SETUP.md`.

## 1:20 to 1:45. Checkpoint 3: Sprint 1

Copy `templates/sprint-1.md` to `03-build/sprints/sprint-1.md`. Definition of done at the top. Honest hours per teammate, totaled. One story per journey step, north star step first: criteria a teammate can check on a phone, the event it fires, one owner, one reviewer, hours. The deploy is its own story. Story hours never exceed the total. Slip rule. Commit.

Optional: `resources/stories-and-acceptance-criteria.md` if a criterion cannot fail; `resources/sizing-sprint-1-to-real-hours.md` if the hours do not fit.

## 1:45 to 1:50. Studio

Track A: start `setup/SHIP-STACK-SETUP.md` step 1. Track B: message the testers you owe. Track C: choose your route and write its DECISIONS.md line: the clickable v1 generated tonight from your Lab 5 plan, or the first deployed screen of your journey as the prototype, with the frozen test run on it. Either way: three sessions before the Week 7 lab.

Board and daily merges, tonight: `optional-deep-dive/process-for-pods.md`.

## 1:50 to 2:00. Homework, read aloud

**Deliverable:** `03-build/mvp-boundary.md` (journey, cut list, event mapping), architecture sketch, Sprint 1 plan. Begin building the journey.

**Deadline:** Before your Week 7 lab. Week 7 is the ship week: arrive with the journey partially working.

**Submission:** Commit to your team repo.

**Points:** Feeds Milestone 2 (10 pts, Week 11). HOMEWORK 2 (5 pts, individual) is due end of Week 7: it includes your ship report, so the more you ship this week, the easier it writes.

The Week 7 lab ends with a hard gate: deployed and instrumented before the exam break. Teams that arrive with nothing running will spend the lab catching up instead of shipping.

Catch-up, if it applies to you: your prototype track is a DECISIONS.md line, and three test sessions are logged in `02-design/user-testing/usability-findings.md` before the Week 7 lab, on whichever prototype your track names.
