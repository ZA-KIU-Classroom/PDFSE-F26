# Lab 5: Prototype Build and North Star

## What you leave this lab with

Five things in your team repo, at exactly these paths. Nothing else is produced today.

| # | What | Where | Starts from |
|---|---|---|---|
| 1 | Prototype v1, live and clickable | The **Prototype** row of your team `README.md` table: replace "coming Week 5" with the link | Your `02-design/prototype-plan.md` |
| 2 | Event schema with your north star | `03-build/analytics/event-schema.md` | `templates/event-schema.md` |
| 3 | Test plan with five named testers | `02-design/user-testing/test-plan.md` | `templates/test-plan.md` |
| 4 | Your north star decision | One new line at the bottom of `DECISIONS.md` | `templates/north-star-worksheet.md` (a worksheet; only its last line goes in your repo) |
| 5 | The prototyping tool you used | One new line in `docs/ai-usage-log.md` | The format already in that file |

Each template says at the top where its file goes. Each has a finished Sakhli version in `examples/` with the same name. Copy the shape, never the content.

## Before you arrive

Your `02-design/prototype-plan.md` committed and open. An account on the AI prototyping tool your team chose, created before the lab, not during it. Your north star draft from the Week 5 session. The Week 5 watch-check submitted.

## 0:00 to 0:15. Recap and two demos

Two students picked at random screen-share their team's `02-design/prototype-plan.md` for two minutes each, sections 4 and 5: the "will not appear" list and the test. Not a presentation; show the file.

## 0:15 to 0:35. Live demo

I user-test a volunteer team's prototype cold, thinking aloud, with a stopwatch, the way Sakhli tested with Oni-1. I have not seen it before. The team reads me their task word for word and then says nothing. Afterwards we score it against their own rule from section 5.

## 0:35 to 1:05. Checkpoint 1: build v1

Open your prototype plan. Paste your problem statement into the tool, then prompt for exactly the screens in your screen table and name everything that must not appear (the Week 4 prompt shape). When the tool finishes, check every screen against the plan before anyone else sees it: a screen that is not in your table gets deleted, and the delete is a DECISIONS.md line if it was a real feature.

Open the prototype on a phone, not a laptop. Walk the one action once yourself. Then put the link in the Prototype row of your team README and add one line to `docs/ai-usage-log.md`: week, who, tool, what it produced, what you changed. Commit.

Optional, if the tool keeps inventing screens: `resources/prompting-for-a-prototype.md`.

## 1:05 to 1:30. Checkpoint 2: north star and event schema

Open `templates/north-star-worksheet.md` as a worksheet (do not commit it). Write three candidates, including your session draft. Run the three tests on each. Keep one; the other two are your decoys. Write the last line of the worksheet as a new line at the bottom of `DECISIONS.md`.

Then copy `templates/event-schema.md` to `03-build/analytics/event-schema.md`. North star sentence at the top, north star event named, then one row per event: name, fired by, properties, owner. Four to six rows is right for this week. Fill the Reconcile plan line with your silent-failure prediction from the session. Commit.

Optional, if stuck: `resources/choosing-a-north-star.md` and `resources/writing-an-event-schema.md`.

## 1:30 to 1:45. Checkpoint 3: test plan

Copy `templates/test-plan.md` to `02-design/user-testing/test-plan.md`. Paste your frozen test from prototype-plan section 5, unchanged. Name five testers: code name, role, how they match your ICP, who on your team runs the session, and a target day. At least three must be people you have already messaged. Commit.

Optional, if stuck on recruiting or running sessions: `resources/running-five-user-tests.md`.

## 1:45 to 1:50. Studio

Send the outreach messages for any tester slots still empty. Real names stay in your team chat; code names go in the repo.

## 1:50 to 2:00. Homework, read aloud

**Deliverable:** Prototype v1 link in README, `03-build/analytics/event-schema.md` with north star, 5-user test plan. Interviews complete: 10 total logged.

**Deadline:** Before your Week 6 lab. Run at least 3 of the 5 prototype tests before then.

**Submission:** Commit to your team repo.

**Points:** Feeds Milestone 2 (10 pts, Week 11). Watch-check for the Week 6 recording due before your lab.

Your north star will be challenged in Lab 6. Bring the sentence, the number, and the reason.
