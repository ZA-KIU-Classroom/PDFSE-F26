# Event Schema

**This is the Sakhli team's file.** Theirs lives at `03-build/analytics/event-schema.md`; yours goes to the same path. Copy the shape, not the content.

Your metric is only as good as your instrumentation. Every row here becomes one `capture()` call in Week 7 and one dashboard tile. Names are copied from this file, never retyped.

**North star:** Confirmed direct bookings per active host per month.

**North star event:** `host_confirms_first_direct_booking`

**How the north star is computed from events:** count of `host_confirms_first_direct_booking` plus count of `host_confirms_repeat_booking`, per host with at least one confirm in the window, per calendar month.

## Events

| Step | Event (actor_verb_object) | Fired by | Properties | Owner |
|---|---|---|---|---|
| Acquisition | `guest_opens_host_link` | guest | host_id, source (card, instagram, whatsapp, other) | GT |
| Activation (precursor) | `guest_requests_dates` | guest | host_id, request_id, nights, party_size | GT |
| Activation (north star) ★ | `host_confirms_first_direct_booking` | host | host_id, request_id, nights, is_first_for_host | NK |
| Retention | `host_confirms_repeat_booking` | host | host_id, request_id, days_since_last_confirm | NK |
| Activation (failure path) | `host_declines_request` | host | host_id, request_id, reason (full, dates, other) | NK |

Referral and Revenue are empty on purpose. There is nothing to refer and nothing to pay for before Week 12.

## Rules we are following

- One name per event, one spelling, lowercase with underscores.
- `host_id` on every event. It is an id our app made up. No names, phone numbers, or message text anywhere in analytics.
- The north star event is fired by the host, because the host receives the value and the host is who the problem statement is about.
- `guest_requests_dates` stays in the schema as a precursor so that when confirms are low we can see whether demand or response time is the problem.

## Reconcile plan

**Event most likely to fail silently:** `host_confirms_first_direct_booking`
**How it would fail:** double fire; the confirm screen re-renders after the tap and the capture call is on the render, not the tap.
**The check that would catch it:** count confirmed bookings in our own database for the same week and compare to the event count. If the event count is about double, it is the render.
**Who runs the check in Week 7:** NK, in the lab, before the gate is confirmed.
