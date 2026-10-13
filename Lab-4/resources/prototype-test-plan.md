# Planning a Prototype Test That Can Fail

*Optional. Linked from Lab 4, checkpoint 5. You can finish the plan without it; your Lab 5 build will be faster and your tests sharper with it.*

## The concept

A prototype is a question you can hand to someone. It exists to be misunderstood in a way that teaches you something, not to impress. Planning it means deciding four things before you open any tool: the riskiest assumption (the belief that, if false, makes everything else pointless), the one action a tester must be able to attempt, the cheapest fidelity that can test it, and a test with a failure behavior written down in advance.

Fidelity is a dial, not a virtue. Paper sketches, clickable screens, and coded software can each be the right answer. The right one is the cheapest that can kill your riskiest assumption. More polish than that is time you spent on decoration.

A test can fail only if you wrote down, before the session, what failure looks like. "See if they like it" has no failure. Every result reads as encouragement, so the test proves nothing.

## Why it matters

Two of the most famous early-stage tests in startup history spent almost nothing.

Dropbox, before the product worked reliably across machines, made a short screencast of how file syncing would feel. Drew Houston aimed it at the early-adopter crowd most likely to care, and according to Eric Ries in *The Lean Startup*, the beta waiting list jumped from about 5,000 to 75,000 people overnight. The riskiest assumption was "people want this badly enough to sign up". A video tested it. Code would have tested it months later.

Zappos began with Nick Swinmurn photographing shoes in local stores and posting the photos online. When someone ordered, he bought the pair at full price and shipped it. The assumption was "people will buy shoes without trying them on". He did not need a warehouse to find out.

The failure version is quieter. A team builds a polished clickable flow, shows it to five friends, and records "everyone liked it". Two weeks later real users ignore it, and nobody can say why, because the test never defined what not liking it would look like.

## Worked example, step by step

The Sakhli team wrote `02-design/prototype-plan.md` in about fifteen minutes.

**Step 1: List the assumptions, then pick the one that kills.** Their list: hosts want one calendar; a sync between Booking.com and direct bookings is buildable; hosts will confirm a request on their phone instead of WhatsApp and the notebook. The second is an engineering question with a known answer. The first is supported by four logs. The third has no evidence at all, and if it is false, the calendar is never used. That one is riskiest.

**Step 2: Write the one action.** A host can see a guest's date request and confirm it, and see the dates blocked. One person, one verb. The guest side is not tested yet; the host is the one whose behavior is in doubt.

**Step 3: Turn the dial.** Paper cannot test a tap on her own phone. Code adds data and accounts the test does not need. Clickable, phone-sized, built in one evening with an AI prototyping tool, wins.

**Step 4: List screens and trace each to evidence.** Request card (01, 03), calendar (03), confirm (the one action), blocked week (01, 03, 05, 07). Four screens. Then the "will not appear" list, written before the tool runs: reviews, payments, a guest choosing a room, an AI assistant.

**Step 5: Write the test.** Task, read word for word: "A family just asked for 14 to 16 August. Show me what you would do." Success: confirms within 60 seconds without asking. Failure: opens WhatsApp; asks what to press; taps the guest's button; reaches for the notebook. Decision rule: 3 or more failures out of 5, and the team tests a WhatsApp-first version before building more.

**Step 6: Predict the first mistake.** "She will tap Request dates, the guest's button." Writing the prediction makes the first twenty seconds of every session a mini experiment.

**Step 7: Name five testers.** Three hosts from earlier logs, two new. Code names only.

## Common mistakes and how to spot them

**A technical assumption as the riskiest one.** "We can build real-time sync" is a build risk, not a market risk. Spot it: if the assumption is about your code, not their behavior, pick again.

**Too many actions.** A prototype that tests sign-up, search, booking, payment, and reviews tests none of them well. Spot it: section 2 has "and" in it more than once.

**Screens nobody asked for.** AI prototyping tools generate plausible extras: dashboards, ratings, settings. Spot it: a screen with an empty "what earns it" cell. Delete it and log why.

**Failure you cannot see.** "They are confused" or "they do not like it" cannot be observed reliably. Spot it: could two teammates watching the same session disagree about whether it happened? If yes, rewrite as a behavior: they asked a question, they tapped the wrong button, they gave up.

**Changing the task after session one.** Editing the task mid-study makes sessions incomparable. Spot it: the commit history of your plan shows edits to section 5 after testing started. Freeze it, and note changes for the next round instead.

## Check yourself

1. Your riskiest assumption is "users will trust our recommendations". Your plan is a fully coded app with accounts. What is the cheaper fidelity, and why?
2. A test plan says: "Success: users find it intuitive. Failure: users find it confusing." Rewrite the failure line so two observers would agree.
3. In session one, the tester does something you never predicted and the task stops making sense. What do you do with the plan?

*Answers.* 1: Clickable screens (or even paper) showing a recommendation with fake but realistic content; trust is a reaction to what is on screen, not to whether a database exists. 2: For example: "asks us what to do next; taps anything other than confirm first; takes longer than 60 seconds." 3: Log what happened as the most valuable finding, finish the remaining sessions with the same task so they stay comparable, and write a new plan for round two.
