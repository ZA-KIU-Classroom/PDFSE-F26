# When Nobody Came

## The concept

Some teams arrive at Lab 8 with a live product and no real users, or with the gate still open. That is a state, not a failure of the lab. It has its own readout, and the readout is not empty.

When nobody used the product, the product has told you nothing yet. Something else has: the path between you and your users. Who was meant to get the link, whether it reached them, whether they opened it, and whether they did the first step. Each of those is a count, and each zero has a cause you can find this week.

The rule: an absence is data about delivery before it is data about the product. Do not conclude "they do not want it" from people who never saw it.

## Why it matters

In the Second World War, American analysts studied bombers returning from missions and mapped where the bullet holes were. The plan was to add armour where the holes clustered. A statistician named Abraham Wald pointed out what the map left out: the aircraft that did not come back. The holes showed where a plane could be hit and still fly home. The armour belonged where the returning planes had no holes at all. The missing planes were the most important data, and they were not in the sample.

Your dashboard only shows people who arrived. The people who never opened your link are your missing planes. They are not in PostHog. They are in your field table, and in your phone.

## Worked example, step by step

A team in state B. Product live, north star event reconciled on test data, five people named in the Sprint 2 field table, zero real events.

Step one: section 1 of the readout still applies. Reconcile on your test record, so you know the pipe works. If it does not, that is your finding and you are in state C.

Step two: section 2. Paste the prediction. Real: zero. Say so plainly. If "we are wrong if" fired, write that it fired.

Step three: sections 3 and 4, from the field table instead of events. Asked: 5. Message actually sent: 3; two teammates never sent theirs. Link opened: 1, judged by `guest_opens_host_link` with that person's source tag. First step done: 0.

Step four: name the actor at the widest drop. Here it is the team: two of five messages were never sent. That is uncomfortable and true, and it is the most fixable finding there is.

Step five: for the one who opened and stopped, section 5. What did she see? Ask her, today. That is one ten-minute call and one new interview log.

Step six: Experiment 1 is about delivery. Hypothesis: "people do not open the link because it arrives as a bare URL from a stranger." Change: a teammate hands it over in person or on a call and stays for the first open. Metric: of 5 people, how many do the first step within 3 days. Success: 3 or more. Failure: 1 or fewer.

Step seven: section 8, and the messages, sent in the lab.

For state C, add one step at the front: the rung you are on, the error or blocker in one line, the owner, and the day it closes. Checkpoint 1's time goes to that. Then write sections 2, 5 and 8, which need no data.

## Common mistakes and how to spot them

**Writing nothing.** Spot it: a readout that says "no data" and stops. The field table is data.

**Blaming the user.** "People are not interested." Spot it: ask how many of them saw the product working.

**Hiding unsent messages.** Spot it: the "sent by, and by when" column in Sprint 2 against what was sent.

**Filling the gap with your own clicks.** Spot it: the internal filter is off and the numbers are suddenly healthy.

**Jumping to a new idea.** No users in one week is not evidence against the problem you spent seven weeks finding. Spot it: a pivot line with no log behind it.

**Waiting for traffic.** Spot it: no names in section 8.

## Check yourself

1. Of the people in your field table, how many definitely saw your product working?
2. Which step of delivery lost the most people, and who owned it?
3. What would you have to see by Lab 9 to say the product, rather than the delivery, is the problem?
