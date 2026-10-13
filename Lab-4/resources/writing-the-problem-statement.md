# Writing the Problem Statement from Evidence

*Optional. Linked from Lab 4, checkpoint 3. You can finish the lab without it; your statement will hold up better under questioning with it.*

## The concept

Your Milestone 1 problem statement is one paragraph that says who has the problem, when it happens, what it costs them, what they do about it today, and why that fails them. Every sentence ends with the log numbers that prove it. That last rule is what separates it from every problem statement you have written before.

It is not a pitch. A pitch tries to make a reader want something. A problem statement tries to make a reader see something they could not see before, and lets them check your work. If a reader cannot open log 03 and find the line you are leaning on, the sentence does not count.

It is also not your Lab 1 statement. That one recorded one moment you watched. This one is the pattern your interviews proved, narrowed to one person and one moment.

## Why it matters

Everything you build in Weeks 5 to 7 inherits the problem statement. The prototype tests it, the north star measures it, the MVP boundary cuts toward it. A vague statement does not fail loudly; it fails by letting the team build anything.

Quibi is the expensive version. It raised about 1.75 billion dollars on a confident statement of the problem: people want premium shows in ten-minute pieces for the in-between moments of their day, on their phones, on the go. It launched in April 2020 and announced it was shutting down about six months later. The pandemic made the "on the go" moments disappear, but the deeper issue was that the problem statement was a belief about behavior, not a record of it. No amount of production quality could fix a problem that real people were not having in the way the statement described.

Your statement is cheaper than Quibi's because you can check every sentence against a log this week.

## Worked example, step by step

The Sakhli team built theirs from `patterns-analysis.md` in about twenty minutes. Here is the order that works.

**Step 1: Start from the strongest pattern and its root cause.** Pattern: hosts fear the double-book more than the commission (01, 03, 05, 07). Root cause: two booking channels that never sync.

**Step 2: Write "who" from the logs, not from the ICP.** The ICP said "hosts with 3 to 10 rooms". The logs added the detail that matters: hosts who take bookings on Booking.com and directly at the same time. A host on one channel cannot double-book across channels. That detail narrows the who, and it came from evidence.

**Step 3: Write "when" as a moment you could film.** Not "in summer". The logs say July and August evenings, when requests arrive on two channels within an hour (01, 03).

**Step 4: Write "cost" with numbers.** Two double-bookings in a season (01), one refund plus a neighbor's room paid for (07), 3 a.m. phone checks (03). No adjectives.

**Step 5: Write "today" and "why it fails" in their words.** The notebook by the phone, checked twice a day (03), and the call to the neighbor (05). Then the quote that explains the failure: "Still, twice this season." (03)

**Step 6: Write what the evidence ruled out.** The commission: 0 of 8 unprompted, 7 of 8 called it normal. This sentence protects the team from drifting back to the old idea under pressure.

**Step 7: Write what is still open.** Whether a host will trust a tap on her phone more than her own handwriting. This is honest, and it hands off directly to next week's prototype.

**Step 8: Add a DECISIONS.md line.** The statement is a decision, so it gets a line with its evidence:

```
Wk4 · Problem statement v1: double-booking across unsynced channels, scoped to Racha hosts with 3 to 10 rooms · evidence: 01-discovery/problem-statement.md, synthesis/patterns-analysis.md · owner: MG
```

## Common mistakes and how to spot them

**Solution words.** "Hosts need a shared calendar" is a solution wearing a problem's clothes. Spot it: search the file for app, platform, tool, AI, need, should. Rewrite each as what happens to them today.

**A segment instead of a person.** "Small businesses in Georgia" could be anyone. Spot it: read sentence 1 aloud and ask whether a stranger could find this person in a room of fifty.

**Costs as feelings.** "It is very stressful" cannot be checked. Spot it: if sentence 3 has no number, no money, no lost customer, and no hour, it is not a cost yet. Find the log that has one, or admit you need another interview.

**Combining two patterns into one statement.** Double-booking and English replies are both real for Sakhli, but a statement about both is a statement about neither. Spot it: if your "when" has two different moments, pick one. The other becomes your runner-up.

**Writing it from memory.** Teams who write the statement first and add log numbers afterwards always find a sentence nobody said. Spot it: write the numbers as you write each sentence, never later.

## Check yourself

1. A team writes: "Students struggle with time management, which causes stress. (02, 04)". Name two things wrong with it.
2. Your strongest pattern has a clear cost, but the cost only appears in one of its three logs. Can sentence 3 still stand?
3. A teammate wants to add a sixth sentence describing the product you plan to build, "so the reader knows where this is going". What do you tell them?

*Answers.* 1: The who is a segment, not a person; "time management" is a topic, not a filmable moment; "stress" is a feeling, not a cost. 2: Yes, if it cites that one log honestly, but mark it as the claim with the least support and probe cost in your next interviews. 3: No. The problem statement is checked against logs, and no log contains your product. The product goes in the prototype plan.
