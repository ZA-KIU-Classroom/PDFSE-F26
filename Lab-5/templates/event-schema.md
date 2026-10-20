# Event Schema

**Save this file as:** `03-build/analytics/event-schema.md`
**Filled-in example:** `Lab-5/examples/event-schema.md` (Sakhli)

Your metric is only as good as your instrumentation. Every row here becomes one `capture()` call in Week 7 and one dashboard tile. Names are copied from this file, never retyped.

**North star:** [the sentence from your worksheet, word for word]

**North star event:** `[actor_verb_object]`

**How the north star is computed from events:** [for example: count of X plus count of Y, per person with at least one X in the window, per month]

## Events

Four to six rows this week. Fill only the AARRR steps your product can fire before Week 7. An empty step is honest; an invented event is a lie you will delete later.

| Step | Event (actor_verb_object) | Fired by | Properties (never a name, phone, email, or message text) | Owner |
|---|---|---|---|---|
| Acquisition | | | | |
| Activation (precursor) | | | | |
| Activation (north star) ★ | | | | |
| Retention | | | | |
| | | | | |

## Rules we are following

- One name per event, one spelling, lowercase with underscores.
- `[your internal id property]` on every event. Nothing that identifies a real person.
- The north star event is fired by the person who receives the value.

## Reconcile plan

Before we believe the dashboard, we count the north star event a second way.

**Event most likely to fail silently:** `[event]`
**How it would fail:** [never fires / name mismatch / double fire / blocked]
**The check that would catch it:** [for example: count confirm rows in our database for the same week and compare]
**Who runs the check in Week 7:** [initials]
