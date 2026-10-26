# Stories and Acceptance Criteria

## The concept

A user story is one journey step, written so it can fail. It has three parts. The story: as a named person from your ICP, I do one step, so that a value from your problem statement. The acceptance criteria: three to five lines, each one something a teammate can check on a phone at the deployed URL without asking the builder; given, when, then is the shape, and the then must be visible. The smallest demo: one sentence, what you would do on screen in thirty seconds to prove the story is done.

The criteria are the Lab 4 test plan in a new costume. Task, success, failure behaviors, written before the work, frozen, able to say no.

## Why it matters

Without criteria, "done" means "it works on my laptop and I am tired," and the disagreement surfaces the night before the gate. With criteria, a reviewer opens the deployed URL on a phone, runs five lines top to bottom, and the card moves or it does not.

The failure story is from Spring. A team's story for the core action read: "As a user, I can book a session easily." The builder finished it on a Tuesday. On Friday the reviewer could not find the button below the fold on a phone and said it was not done. They argued for forty minutes and shipped it as it was. The first real user on the break could not find the button either. Four criteria written before the work would have settled it in thirty seconds: button visible without scrolling on a phone; tapping it books the slot; the booking appears in the tutor's list; the event fires. "Easily" was the whole problem.

## Worked example, step by step

Sakhli, Sprint 1, story S3.

Step one: pick the journey step. Step three, the host confirms. It fires the north star event, so it gets written first and built first.

Step two: write the story with a real person. As Nino, I see every pending request in one place and confirm with one tap, so that I never say yes to the same dates twice. The who is the ICP by name. The so-that is the problem statement's pain, in her words from log 01.

Step three: write the criteria as things a reviewer can see. Given my private host link with one pending request, when I tap Confirm, then the request shows Confirmed with the guest's first name and dates. That is a screen. And the requests row status is confirmed. That is a database query the reviewer can run or ask to see. And the north star event fires with `is_first_for_host` true the first time, the repeat event after. That is a line in the console now and the live view in Week 7.

Step four: strike every adjective. The first draft said "quickly" and "clearly." Quickly became "within two seconds." Clearly became "with the guest's first name and dates." If two teammates could disagree about whether a line passed, it is an adjective.

Step five: write the demo. Confirm on a phone, show the row, show the event. Thirty seconds. If the demo had needed five minutes, the story was three stories.

Step six: one owner, one reviewer. NK builds it. GT walks it on a phone at the deployed URL and moves the card; GT reports, GT does not fix.

## Common mistakes and how to spot them

**"As a user."** No person from the ICP in the story. Spot it: the who must be a name from `00-foundation/icp.md` or a role from a log. "As a user" means you have not decided whose problem this step solves.

**Criteria that are adjectives.** Easily, quickly, nicely, intuitively, works on mobile. Spot it: ask whether two teammates could disagree. Replace each adjective with a number, a screen state, or a database state.

**No event in the criteria.** The story describes the screen and forgets the schema. Spot it: every journey step has an event in the mapping, so every story has a line that names it. A story that fires no event is not done under the definition of done.

**A story that is three stories.** "As Nino, I see requests, confirm them, and the guest is notified and the calendar updates." Spot it: the demo takes more than thirty seconds, or the story has two actors. Split at the actor change or the second verb.

**The builder as reviewer.** Spot it: the owner and reviewer columns must have different initials. On a two-person team they swap every story.

**Criteria written after the build.** The story is finished, then the criteria are written to match what was built. Spot it: the criteria are committed in the sprint plan on lab day, before any code exists. Changing them later is a DECISIONS.md line, not an edit.

## Check yourself

1. Read your north star story aloud. Who is the person, and could a teammate check each criterion on a phone without asking you anything?
2. Which criterion names the event, and is the event name copied from the schema rather than typed?
3. How long is your smallest demo? If over thirty seconds, where does the story split?
