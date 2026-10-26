# Drawing the MVP Boundary

## The concept

An MVP is not the smallest set of features you can ship. It is the smallest complete user journey that tests whether the product creates value. The difference is the word journey. A feature is a capability your product has. A journey is a sequence of actions one real person takes, with a first step and a last step, where the last step is the moment their problem is smaller than it was.

The boundary is the line around that journey. Inside the line: every step the value needs, however hard. Outside the line: everything else, however easy, with a one-line reason that points at evidence and a note on when it comes back.

## Why it matters

A team with four weeks of evenings and a feature list of twenty items will build the first two or three items beautifully, run out of time, and arrive at the deadline with a landing page. It will look good in a screenshot and test nothing, because the person never reaches the step where the value lands.

The failure story is from Spring. A team building a scheduling tool for private tutors spent Sprint 1 on a polished tutor profile page: photo, bio, subjects, rates, availability grid. Nobody could book a lesson through it, because booking was "Sprint 2". The exam break arrived, the product sat live for two weeks, and the dashboard showed forty profile views and zero bookings. The team read that as "tutors are interested." It meant nothing, because the journey ended before the value. They shipped the booking flow in Week 10, three weeks after they could have had real data on it.

Their boundary should have been: a student opens a tutor's link, picks a slot, the tutor confirms, both get the time. Four steps. The profile page was one field (a name) in step one.

## Worked example, step by step

Sakhli, Lab 6.

Step one: write the feature cloud. Everything in anyone's head, including the things the prototyping tool invented. Sixteen items: guest opens link, payments, request dates, reviews, AI reply drafter, host confirms, channel sync, confirmation to both, multi-property, guest room picker, calendar blocks dates, photo gallery, host login, stats dashboard, in-app chat, map.

Step two: ask the only question that draws a line. What is the shortest sequence of actions after which Nino's double-booking fear is smaller than it was? The answer is five steps: a guest opens her link, requests dates, she taps confirm, both get the confirmation, the calendar blocks those dates. At step five, one booking exists in one place and cannot be sold twice.

Step three: everything not on that path goes on the cut list. Eleven items. The three most impressive ones, payments, the AI drafter, channel sync, are all outside the line. Impressive features come from other products; journey steps come from logs.

Step four: write one reason per cut, pointing at evidence or the hypothesis. Payments: the hypothesis is testable without money moving, and zero of ten logs asked. Room picker: log 04 has the host choosing. Host login: Nino does not use email; a private link reaches step three. Map: Oni has one road.

Step five: write when each cut comes back. Payments after the Week 12 pricing test. The AI drafter in Week 10, once there is real calendar data. Reviews never, until a host asks. The cut list is now the roadmap.

Step six: check complete and smallest. Complete: without the last step, a confirmed request with no calendar block is still a double-booking waiting to happen. Smallest: for each step, ask whether the value lands without it. Step four was the closest call; log 03's host calls guests back "so they know it is real," so without a confirmation the guest messages on WhatsApp and the notebook returns.

## Common mistakes and how to spot them

**The journey ends before the value.** The last step is "user submits the form." Spot it: ask what is true in the person's life after the last step that was not true before. If the answer is "we have their data," the journey is not complete.

**A reason that names difficulty.** "Too hard," "later," "Sprint 2." Spot it: a reason must point at a log, a session, or the hypothesis. Hard things the hypothesis needs stay in. A boundary drawn around the easy parts is not an MVP; it is a demo.

**The journey is a list of features in disguise.** "1. Profiles 2. Search 3. Booking 4. Payments." Spot it: every step must start with a person and a verb. "Guest opens the link." "Host taps confirm." If a step has no actor, it is a feature.

**Two journeys.** The guest's journey and the host's journey written as two separate lists. Spot it: Sakhli's journey switches actor at step three and that is fine; one journey can have two people in it. Two journeys means two products, and Sprint 1 holds one.

**Nothing on the cut list.** Spot it: a boundary with no cuts has not been drawn. Run the smallest test on each step and the list fills.

## Check yourself

1. What is true for your ICP person after the last step of your journey that was not true before it?
2. Read your three biggest cuts. Does each reason cite a log, a session, or the hypothesis, rather than difficulty?
3. Which step was the closest call to cut, and what evidence kept it in?
