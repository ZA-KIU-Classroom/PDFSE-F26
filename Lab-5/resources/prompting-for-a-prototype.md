# Prompting for a Prototype

## The concept

An AI prototyping tool turns a description into a clickable flow in minutes. That speed is real, and it is why prototype-first is now the default way small teams work. The cost is that the tool is built to be helpful, and to a tool, helpful means complete: every gap in your description gets filled with a feature from every app it has ever seen. Prompting for a prototype is the discipline of giving the tool your evidence, your exact screen list, and your list of what must not appear, so that what comes back is your product and not the average of every booking app on the internet.

The prompt is not the end. Every screen that comes back is checked against the prototype plan before a tester sees it. A good prompt makes the check faster. It never makes it optional.

## Why it matters

The first Sakhli prompt was two sentences and included the words "professional and complete". Eight minutes later: seven polished screens, two of which, guest reviews and deposit payments, no host had ever mentioned, and one of which, choose your room, worked against what log 04 actually said. A team that had not written its screen table first would have tested all seven, collected findings about screens that should not exist, and built Week 6 on top of them.

The failure story is from a Spring team building a tool for small bakeries to manage pre-orders. Their first prompt said "a pre-order app for bakeries". The tool returned loyalty points, a reviews tab, push notifications, a map of nearby bakeries, and an admin dashboard with charts. The team spent their build lab deleting, then ran out of time, then tested a prototype that still had a loyalty-points screen in it. Two of their five testers spent the whole session trying to understand the points. The team's one action, "a baker can accept tomorrow's orders in one place", was never reached by either tester. They learned nothing about their riskiest assumption and a great deal about loyalty points, which were not in any interview.

## Worked example, step by step

Sakhli's second prompt, Lab 5, same tool, same evening as the first.

Step one: paste the evidence first. The whole problem statement from `01-discovery/problem-statement.md` goes in before any instruction. The tool now knows who the host is, what she fears, and what she does today. That context shapes every screen it generates, in the same way it would shape a human designer.

Step two: name the exact screens, from the screen table in the prototype plan, and say "exactly these and nothing else". For Sakhli: request card with guest name, channel, dates, party size; this week's calendar showing which rooms are free; confirm, one button; blocked week with the dates marked taken. Four screens. The number is in the prompt.

Step three: name what must not appear. Reviews, payments, deposits, guest room choice, chat, settings, onboarding, dashboards. The list comes from the "will not appear" section of the plan, which was written before the tool was opened. Then the instruction that matters most: "If something seems missing, leave it out and list it at the end instead."

Step four: ask for phone-sized output, opened from a link. The test is about a tap on the host's own phone. A desktop layout tests a different thing.

Step five: when it comes back, walk every screen against the table. A screen in the table: keep. A screen not in the table: delete, and if it was a real feature the tool invented, log the delete as a DECISIONS.md line with the count of interviews that asked for it, which is zero. Then open the link on a phone and walk the one action yourself before any tester does. Then one line in `docs/ai-usage-log.md`: week, who, tool, what it produced, what you changed.

## Common mistakes and how to spot them

**"Professional and complete."** Any adjective that invites the tool to fill gaps. Spot it: if your prompt has no list of what must not appear, it has invited everything.

**No screen count.** "Build the booking flow" instead of "exactly these four screens". Spot it: the tool returns more screens than your plan has rows.

**Evidence after instructions, or not at all.** Spot it: if your problem statement is not in the prompt, the tool is designing for a generic user.

**Trusting the output because it looks finished.** Spot it: a polished screen with no row in your table. Looking finished is the tool's job; belonging is yours to check.

**Testing on the laptop the tool is open on.** Spot it: your tester did not open a link on their own phone.

**Forgetting the usage log.** Spot it: `docs/ai-usage-log.md` has no line for this week.

## Check yourself

1. Does your prompt contain your problem statement, your exact screen list with a count, and your "must not appear" list?
2. After generation, how many screens came back versus how many are in your table? What happened to the difference?
3. Did you walk the one action on a phone yourself before a tester did?
