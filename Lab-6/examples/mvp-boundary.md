# MVP Boundary

**This is the Sakhli team's file.** Theirs lives at `03-build/mvp-boundary.md`; yours goes to the same path. Copy the shape, not the content.

The smallest complete user journey that tests whether the product creates value. Complete: the person gets the value, start to finish. Smallest: nothing that is not on that path is in Sprint 1.

**Value hypothesis under test:** A host who confirms a guest's dates in one calendar, instead of across Booking.com, WhatsApp, and the notebook, will stop double-booking in peak season (problem statement, sentences 2 and 4; logs 01, 03, 07).

**The one person walking this journey:** Nino, 52, six rooms in Oni, Booking.com plus a WhatsApp number on a card, double-booked twice this season.

## The journey

1. Guest opens Nino's Sakhli link (from the card, an Instagram bio, or a WhatsApp forward)
2. Guest requests specific dates, nights, and party size, and leaves a way to be reached
3. Nino opens her private host link, sees the pending request, taps Confirm
4. Guest and Nino both receive the confirmation with the dates
5. The calendar blocks those dates, so nobody can request them again

**Why this is complete:** After step 5 one booking exists in exactly one place and cannot be sold twice, which is the thing Nino apologized for twice this season (log 01, log 07).

**Why this is smallest:** We considered removing step 4. Log 03's host calls guests back "so they know it is real"; without step 4 the guest still messages on WhatsApp, and the notebook comes back.

## Cut list

| Feature | Reason (cite the log, session, or hypothesis) | Comes back when |
|---|---|---|
| Online payment and deposit | The hypothesis is testable without money moving; 0 of 10 logs asked for payment, 3 mentioned cash on arrival as normal | After the Week 12 pricing test says anyone will pay through the app |
| AI reply drafter (Georgian and English) | Needs a calendar with real bookings to be grounded in; there is no calendar until step 5 ships and collects data | Week 10, built on break data |
| Guest reviews | 0 of 10 logs; reviews are Booking.com's job, not Nino's fear | Never, until a host asks |
| Booking.com channel sync | Tests nothing about direct bookings and rewards the channel Sakhli replaces | Only if hosts still run both channels after Week 12 |
| Multi-property management | Nino runs one house; every ICP host runs one house | If a Week 13 interview finds a two-house host who is otherwise ICP |
| Guest picks a room | Log 04 has the host choosing the room; invented by the tool in Week 4, deleted then, tried to come back | Never |
| Photo gallery | One photo on the link page is a field in S1; a gallery was asked for by nobody | If session logs show guests scrolling for photos |
| Host login with password | Nino does not use email (log 01); a private admin link reaches step 3 | Sprint 3, if a link ever leaks |
| Host stats dashboard | PostHog is the dashboard until a host asks for one; none has | When a host asks |
| In-app chat | WhatsApp exists and every host uses it (10 of 10 logs); Sakhli is not a messenger | Never |
| Map of Oni | Oni has one road | Never |

## Step to event

| Step | Event (actor_verb_object) | In the schema? |
|---|---|---|
| 1 | `guest_opens_host_link` | yes |
| 2 | `guest_requests_dates` | yes |
| 3 | `host_confirms_first_direct_booking` (first time) / `host_confirms_repeat_booking` (after) | yes |
| 4 | `system_sends_confirmation` | added today (fired by system; host_id, request_id, channel, recipient_role; owner LK) |
| 5 | `system_blocks_calendar` | added today (fired by system; host_id, request_id, ms_since_confirm; owner LK) |

**North star step:** 3

## The DECISIONS.md line

`Wk6 · MVP boundary: 5-step journey (guest opens link to calendar blocks dates); cut payments, AI drafter, reviews, channel sync, login · evidence: 03-build/mvp-boundary.md, logs 01, 03, 04, 07, sessions 1 to 3 · owner: NK`
