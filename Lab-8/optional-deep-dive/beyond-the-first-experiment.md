# Beyond the First Experiment (optional)

Nothing here is required for any grade. Read it if your readout is written, Experiment 1 is running, and you want to know what comes after.

## Why you are not running an A/B test

An A/B test shows a change to half your users and compares the halves. It needs enough people in each half that the difference is not luck, which usually means hundreds per side. With six users you do not have halves. What you are running instead is a before-and-after test: a baseline week, then a week with the change. It is weaker, because other things change between weeks too. That is why the template makes you write what you will not change while it runs, and why a result between your two thresholds counts as "unclear".

## Fake door, concierge, Wizard of Oz

Three named ways of testing a feature before building it.

A fake door is a button for a feature that does not exist; you count who taps it and tell them it is coming. It measures interest, never use.

A concierge test is you doing the job for the user openly, by hand. Entering a host's notebook bookings for her is a concierge test.

A Wizard of Oz test is you doing the job secretly behind the product. GT sending the nudge messages by hand is close to this. It measures real behaviour, at the cost of your evenings.

## Cohorts

When you have a few dozen users, stop reading totals and start reading groups by the week they arrived. A total can rise while every new group is doing worse than the last. In PostHog, a Retention insight is this view.

## Experiment 2

Write it only when Experiment 1 has a result. Its hypothesis should come from that result, or from a conversation the first one caused. A list of five experiments planned in advance is a roadmap in a lab coat.

## Feature flags

PostHog can switch a feature on for chosen users. When you do have enough people for halves, that is the tool. For now, know that it exists.
