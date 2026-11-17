# Walking Your Own Product

## The concept

Deployed means a stranger can open it on a phone and finish the journey without you. Not "the build passed". Not "it works on my laptop". A walk is the check for that: one teammate who did not build the step opens the production address on a phone, on mobile data, and does the journey from the first tap to the last, while saying nothing to the person who built it.

Your product lives at three addresses. `localhost` is yours alone. A preview address (the long one with a branch name in it) is for teammates signed in to your host, and a tester who opens it sees a login wall. The production address is the short one, and it is the only one that counts for rungs 1 and 2, for user tests, and for the field week.

## Why it matters

On its first day in 2013, the United States government's health insurance site, HealthCare.gov, was open to the whole country. Internal notes later released to Congress recorded six completed enrollments that day. Each part had been built and tested by its own contractor. What had not happened, until days before launch, was one person walking the whole journey, end to end, in the real environment, the way a citizen would. The parts worked. The journey did not.

Your version of this is smaller and the same shape. The link page works. The request form works. The host page works. And nobody has gone from the first to the last on a phone that has never seen your laptop's network.

## Worked example, step by step

Sakhli, Lab 7, checkpoint 1. LK is the walker because LK did not build stories S1 to S3.

Step one: Wi-Fi off. LK's phone and NK's laptop are on the same campus network, and Sakhli's first deploy had a database URL that only resolved from that network. On mobile data, the page loaded and the dates did not. Rung 1 passed, rung 2 failed, and the team knew in ninety seconds.

Step two: the fix was a variable. `DATABASE_URL` in the host's settings still held a local value from testing. NK replaced it with the hosted database's string and redeployed. A variable changed in the host's settings does not exist until the next deploy.

Step three: LK walks again, from the top. Opens the test house's guest link. Picks two nights. Types a first name and a contact. Taps Request. Sees "Sent."

Step four: LK opens the test house's private host link on the same phone. One pending request. Taps Confirm. The request shows Confirmed.

Step five: LK goes back to the guest link and tries to request the same dates. The picker refuses them. That is the journey's last step, seen by someone who did not write it.

Step six: LK says what was confusing, once, at the end: the Confirm button needed a scroll on a small screen. That becomes a card on the board, not an argument.

Rung 2 is reached when the walker finishes without help. If the walker had to ask what to press, that is a finding to log, and the walk still counts.

## Common mistakes and how to spot them

**The builder walks their own step.** They know where to tap and which fields to skip. Spot it: the walker's initials differ from the story owner's.

**Walking a preview link.** It works for the team and shows a login to everyone else. Spot it: the address has a branch name or a long hash in it. Production is the short one.

**Walking on the same network as the laptop.** Things resolve there that resolve nowhere else. Spot it: turn Wi-Fi off before the first tap.

**A variable in one place and not the other.** Present in the local env file, missing in the host's settings, or added there with no redeploy. Spot it: the page loads but the data, the events, or the email do not. Compare the names in `.env.example` against the host's settings, one by one.

**Stopping at the first working screen.** "It loads" is rung 1. The journey is rung 2. Spot it: ask the walker what was true at the end that was not true at the start.

**Walking on a real user's record.** A confirmed test booking on a real host's calendar is a real problem for her. Spot it: your team has one test record, and its id is written in your schema file.

## Check yourself

1. Who walked your journey, on what network, and which story did they not build?
2. What is your production address, and how can you tell it from a preview address at a glance?
3. Name each environment variable your product needs, and the two places each one must exist.
