# The Three-Tile Dashboard

## The concept

A dashboard is a small set of questions you can look at every morning. Three tiles are enough for a product with a handful of users, and each tile answers one question.

The north star trend: is value being delivered? A Trends insight counting your north star event over time.

The journey, step by step: where do people stop? If one person does every step, a Funnels insight with your journey's events in order, ending at the north star. If two different people do them, the step counts side by side.

Retention: does anyone come back? A Retention insight on your north star event. Empty this week, on purpose.

The test for any tile is the Week 5 test for a metric: can it go down, and would you do something different on Monday if it did?

## Why it matters

A number on a wall changes what people do, whether or not it measures the right thing. For years Wells Fargo tracked and rewarded the number of accounts opened per customer. The number rose steadily. In 2016 the bank acknowledged that employees had opened accounts customers had never asked for, in very large numbers, to hit it. The dashboard was accurate. It counted accounts. It did not count value delivered to a customer, and nobody had asked whether it could go up while customers got nothing.

Your version is a pageviews tile. It goes up every time you test. It will be the biggest number on your dashboard and the least useful. Leave it off.

## Worked example, step by step

Sakhli, Lab 7, checkpoint 3. Every event name is picked from PostHog's list, where it appears because it has already fired.

Step one: Dashboards, New dashboard, blank. Name: "Sakhli north star".

Step two: tile one. New insight on the dashboard, type Trends. Series: `host_confirms_first_direct_booking`, total count. Add a second series: `host_confirms_repeat_booking`. Interval: day for now. Breakdown by the event property `host_id`, so each host is a line. Confirm the internal filter toggle is on. Save and add to dashboard.

Step three: tile two, first try. New insight, type Funnels. Step 1 `guest_opens_host_link`, step 2 `guest_requests_dates`, step 3 `host_confirms_first_direct_booking`. It reads 9, then 3, then 0. Activity shows a confirm. The tile says none.

Step four: the team works out why. A funnel follows one person through the steps. The guest does steps 1 and 2 in a browser, anonymously. The host does step 3 as a different person. Nobody does all three, so nobody completes the funnel. Nothing is broken; the tool is answering a question Sakhli did not mean to ask. They replace the tile with a Trends insight holding three series, one per step, shown as totals: 9 opened, 3 asked, 1 confirmed, and write one line in the tile's description saying why it is counts. (A funnel can also be set to aggregate by an id every step carries, such as `host_id`, which then reads per host. Counts are simpler this week.)

Step five: tile three. New insight, type Retention. Cohort event and return event both set to the confirm events, weekly. It shows one host in week zero and nothing after. That is correct.

Step six: one extra tile with a named decision. `guest_opens_host_link` broken down by `source`. Decision: if `whatsapp` beats `card`, the team stops printing cards and writes a forwardable message for hosts instead.

Step seven: share. On the dashboard, create a sharing link that opens without a login, paste it into the Analytics dashboard row of the README, and open it in a private browser window to check it loads.

## Common mistakes and how to spot them

**A tile that reads zero when Activity shows events.** The insight's date range is wrong, the internal filter is hiding your only data (your own tests), or the event name in the tile is the stray misspelled one. Spot it: open the insight, turn the filter off, widen the range.

**A funnel across two people.** One actor starts the journey and another finishes it. Spot it: the last step reads zero while the trend tile shows confirms. Use counts side by side, or a property both events share.

**Percentages of tiny numbers.** "33 percent conversion" from nine opens. Spot it: if the denominator is under about thirty, say the counts.

**Tiles nobody can name a decision for.** Spot it: ask of each tile, what do we do differently if this drops by half?

**A dashboard link that needs a login.** The grader and your teammates' phones cannot open it. Spot it: a private window.

**Counting your own team.** Spot it: the north star tile jumps on the evenings you work.

## Check yourself

1. For each of your three tiles: the question it answers, in five words or fewer.
2. Does one person do every step of your funnel, or two? What did you do about it?
3. Which tile would you delete first if you could keep only two, and what does that tell you?
