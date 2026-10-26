# Lab 6 Homework

**Deliverable:** `03-build/mvp-boundary.md` (journey, cut list, event mapping), architecture sketch, Sprint 1 plan. Begin building the journey.

**Deadline:** Before your Week 7 lab. Week 7 is the ship week: arrive with the journey partially working.

**Submission:** Commit to your team repo.

**Points:** Feeds Milestone 2 (10 pts, Week 11). HOMEWORK 2 (5 pts, individual) is due end of Week 7: it includes your ship report, so the more you ship this week, the easier it writes.

The Week 7 lab ends with a hard gate: deployed and instrumented before the exam break. Teams that arrive with nothing running will spend the lab catching up instead of shipping.

Catch-up, if it applies to you: your prototype track is a DECISIONS.md line, and three test sessions are logged in `02-design/user-testing/usability-findings.md` before the Week 7 lab, on whichever prototype your track names.

## Where each thing goes

| What | Path |
|---|---|
| MVP boundary | `03-build/mvp-boundary.md` (made in the lab; keep the cut list current as you build) |
| Architecture | `03-build/architecture/architecture.md` (made in the lab) |
| Sprint 1 plan | `03-build/sprints/sprint-1.md` (made in the lab; move stories across the board as they land) |
| Code | `app/` in your team repo, merged to `main` every day you work |
| Each test session | One block in `02-design/user-testing/usability-findings.md` (template and Sakhli example in `Lab-5/`) |
| Each story that lands | Nothing new to write: the commit, the deploy, and the reviewer's walk are the evidence |

## Building the journey this week

Build vertically. Each working day ends with the journey one step longer, not one screen prettier. Start with the story that fires your north star event. The stack, from empty folder to a public URL with events in PostHog, is `Lab-6/setup/SHIP-STACK-SETUP.md`: about 90 minutes, do it this week, not in the Week 7 lab.

The Week 7 lab verifies the gate on the clock. A team that arrives deployed with events firing spends the lab on the dashboard. A team that arrives with a link page spends it building.
