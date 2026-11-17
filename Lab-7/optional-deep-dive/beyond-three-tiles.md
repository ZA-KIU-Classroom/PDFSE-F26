# Beyond Three Tiles (optional)

Nothing here is required for any grade. Read it if your three tiles are built, your count reconciles, and you want to know what else the tool can do.

## Step counts by a shared id

A funnel follows one person. When a guest starts a journey and a host finishes it, nobody completes the funnel. Besides showing step counts side by side, you can set a funnel to aggregate by a SQL expression on an id that every step carries, for example `properties.host_id`. The funnel then reads "hosts whose link was opened, hosts who received a request, hosts who confirmed". That is a different and often more useful question than the per-guest one. Try it once you have more than a handful of hosts; with four, the counts tell you the same thing.

## Autocapture

`posthog-js` records clicks and page views without any code from you. Leave it on: it costs nothing and sometimes answers a question you did not plan for, such as which button people tap before giving up. It never replaces a named event from your schema. Autocaptured clicks are named by the page's markup, which changes every time you restyle a button.

## Session replay

Replay records what a person saw and did, as a video-like reconstruction. It is the most persuasive evidence there is for a usability problem, and it captures whatever is on the screen, including what people type. If you turn it on: mask every input, say so in your privacy line, and tell your field-week people before they start. Do not turn it on quietly this week.

## Feature flags

A flag lets you ship code that is off for everyone except the people you choose. In Lab 8 you design an experiment; a flag is the usual way to show a change to half your users. With five users you do not have halves. Know that it exists, and come back to it when you have fifty.

## The SQL editor

PostHog can run SQL over your events. One query worth saving now, because it becomes your reliability measure in Lab 9: the distribution of a timing property.

```sql
select quantile(0.5)(toFloat(properties.ms_since_confirm)) as median_ms,
       quantile(0.99)(toFloat(properties.ms_since_confirm)) as p99_ms,
       count() as n
from events
where event = 'system_blocks_calendar'
```

Swap in your own event and timing property. If you have no timing property on any event, that is worth one line in your schema this week.

## Alerts

A Trends insight can notify you when a number crosses a threshold. One alert earns its place in a field week: your north star event count going above zero for a real user. You will open the dashboard less, and you will know the minute it matters.
