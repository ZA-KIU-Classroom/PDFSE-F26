# The Problem Hypothesis: Writing Down What Could Prove You Wrong

*Concept guide for Lab 2, step C2. About 7 minutes to read.*

## The idea, in plain language

By the end of C1 you have picked a problem to investigate. You also have beliefs about it: who has it worst, when it hits, what it costs. Right now those beliefs live in your heads, which means they cannot be wrong. A belief nobody wrote down quietly adjusts itself to whatever you hear.

A problem hypothesis is those beliefs written as one testable statement, plus the signal that would prove it false. It has six slots:

> **We believe** [who, from your ICP]
> **struggle with** [the problem]
> **when** [the specific moment it happens],
> **which costs them** [time, money, stress, customers].
> **Today they** [the workaround you have seen or expect].
> **We are wrong if** [what you would hear in interviews if this were false].

The last slot is the one that matters. A hypothesis without a "we are wrong if" line is a wish. With it, every interview becomes a vote: for your hypothesis, against it, or pointing somewhere you did not expect.

Three rules keep it honest:

- **It describes a problem, never a product.** "Hosts need a booking app" is a solution in disguise. "Hosts lose bookings when requests arrive on three channels at once" is a problem.
- **Every slot is specific enough to be checked.** "Sometimes" cannot be tested. "Every weekend in July and August" can.
- **It is written before your first real interview.** Afterward, your memory will helpfully rewrite it to match what you heard.

It lives in `01-discovery/problem-hypothesis.md`. Its "we are wrong if" line goes at the top of your interview script as your prediction, and into every interview log, so you check it every single time.

## Why it matters in practice

Juicero launched in 2016 with a 700 US dollar Wi-Fi-connected juice press (later cut to 400) and raised roughly 120 million dollars. The machine pressed single-serving packs of chopped fruit and vegetables sold by subscription.

In April 2017, Bloomberg reporters squeezed the packs by hand. It was about as fast as the machine and produced nearly the same amount of juice. Juicero shut down that September.

The hidden hypothesis was: "people who want fresh juice at home struggle to get it out of a pack without a powerful press." Written with a "we are wrong if" line, the test almost writes itself: *we are wrong if people can get the juice out without the machine.* That test costs one afternoon and a pair of hands. Instead, journalists ran it after the money was spent.

You are not raising 120 million dollars, but you are about to spend a semester. At every scale, the mistake is the same: building for a belief one honest test would have killed.

## Worked example, step by step

Here is how the Sakhli team wrote theirs in Lab 2, right after picking their problem.

**Step 1: Write what each of you believes, silently.** Two minutes, each on their own. Keti: "Booking.com's commission is the main pain." Luka: "They are overwhelmed in summer." Mariam: "They can't answer foreign guests fast enough." Three different beliefs is normal, and exactly why you write before you discuss.

**Step 2: Choose the one you test first.** Five minutes of argument. Keti had the strongest conviction and her aunt as evidence, so commissions went in. The other two became questions in the script, so the team would still hear about them.

**Step 3: Fill the slots, starting from your pick and your ICP.** Who: hosts with 3 to 10 rooms, like Nino. Struggle: the commission on every booking. When: looking at payouts in peak season. Cost: 15 to 18 percent of summer revenue. Today: they accept it, because the foreign guests are there. Wrong if: *hosts do not raise the commission themselves when they describe their biggest problems, before we mention it.* The full hypothesis is in `examples/sakhli-problem-hypothesis.md`.

**Step 4: Check the "wrong if" line is observable.** Could they tell from one interview log whether it happened? Yes: a host raised the commission unprompted, or did not. That is a test.

**Step 5: Copy the line forward.** It became the prediction at the top of script v1 and the prediction line in every log.

**What happened.** Four hosts in a row never mentioned the commission until asked. All four raised the fear of double-booking on their own. The hypothesis died by its own rule in Week 3, and hypothesis v2, built around double-booking, became Sakhli. Nobody argued with the evidence, because they had agreed in advance what it would mean.

## Common mistakes, and how to spot them

**The solution in disguise.** "Students need a better app to find study rooms." Search your hypothesis for product words (app, platform, tool, AI, bot). A problem hypothesis contains none.

**The unfalsifiable "we are wrong if".** "We are wrong if nobody has this problem." Nobody will ever say that, so it never triggers. Ask: what would I actually see in one log if this were false? If you cannot picture the line, rewrite it.

**The team average.** Three beliefs blended into one mushy sentence nobody holds. Spot it when every teammate reads it and says "sort of". Test one belief; turn the others into questions.

**Written after the interviews.** If the hypothesis perfectly matches your first three logs, check the commit dates. It should be committed before your first real interview.

## Check yourself

1. Rewrite this into a problem hypothesis with all six slots: *"KIU students need an app to split rent with roommates."*
2. Why did the Sakhli team write the commission belief into the hypothesis, even though two teammates believed something else? What happened to the other two beliefs?
3. Your "we are wrong if" line is "we are wrong if interviews go badly." What is wrong with it, and what would a better one look like for your own problem?
