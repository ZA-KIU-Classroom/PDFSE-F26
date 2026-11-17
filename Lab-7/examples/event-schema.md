# Event Schema

**This is the Sakhli team's file as it stands after Lab 7.** Theirs lives at `03-build/analytics/event-schema.md`; yours goes to the same path. What Lab 7 added: the `Live` column, and the Gate reconcile block at the bottom. Copy the shape, not the content.

**North star:** Confirmed direct bookings per active host per month.

**North star event:** `host_confirms_first_direct_booking`

**How the north star is computed from events:** count of `host_confirms_first_direct_booking` plus count of `host_confirms_repeat_booking`, per host with at least one confirm in the window, per calendar month.

## Events

| Step | Event (actor_verb_object) | Fired by | Properties | Owner | Live |
|---|---|---|---|---|---|
| Acquisition | `guest_opens_host_link` | guest (browser) | host_id, source (card, instagram, whatsapp, other) | GT | yes |
| Activation (precursor) | `guest_requests_dates` | guest (browser, after the server says OK) | host_id, request_id, nights, party_size | GT | yes |
| Activation (north star) ★ | `host_confirms_first_direct_booking` | host (server, after the update returns a row) | host_id, request_id, nights, is_first_for_host | NK | yes |
| Retention | `host_confirms_repeat_booking` | host (server) | host_id, request_id, days_since_last_confirm | NK | yes |
| Activation (failure path) | `host_declines_request` | host (server) | host_id, request_id, reason (full, dates, other) | NK | no: the decline button is Sprint 2, story S6 |
| Journey step 4 | `system_sends_confirmation` | system (server) | host_id, request_id, channel, recipient_role | LK | yes, with channel `screen` only; `email` is Sprint 2, story S4b |
| Journey step 5 | `system_blocks_calendar` | system (server) | host_id, request_id, ms_since_confirm | LK | yes |

## Reconcile plan (written in Lab 5)

**Event most likely to fail silently:** `host_confirms_first_direct_booking`
**How it would fail:** double fire; the confirm screen re-renders after the tap and the capture call is on the render, not the tap.
**The check that would catch it:** count confirmed bookings in our own database for the same week and compare to the event count. If the event count is about double, it is the render.
**Who runs the check in Week 7:** NK, in the lab, before the gate is confirmed.

## Gate reconcile (Lab 7)

**Production URL walked:** the Live product link in our README, path `/h/test-house` · **walked by:** LK (did not build S1 to S3) · on a phone, mobile data: yes

| Source | Count | Window | Exactly how it was counted |
|---|---|---|---|
| PostHog | 3 | From the fix commit to the end of the lab | Trends insight, total count of `host_confirms_first_direct_booking` plus `host_confirms_repeat_booking`, internal filter off |
| Database | 3 | Same | `select count(*) from requests where status = 'confirmed' and confirmed_at > '<time of the fix commit>';` |

**Match:** yes, on the second try.

**If no, first:** PostHog 6, database 3. Exactly double. A `posthog.capture` call left over from the prototype was still in the Confirm button's click handler, and the confirm route on the server fired as well. GT deleted the call in the button (commit `3f2a91c`). Three new confirms after the fix: PostHog 3, database 3.

**Silent failure we predicted in Lab 5:** double fire on the confirm. **Did it happen?** Yes, though not from a re-render as predicted: from two capture calls, one on each side. The check we had written caught it anyway.

**Internal filter set in PostHog:** `host_id is not h_test`, and `Host does not contain localhost`; enabled on all new insights and checked on all three tiles. **Our test record is:** the host `h_test` at `/h/test-house`. Nobody on the team clicks on a real host's link.

**Checked by:** NK · **events still not Live, with owner and by when:** `host_declines_request`, NK, by the Tuesday before Lab 8; `system_sends_confirmation` with channel `email`, LK, by the Wednesday before Lab 8.
