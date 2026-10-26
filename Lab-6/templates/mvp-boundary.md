# MVP Boundary

**Save this file as:** `03-build/mvp-boundary.md`
**Filled-in example:** `Lab-6/examples/mvp-boundary.md` (Sakhli)

The smallest complete user journey that tests whether the product creates value. Complete: the person gets the value, start to finish. Smallest: nothing that is not on that path is in Sprint 1.

**Value hypothesis under test:** [one sentence, copied or tightened from `01-discovery/problem-statement.md`; name the person and the thing that gets smaller or easier for them]

**The one person walking this journey:** [the ICP name from `00-foundation/icp.md`, not "the user"]

## The journey

Five to seven steps. Who does what, one line each. The last step is the one where the problem is smaller than it was. If the journey does not fit here, it is not the smallest one yet.

1. [who] [does what]
2. [who] [does what]
3. [who] [does what]
4. [who] [does what]
5. [who] [does what]

**Why this is complete:** [what is true for the person after the last step that was not true before, in one sentence]

**Why this is smallest:** [name one step you considered removing and why the value would not land without it]

## Cut list

Every feature you considered and did not keep. The reason must point at your logs, your usability sessions, or the value hypothesis. "Too hard" and "later" are not reasons; hard things the hypothesis needs stay in.

| Feature | Reason (cite the log, session, or hypothesis) | Comes back when |
|---|---|---|
| | | |
| | | |
| | | |
| | | |
| | | |
| | | |

## Step to event

One row per journey step. Event names are copied from `03-build/analytics/event-schema.md`, never retyped. A step with no event: add the event to the schema in the same commit (four parts: name, fired by, properties, owner), or cut the step.

| Step | Event (actor_verb_object) | In the schema? |
|---|---|---|
| 1 | | yes / added today |
| 2 | | |
| 3 | | |
| 4 | | |
| 5 | | |

**North star step:** [the step number whose event is your north star event]

## The DECISIONS.md line

Copy this line, filled in, to the bottom of `DECISIONS.md`:

`Wk6 · MVP boundary: [N]-step journey ([first step] to [last step]); cut [the three biggest cuts] · evidence: 03-build/mvp-boundary.md, [logs or sessions cited in the cut list] · owner: [initials]`
