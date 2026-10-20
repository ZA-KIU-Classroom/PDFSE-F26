# North Star Worksheet

**This file is a worksheet. Do not commit it.** Fill it in during Checkpoint 2, then copy its last line to the bottom of `DECISIONS.md`. The north star sentence also goes at the top of `03-build/analytics/event-schema.md`.

**Filled-in example:** `Lab-5/examples/north-star-worksheet.md` (Sakhli)

## 1. Three candidates

Write three. One must be the draft from the Week 5 session. One should be the vanity metric your team is most tempted by, so you reject it on purpose.

| # | Candidate, in the shape [value event] per [who] per [window] |
|---|---|
| A | |
| B | |
| C | |

## 2. Three tests on each

Stop at the first test a candidate fails. Write the reason in the cell, not just a cross.

| Test | A | B | C |
|---|---|---|---|
| 1. Counts value delivered, not presence. After this event, is the person's problem smaller? | | | |
| 2. Countable from one event you can name in actor_verb_object form | | | |
| 3. Can go down, and that would mean something | | | |

## 3. The survivor

**North star:**

**North star event (actor_verb_object):**

**Who fires it, and why that person:** (it must be the person your problem statement is about)

**The log numbers that show value lands at this moment:**

## 4. The two decoys, with the test each failed

- Rejected **[candidate]** because it fails test [n]: [one phrase]
- Rejected **[candidate]** because it fails test [n]: [one phrase]

## 5. The line you commit

Bottom of `DECISIONS.md`, one line, this exact shape, angle brackets replaced:

```
Wk5 · North star: <sentence>; rejected <decoy 1> (<reason>) and <decoy 2> (<reason>) · evidence: 03-build/analytics/event-schema.md, 01-discovery/interview-logs/<files> · owner: <initials>
```
