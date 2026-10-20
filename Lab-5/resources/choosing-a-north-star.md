# Choosing a North Star

## The concept

A north star metric is the one number that says whether your product is delivering the value it promises. Not whether people found it, not whether they signed up, not how hard your team worked. Whether the person your problem statement is about got the thing they needed, and how often.

It passes three tests, applied in order. It counts value delivered, not presence. It is countable from a single event your code can observe. It can go down, and that going down would mean something true about the product. A candidate that fails any test is not a north star; it may still be a useful number, but it is not the one you steer by.

## Why it matters

A team steers by whatever it measures. If the number on the slide is sign-ups, the team will, without ever deciding to, spend its time on things that produce sign-ups: landing pages, Instagram posts, referral links. None of those make the product work. All of them make the graph go up. By Week 10 the team has a healthy-looking chart and no idea whether anyone's problem got smaller.

The failure story is from Spring. A team building a tool for private tutors chose "tutors registered" as their metric in Week 5. It rose every week. They presented it at the midterm check with pride. Then one teammate, preparing for the quality audit, counted how many registered tutors had actually scheduled a session through the tool. Four, out of thirty-one. Twenty-seven tutors had registered because a friend asked them to, and never returned. The team had measured presence for six weeks and called it traction. Their north star should have been sessions scheduled per active tutor per week, which would have read four, and would have sent them back to interviews in Week 6 instead of Week 11.

## Worked example, step by step

Sakhli, Lab 5, three candidates on the worksheet.

Step one: write the three in the same shape, value event per who per window. App downloads per month. Hosts signed up, total. Confirmed direct bookings per active host per month.

Step two: apply test one to each. After this event, is the person's problem smaller? A download: no. A guest found a link; Nino's August is unchanged. Signed up: no. Nino has three apps her nephew installed and uses none. A confirmed direct booking: yes. One booking that cannot be sold twice, through one calendar instead of two. Two candidates fail at the first test and the worksheet stops there for them.

Step three: apply tests two and three to the survivor. Countable from one event? Yes: `host_confirms_first_direct_booking`, and later `host_confirms_repeat_booking`. Can it go down? Yes, to zero in January, and that would be the winter churn assumption showing up in the number seven weeks before anyone names it.

Step four: check every word in the sentence. Confirmed, not requested: value lands on the host's action. Direct, not platform: the product exists to replace Booking.com for these bookings. Per active host, not total: ten bookings from one host is a pilot, one each from ten is a product. Per month: a window short enough to see winter.

Step five: write the DECISIONS.md line with both decoys and the test each failed. The decoys are the evidence that the team chose rather than defaulted.

## Common mistakes and how to spot them

**Choosing an effort metric.** Interviews done, features shipped, hours logged. These measure your team, not your user. Spot it: the user does not appear in the sentence.

**Choosing the precursor.** The event that fires most often, earliest, by the person who is easiest to count. For Sakhli, guest requests. Spot it: ask who receives the value. If the event is fired by someone else, it is the step before.

**Choosing a cumulative total.** Anything with "total" or "registered" in it. Spot it: can it ever go down? If not, it cannot tell you that you are failing.

**Choosing a window the product cannot fill.** "Per day" for a product used twice a month gives you a graph of zeros with occasional spikes, and you will conclude the product is dead. Spot it: ask how often the value event could plausibly happen for one person, and set the window to that.

**Keeping two north stars.** "We track bookings and also host satisfaction." That is a north star and a thing you also look at. Spot it: if two numbers disagree, which one decides? That one is the north star. The other is a diagnostic.

## Check yourself

1. Who fires your north star event, and is that the person your problem statement is about?
2. Could your north star read zero next month? What would that mean, in one sentence?
3. Read your two decoys. Can you name the test each one failed without looking at the worksheet?
