# Beyond the North Star

Not required, not graded. For teams who want to see where this week's ideas go once a product has more than five users.

## Input metrics and the tree under the star

A north star is a single output. It is usually too slow to steer by day to day, because it moves only when a user gets value, and in a pilot that might be twice a week. Mature teams draw a tree: the north star at the top, and under it the three or four inputs that move it. For Sakhli: hosts with a live link, requests per host per month, confirm rate within 24 hours, repeat rate. Each input is faster-moving and more directly in the team's control than the star itself. The discipline is that every input must demonstrably move the star; an input that goes up while the star stays flat is a vanity metric wearing a tree.

## Cohorts, properly

The rows-not-a-total slide in the Week 5 session is the simplest cohort view: one row per user, one column per week since activation. The general version groups users by the week they activated and tracks each group forward. It answers a question totals hide: are later cohorts retaining better than earlier ones? If they are, the product is improving. If every cohort decays the same way regardless of what the team shipped, the team is shipping things that do not matter. PostHog draws this for you in Week 7; the value is in reading it, not building it.

## Leading, lagging, and the time-to-value question

Retention is lagging: you learn a host has churned only after she has been silent for weeks. Teams look for a leading signal, something in the first session that predicts retention. For Sakhli the candidate is time to first confirm: hosts who confirmed a real request within three days of getting their link may retain far better than hosts who waited two weeks. If that holds, the team has a lever: get the first request in front of the host fast. The schema already captures what is needed to test it (first confirm timestamp against link creation), which is one more argument for writing the schema before the code.

## Why five users, and when five is not enough

The five-user figure comes from usability research in the 1990s showing that the first five testers surface most of the problems in a single flow, with steeply diminishing returns after. It holds for finding what is broken in one task. It does not hold for estimating how common a behavior is, for comparing two designs, or for a product with several distinct user types. If your ICP has two genuinely different kinds of user (a host and a guest), five of each. If you want to know whether a version is better, not just whether it breaks, you need more sessions than any single lab week allows, and that is Week 10's experiment design.

## When the north star should change

A north star is a decision, and the Evidence Rule applies: changing it is a DECISIONS.md line with evidence. Legitimate reasons: the product pivoted and value now lands somewhere else; the metric turned out to be gameable or unmeasurable in practice; a leading indicator proved so reliable that steering by it is faster. Illegitimate reason: the number is low and a different number would look better. The reconcile habit protects against the first kind of problem; honesty protects against the last.
