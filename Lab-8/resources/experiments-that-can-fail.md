# Experiments That Can Fail

## The concept

An experiment is a bet you can lose, written down before you make it. It has six parts. A hypothesis: what you think causes the drop, in a sentence that could be false. One change. A metric, and exactly where you will read it. A success threshold. A failure threshold. And a decision rule that says what you do in each case, including the case where too little happened to say anything.

All six are written before the first day and then frozen. The commit that adds the file is the freeze. If you can still adjust the thresholds after the data arrives, you are describing, not testing.

It is the Lab 4 test card again, pointed at a live product.

## Why it matters

In 1985 Coca-Cola replaced its recipe. The company had run close to two hundred thousand taste tests, and the new formula won them clearly. Within three months, after a flood of angry calls and letters, the original was back on the shelves. The tests had measured the wrong thing with great care: which of two sips people preferred. The decision was about something else: how people would behave when the drink they had grown up with was taken away. Nobody had written down what result, on what measure, would mean "do not do this".

A team of three makes the same mistake cheaply. You measure what is easy to read, clicks on a button, when the bet is about something else, whether a host answers a guest. Then any result looks like progress.

## Worked example, step by step

Sakhli, Lab 8, checkpoint 2.

Step one: start from the readout. The widest drop: 11 requests, 5 with no answer.

Step two: baseline. Median 14 hours to answer, on 6 answered requests. Without this line, no later number means anything.

Step three: hypothesis. "Hosts answer late mainly because they do not notice that a request has arrived." It could be false. One host has already said she noticed and waited anyway.

Step four: one change, done by hand. For 7 days GT sends the host a WhatsApp message within 10 minutes of each request. No code. If a teammate can play the feature for a week, do that before building it.

Step five: metric. Hours from request to answer, same query as the baseline. Not "messages sent", which GT controls, and not "link opens", which is not the bet.

Step six: thresholds, both. Success: median under 4 hours on at least 10 requests. Failure: median still over 10 hours, or fewer than half answered within a day. The gap between 4 and 10 is on purpose: a result in between is "unclear", and the rule covers it.

Step seven: decision rule. Success: build the automatic nudge. Failure: noticing is not the problem; enter one host's notebook bookings by hand and test that. Fewer than 10 requests: run another week and claim nothing.

Step eight: write what will not change while it runs. The guest email is held back until the experiment ends, so only one thing moves.

Step nine: commit, then start.

## Common mistakes and how to spot them

**No failure threshold.** Spot it: ask what result would make you stop. If the answer is a shrug, write a number.

**A threshold with no minimum number of cases.** "Median under 4 hours" on two requests. Spot it: every threshold names how many cases it needs.

**A metric you control.** Messages sent, features shipped. Spot it: could the number go up with no user doing anything?

**A metric that cannot move in your window.** Monthly retention in seven days. Spot it: count how many times the event could even happen before the end date.

**Two changes at once.** Spot it: the "what we will not change" line is empty.

**Editing the file after the start.** Spot it: the commit history. Only the run log and the result should change.

**No baseline.** Spot it: the first line of the file.

## Check yourself

1. What number, on how many cases, would make you drop your idea?
2. Could a teammate play your change by hand for a week instead of building it?
3. If too little happens to say anything, what does your decision rule tell you to do?
