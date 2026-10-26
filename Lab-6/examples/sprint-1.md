# Sprint 1

**This is the Sakhli team's file.** Theirs lives at `03-build/sprints/sprint-1.md`; yours goes to the same path. Copy the shape, not the content.

## Definition of done

A story is done when it is merged to `main`, deployed at the public URL, walked on a phone by a teammate who did not build it, and its events show in PostHog's Activity view.

## Real hours before the Week 7 lab

| Initials | Hours free | When, specifically |
|---|---|---|
| NK | 6 | Tue and Thu evenings 20:00 to 22:00, Sun 10:00 to 12:00 |
| GT | 8 | Mon, Wed, Fri, Sat evenings, 2h each, hard stop |
| LK | 5 | Sat 14:00 to 18:00, Wed 21:00 to 22:00 |
| **Total** | **19** | |

## The board

GitHub Projects on the team repo, linked from the README. Columns: next, doing, review, done. One card per story. Merge to `main` every day anyone works.

## Stories

### S1 · Guest opens Nino's link · owner GT · reviewer LK · 4 h

**As** a guest who found Nino's link on her card, **I** open it on my phone and see her house and which dates are free **so that** I do not have to message three apps to find out.

**Acceptance criteria:**
- Given the link `/h/nino-oni` on a phone browser, when it loads, then I see the house name, one photo, and a date picker, with no pinch-zoom needed
- And dates already in `blocked_dates` cannot be selected
- And `guest_opens_host_link` fires once per load with `host_id` and `source` (from `?src=card`, `instagram`, `whatsapp`, or `other`)

**Smallest demo that proves it:** open the link on a phone with `?src=card`, show the picker refusing a blocked date, show the event.

### S2 · Guest requests dates · owner GT · reviewer NK · 4 h

**As** a guest, **I** request specific dates **so that** Nino sees my request without me chasing her on three apps.

**Acceptance criteria:**
- Given the link page, when I pick 14 to 16 Aug, 2 people, enter a first name and one contact, and tap Request, then I see "Sent. Nino will confirm." with my dates
- And a `requests` row exists with status `pending` and those fields
- And `guest_requests_dates` fires with `host_id`, `request_id`, `nights`, `party_size`

**Smallest demo that proves it:** request dates on a phone, show the row, show the event.

### S3 · Nino confirms · owner NK · reviewer GT · 5 h

**As** Nino, **I** see every pending request in one place and confirm with one tap **so that** I never say yes to the same dates twice.

**Acceptance criteria:**
- Given my private link `/h/nino-oni/admin/TOKEN` with one pending request, when I tap Confirm, then the request shows Confirmed with the guest's first name and dates
- And the `requests` row status is `confirmed`
- And `host_confirms_first_direct_booking` fires (`is_first_for_host` true) the first time, `host_confirms_repeat_booking` after

**Smallest demo that proves it:** confirm on a phone, show the row, show the event.

### S4 · Confirmation to both, calendar blocks · owner LK · reviewer NK · 4 h

**As** Nino and as the guest, **we** both get the confirmation and the dates close **so that** the booking exists in one place and cannot be sold twice.

**Acceptance criteria:**
- Given a request just confirmed, when the confirm completes, then Nino's screen shows the confirmed state and the guest's contact receives an email with the house name and dates
- And the date range is in `blocked_dates`; reloading the guest link shows those dates unselectable; a new request for 15 Aug is refused
- And `system_sends_confirmation` fires once per recipient with `channel` and `recipient_role`, and `system_blocks_calendar` fires with `ms_since_confirm`

**Smallest demo that proves it:** confirm, open the guest link, try to request 15 Aug, show both events.

### S5 · Deploy and instrument · owner NK · reviewer LK · 2 h

First, not last: `Lab-6/setup/SHIP-STACK-SETUP.md` on the first evening, so S1 to S4 deploy the day they merge. Public URL in the README, five events visible in Activity, reconcile check written. Week 7 adds the dashboard.

## Slip rule

Written now, obeyed later. If S4 is not done by the Wednesday evening before the Week 7 lab, the guest's email moves to Sprint 2 and the guest gets the confirmation on screen only; the calendar block and `system_blocks_calendar` stay in S4 no matter what, because without them the value does not land.

## The DECISIONS.md lines

The boundary line is in `03-build/mvp-boundary.md`. The Sakhli team had a prototype and three sessions before this lab, so no prototype-track line was needed.
