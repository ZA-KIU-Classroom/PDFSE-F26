# Five Whys and Root Cause

## The concept

Five whys is a method for walking from a pattern you observed down to the reason it exists. You state the pattern as a fact, ask why it happens, write the answer in one sentence, then ask why of that answer. Repeat. Five is a convention, not a rule: stop whenever the next answer would be a guess rather than something a quote actually supports, and keep going past five if the evidence holds up that long.

The point is not depth for its own sake. The point is that a pattern tells you what happened, and a root cause tells you what to build against. "Hosts fear double-booking" is a pattern. "Hosts run two uncoordinated booking channels because direct bookings protect the relationships their business depends on" is a root cause you can design a product around.

## Why it matters

Teams that skip root-causing build features aimed at symptoms. If "hosts fear double-booking" is where you stop, the obvious fix is a bigger warning banner or a confirmation email, cosmetic patches on a coordination problem that will keep resurfacing. If you push to the actual root, two calendars that don't talk to each other because the business logic behind direct bookings has no home in either system, you design toward the thing that's actually broken.

The failure story: a team building a tutoring marketplace noticed students kept canceling sessions last minute. They asked why once ("scheduling conflicts") and built a reminder notification feature. Attendance didn't improve. A second round of interviews, pushed to a third and fourth why, found that students canceled because they didn't trust the tutor would actually be useful for their specific problem, and backed out rather than waste an hour. The real fix was a pre-session fit-check, not a reminder. One why wasn't enough to find it.

## Worked example, step by step

Pattern: "Hosts fear the double-book more than the commission," supported by interviews 01, 03, 05, 07.

**Why 1: Why do hosts double-book?**
They track availability in two places, a paper notebook and Booking.com, that do not sync. (Traceable to Int. 03's notebook-by-the-phone detail and Int. 01's "sold the same room twice.")

**Why 2: Why two places that do not sync?**
Booking.com has no visibility into stays arranged directly over WhatsApp. (Traceable to the pattern itself: every host interviewed takes some direct bookings outside the platform.)

**Why 3: Why arrange stays outside the platform at all?**
Direct bookings are commission-free and feel like a relationship, not a transaction. (Traceable to Int. 07's attitude toward "normal" commissions paired with the clear preference for repeat, direct guests across multiple logs.)

**Why 4: Why does the relationship matter so much?**
Repeat guests and word of mouth are the real distribution channel in a small valley. (This one is inferred from context, the valley's size and the overflow-sharing behavior in Int. 05, rather than a single direct quote. Flagged as an inference, not a confirmed fact.)

**Why 5: Why does one double-booking matter this much?**
It costs a guest, a refund, and reputation in a community where everyone talks. (Traceable to the refund mentioned directly in Int. 07.)

Root cause in one sentence: hosts run two uncoordinated booking channels because direct bookings protect the relationships their business depends on, and the coordination gap between those channels is where the fear lives.

Notice that why 4 is marked as an inference rather than a confirmed fact. That's not a failure of the method, it's the method working correctly: you log where your reasoning outran your evidence, and that becomes a question for your next interview instead of something you quietly assume.

## Common mistakes and how to spot them

**Stopping at why 1 and calling the mechanism the root cause.** "Hosts double-book because they use two calendars" explains the mechanism, not the reason the mechanism persists. Spot it by asking: if I fixed only this layer, would the underlying behavior actually change, or would hosts find a new two-calendar workaround?

**Answering with another symptom instead of a reason.** "Why is it stressful? Because it's a big responsibility" restates the problem in different words rather than explaining it. Spot it by checking whether your answer could substitute for the original pattern statement with no new information added.

**Inventing a cause no interview supports.** It's tempting to reach for an answer that sounds smart. Mark every inferred step honestly, the way why 4 is marked above, instead of presenting a guess as a finding.

**Running five whys on a pattern built from one interview.** The chain will look convincing and mean nothing. Root-cause only patterns that already cleared the two-interview floor from your affinity map.

## Check yourself

1. For each "why" in your chain, can you point to a specific quote, or did you mark it as an inference?
2. Does your root cause describe something you could design a feature against, or does it still describe a feeling?
3. If you only had time to fix the thing your root cause names, would the original pattern actually go away?
