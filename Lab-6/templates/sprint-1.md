# Sprint 1

**Save this file as:** `03-build/sprints/sprint-1.md`
**Filled-in example:** `Lab-6/examples/sprint-1.md` (Sakhli)

Sprint 1 runs from today's lab to the Week 7 lab and ends at the gate: deployed at a public URL, north star event firing in PostHog. Everything here is sized to the hours you actually have.

## Definition of done

[One sentence, from the Week 6 session. It names where the code lives, where it runs, who checks it, and how you see it was used.]

## Real hours before the Week 7 lab

| Initials | Hours free | When, specifically |
|---|---|---|
| | | |
| | | |
| | | |
| **Total** | | |

## The board

Where it lives: [GitHub Projects on your repo, a Trello board, or a pinned message; link it]. Four columns: next, doing, review, done. One card per story below. Merge to `main` every day you work.

## Stories

One story per journey step, north star step first, the deploy last. One owner. A different reviewer, who walks the story on a phone at the deployed URL. Hours are the owner's estimate; the sum must not exceed the total above.

### S1 · [journey step] · owner [initials] · reviewer [initials] · [N] h

**As** [the person from your ICP], **I** [do this one step] **so that** [the value from your problem statement].

**Acceptance criteria** (each one checkable on a phone by the reviewer, no adjectives):
- Given [starting state], when [the action], then [what is visible on screen]
- And [what exists in the database, or what is now impossible]
- And `[event_name]` fires with [the properties from the schema]

**Smallest demo that proves it:** [what you would do on screen in 30 seconds]

### S2 to S[N-1] · one block per remaining journey step, same shape as S1

### S[N] · Deploy and instrument · owner [initials] · reviewer [initials] · [N] h

Do this story first, on the first evening, with `Lab-6/setup/SHIP-STACK-SETUP.md`, so every later story deploys the day it merges. Public URL in the README's Live product row, every schema event visible in PostHog's Activity view, reconcile check written. The Week 7 lab adds the dashboard.

## Slip rule

Written now, obeyed later. If [the story most likely to overrun] is not done by [the evening before the Week 7 lab], then [the exact part that moves to Sprint 2] moves, and [the part that stays no matter what, because the value does not land without it] stays.

## The DECISIONS.md lines

The boundary line is in `03-build/mvp-boundary.md`. If your prototype was not built before this lab, add one of these two lines to `DECISIONS.md` as well:

`Wk6 · Prototype track: clickable v1 generated from 02-design/prototype-plan.md tonight; frozen test runs on it, 3 sessions before the Week 7 lab · evidence: 02-design/prototype-plan.md · owner: [initials]`

`Wk6 · Prototype track: the first deployed screen of the journey is the prototype; frozen test from 02-design/user-testing/test-plan.md runs on it, 3 sessions before the Week 7 lab · evidence: 03-build/sprints/sprint-1.md S1 · owner: [initials]`
