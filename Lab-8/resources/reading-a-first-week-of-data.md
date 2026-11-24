# Reading a First Week of Data

## The concept

Reading a week of data is five questions asked in a fixed order. Is it real? What did we predict? Where do people stop? Who is standing at the drop? What does the data refuse to say? The order protects you. The first two questions stop you from explaining numbers that are wrong or from moving the target after you see where the arrow landed. The last one stops you from treating a count as a reason.

The output is one page, the readout. It ends with one thing that comes off your plan and one that goes on. If nothing changes, either your prediction was perfect or you did not read.

## Why it matters

In 1936 an American magazine, the Literary Digest, ran the largest opinion poll anyone had attempted. It posted ten million ballots and got about 2.4 million back. On that mountain of data it predicted that Alf Landon would beat Franklin Roosevelt comfortably. Roosevelt won 46 of the 48 states. The magazine had drawn its addresses from telephone directories and car registrations, in the middle of the Depression, so its 2.4 million answers came from the people least like the country. Nobody had asked the first question: who, exactly, is in this count?

Your version is smaller and the same shape. A dashboard with forty opens and fourteen confirmations looks like a good week until you ask who is in it, and find three teammates and a test account. That is why question one comes first.

## Worked example, step by step

Sakhli, Lab 8, checkpoint 1.

Step one: is it real? NK repeats the Lab 7 reconcile for the whole week. PostHog shows 4 confirm events with the internal filter on. The database shows 4 confirmed rows that are not the test house. Same window. They match, so the reading goes on.

Step two: the prediction, pasted, not paraphrased. Three bookings, six requests, four hosts opening their link, wrong if fewer than two hosts confirm. Beside it: four, eleven, three, and two. Nobody comments yet.

Step three: step counts. 23 opens of a host link, 11 requests, then the requests split: 4 confirmed, 2 declined, 5 with no answer after two days. The widest drop is after the request.

Step four: the actor. The team breaks the 11 requests down by host. Two hosts did all the confirming. One received three requests and answered none. One never opened her link. The drop belongs to hosts. One query adds a size: a 14 hour median from request to answer.

Step five: what it refuses to say. Why one host ignored three requests. Whether the other ever saw the product. Whether the silent guests went elsewhere. Each question gets a person to ask and a teammate to ask them.

Step six: what changes. Before the reading, Sprint 3 was a second door on Instagram and a photo gallery. After it, both are back on the cut list, and host response time is the next thing. That is a DECISIONS.md line with the readout as evidence.

The whole reading took the team forty minutes. The plan it replaced would have cost them two weeks.

## Common mistakes and how to spot them

**Starting at the dashboard's biggest number.** It is usually opens or page views. Spot it: your first sentence is about a step nobody doubted.

**Skipping the reconcile because it matched last week.** Code changed since then. Spot it: section 1 has last week's numbers in it.

**Editing the prediction.** "We meant real hosts, so it was really two." Spot it: the pasted prediction differs from the one in your Sprint 2 commit.

**Stopping at a prediction you hit.** Spot it: your readout has no widest drop.

**Naming a step instead of an actor.** "The drop is at confirmation." Who confirms? Spot it: section 4 has no person or group in it.

**Explaining the drop from your chair.** "Hosts are probably busy." Spot it: a because with no log number after it.

**Reading your funnel as one person's journey when two different people do the steps.** Spot it: a PostHog funnel that reads zero at the handoff. Use step counts.

## Check yourself

1. Who is in your north star count this week, and how do you know your own team is not?
2. What is your widest drop, as two counts, and which actor stands there?
3. What is one thing your data cannot tell you, and whose phone number answers it?
