# Reading Events and Reconciling

## The concept

An event in PostHog is a claim: this thing happened. Reading events means checking the claim one row at a time, in the Activity view. Reconciling means checking the total: counting the same thing in a second place, your own database, and requiring the two counts to match before you believe either.

Four checks on a row. The name matches your schema, character for character. Every property in the schema row is present. It fired once per action. It came from production, through the library you expected (`posthog-js` from a browser, `posthog-node` from a server).

One check on a total. PostHog count equals database count, same window. Equal, or you do not have a north star yet.

## Why it matters

Analytics fails without an error message. In 2016, Facebook told advertisers that for about two years it had overstated the average time people spent watching videos. The metric divided total watch time by the number of views longer than three seconds, instead of by all views, so every short view vanished from the denominator. Nothing crashed. Dashboards looked healthy. Budgets moved on the strength of the number. It was caught only when the figure was compared against a different way of counting the same thing.

If a company with thousands of engineers can run a wrong number for two years, a team of three can run one for a week. The defence is the same at any size: count it twice.

## Worked example, step by step

Sakhli, Lab 7, checkpoints 1 and 2.

Step one: two people, two screens. LK does the action on a phone at the production URL. NK has PostHog open on Activity, with the Live events tab showing rows as they arrive.

Step two: LK requests dates. NK reads the row aloud. Name: `guest_requests_dates`, identical to the schema. Properties: `host_id`, `request_id`, `nights`, `party_size`, all present. Once. Library `posthog-js`, production path. NK writes `yes` in the schema's `Live` column.

Step three: LK confirms as the test host. Two rows named `host_confirms_first_direct_booking` arrive a second apart. One says `posthog-node`. One says `posthog-js`. The library column has just found the bug: something in the browser is firing an event that should only come from the server.

Step four: reconcile, to measure it. NK opens a Trends insight, total count of the two confirm events, since the deploy: 6. LK runs one query in the database's SQL editor, confirmed rows since the deploy: 3. Exactly double.

Step five: GT searches the code for the event name and finds a capture call left in the Confirm button from the prototype. Deleted, committed, deployed.

Step six: three new confirms on the test house. PostHog 3, database 3. Both pairs of numbers go into the Gate reconcile block. The wrong pair stays in the file: it is the evidence that the check works.

Step seven: the filter. In PostHog, Settings, Project, Filter out internal and test users: `host_id is not h_test`, and `Host does not contain localhost`. Enabled on all new insights. From now on the team's own clicks appear in Activity and count in nothing.

## Common mistakes and how to spot them

**Nothing arrives in production; localhost is fine.** The key is missing in the host's settings, or was added with no redeploy, or the region in the host variable does not match the project. Spot it: in the phone's or laptop's browser console, `posthog.get_distinct_id()` returns a string if init ran.

**Two events with nearly the same name.** Typed, not copied. Spot it: the event list in PostHog shows both. Fix the string in code, and hide the stray name in Data management.

**Exactly double, or climbing on refresh.** A capture in the component body or in an effect that reruns. Spot it: reload the page five times and count rows.

**Browser events arrive, server events do not.** The route returned before the events left. Spot it: `await posthog.flush()` is missing before the `return`.

**Reconciling different windows.** PostHog set to the last 7 days, the query counting all time. Spot it: write the start and end beside both numbers.

**Reconciling with the internal filter on.** Your test confirms are filtered out of PostHog and still in the database. Spot it: for a reconcile on your test record, turn the insight's filter off; for real users, exclude the test record in the query too.

**Declaring the database right.** Usually it is. But a server event that fires before a write fails, or a row deleted by hand, makes the database the wrong one. A mismatch is a question, not a verdict.

## Check yourself

1. For your north star event: which library should the row show, and why that side?
2. Write your reconcile as two lines: the insight you will open and the query you will run, with the same window in both.
3. What is your team's test record, and what exact filter keeps it out of your tiles?
