# Process for Pods, Not Enterprises

*Optional. Nothing here is required for any grade. Read it the evening you set up your board, or when a teammate proposes a standup.*

## Three things survive

At two to four people with AI tools, three pieces of process earn their keep. Each one exists because without it a small team breaks in a specific, predictable way.

**A visible board.** One place, four columns: next, doing, review, done. Every story from `03-build/sprints/sprint-1.md` is a card with one owner. GitHub Projects on your repo is enough; so is Trello; so is a pinned message with four headings that someone edits daily. The failure it prevents: two people build the same screen on a Wednesday and nobody builds the host side. The board is where the team sees who is on what without a meeting.

**Small integrations, daily.** Merge to `main` every day anyone works. A branch that lives four days is a merge conflict with a deadline. AI tools make this worse: three people generating code quickly diverge quickly, and the conflicts are in files none of them wrote by hand and none of them fully understand. The rule: if your branch is older than a day, say so in the team chat before you write another line.

**A definition of done, in one sentence.** Yours is at the top of the sprint plan. Sakhli's: merged to `main`, deployed at the public URL, walked on a phone by a teammate who did not build it, and its events show in the live view. Each clause blocks one specific lie a tired teammate will otherwise tell.

That is the whole process. A fourth thing has to pay for itself in the hours you have, or it is ceremony.

## What does not survive

**Ceremony.** A daily standup for three people who sit in the same Telegram group. A retrospective in Week 7 for a sprint that was nine days long. A backlog groomed to forty items when the sprint holds five. Each of these feels like being a real company. A fifteen-minute standup three times a week is forty-five minutes of a nineteen-hour sprint.

**Estimation theater.** Story points argued for twenty minutes and then ignored. Velocity with one data point. Any number that is not hours a named person has free on a named evening.

**Roles as walls.** "The frontend is mine; ask Luka about the database." This is the Week 1 banned sentence in a new costume. In a pod, a role says who is accountable for a story landing, not who is allowed to touch a file. At Demo Day any member may be asked about any part. If only one person can explain the confirm flow, the team has assembled a product, not built one.

## Where Scrum still earns its keep

You will work at larger scale one day, and the lesson from this week is not "process is overhead." It is "every Scrum artifact is a fix for a coordination failure that appears at some size, and the skill is adopting only the fix for the failure you actually have."

Scrum earns its keep when there are thirty people on six teams and one product, and the ceremonies are how teams discover what each other broke. When stakeholders outside the team need a cadence to plan against. When work is hard to see, and a sprint review is how someone two levels up learns what exists. When estimation across teams matters, and relative sizing beats forty people guessing hours.

At three people your failures are divergence and unfinished stories. A board, daily merges, and a definition of done fix those. At thirty you will need more, and by then you will know exactly why each piece is there.

## What AI tools change

Two things, in opposite directions.

They make execution cheap, which makes scope discipline more important, not less. A team that can generate a settings page in ten minutes will generate one, and then own it, test it, deploy it, and explain it at Demo Day. The cut list is how you say no to things that cost nothing to start and plenty to keep.

They make review more important. Code nobody on the team wrote by hand needs a human to walk it on a phone before it counts as done, because the tool's idea of "works" is "compiles." That is the reviewer column in the sprint plan, and it is the smallest code review that works: open the deployed URL, run the criteria top to bottom, move the card or do not.

Every AI-assisted piece of work is one line in `docs/ai-usage-log.md`, same as it has been since Lab 2: week, who, tool, what it produced, what you checked or changed.
