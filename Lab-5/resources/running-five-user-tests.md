# Running Five User Tests

## The concept

A user test is one person from your ICP, holding your prototype on their own phone, trying to do the one task you wrote in Lab 4, while two teammates watch and write and say nothing. Five such sessions find most of what is badly wrong with a flow. The sixth, seventh and eighth mostly find the same things again. So the plan names five people, each session is run identically, and the result of each is a verdict against the decision rule you wrote before you saw anything.

It is the Week 2 discipline with a screen in the middle. Past behavior beat future promises in interviews. In a test, present behavior beats stated opinion. You watch what the thumb does. You do not ask whether they like it.

## Why it matters

Teams that skip real sessions test with teammates and classmates, who know what the product is supposed to do and want it to work. Every session passes. The team concludes the prototype is ready. Then a real host, in Week 7, opens the live product, taps the wrong thing in eight seconds, and the team learns in production what five sessions would have told them two weeks earlier for free.

The failure story: a Spring team building a laundry-pickup app ran five "tests" with flatmates and cousins. Five passes. They built the full flow in Weeks 6 and 7. The first real user, a student in a dorm, could not find how to say which building she was in, because the flatmates had all lived in the same building as the founders and never needed to. The address step was the first screen a stranger needed and the last screen the team had looked at. One session with one real stranger would have caught it. They ran zero.

## Worked example, step by step

Sakhli's five sessions, planned in Lab 5 and run over the following week.

Step one: the test is frozen. Task, success, failure behaviors, decision rule, predicted first mistake, copied from the prototype plan into the test plan unchanged. Nobody edits it after session one, however tempting.

Step two: five testers from the ICP, none in the course, with code names. Three are hosts the team already interviewed (Oni-1, Oni-3, Amb-5), so recruiting is a WhatsApp message to someone who already said yes once. Two are new (Mes-9, Oni-7), one introduced by Oni-1 at the end of her interview. Each row names who runs the session and who logs it, and the roles rotate so every teammate does both.

Step three: the protocol, identical every time. The tester opens the link on her own phone. The runner reads the task word for word: "A family just asked for 14 to 16 August. Show me what you would do." Then the runner says nothing, even when the tester looks up. The logger starts the timer on the last word and writes time to first tap, time to the one action, and every unprompted sentence verbatim. At three minutes or when she stops, one question only: "What were you expecting to happen?"

Step four: the verdict, written before anyone talks. Oni-1 asked what to press at forty-five seconds; that is failure behavior two; FAIL. Not "she got there eventually". Oni-3 confirmed at thirty-one seconds unaided; PASS. Amb-5 picked up her own phone to call the neighbor before touching the prototype; that is the workaround arriving first; FAIL.

Step five: after three sessions, read the rule. Three or more of five fail changes course. Two of three so far. The rule says keep going to five. Meanwhile, two of three testers looked for the guest's name before the dates, which is a finding no interview produced; it goes into v2 as a DECISIONS.md line with the session numbers as evidence, without waiting for the rule.

## Common mistakes and how to spot them

**Testing with people who want you to win.** Teammates, classmates, friends. Spot it: would this person come to your birthday party? Then they are practice, not evidence.

**Helping.** Pointing, saying "try the top one", explaining the screen before they touch it. Spot it: every hint erases a finding. If the runner spoke after reading the task, the session is contaminated; log it honestly and run another.

**Testing on your phone.** Your phone has the link open, the screen size you designed for, and your thumbprints. Spot it: if the tester did not open the link herself on her own device, you did not test the first ten seconds.

**Editing the test after seeing results.** Softening a failure behavior because the first tester did it. Spot it: compare the test plan to the prototype plan; they must be identical.

**Logging feelings instead of behavior.** "Seemed confused." Spot it: two observers would disagree. Write what she did and what she said, with times.

**Asking for opinions at the end.** "Did you like it?" "Would you use it?" Spot it: the Mom Test. One question only, about expectation, not approval.

## Check yourself

1. For each of your five testers, could they be in this course, or would they come to your birthday party? If either, replace them.
2. Is the test in your test plan character-for-character the same as section 5 of your prototype plan?
3. After three sessions, what does your rule say to do, and did you do that rather than what you felt?
