# Sprint 2: the field week

**This is the Sakhli team's file.** Theirs lives at `03-build/sprints/sprint-2.md`; yours goes to the same path. Copy the shape, not the content.

Sprint 2 runs from Lab 7 to Lab 8. Real people use the product this week, and Lab 8 opens by reading what they did.

## Sprint 1 review

Our definition of done: merged to `main`, deployed at the public URL, walked on a phone by a teammate who did not build it, events in PostHog's Activity view.

| Story | Owner | Done by our definition? | If not: which clause is missing, and what happened |
|---|---|---|---|
| S1 Guest opens the link | GT | Yes | Walked by LK |
| S2 Guest requests dates | GT | Yes | Walked by NK |
| S3 Host confirms | NK | Yes, after one trip back to doing | GT's walk found the Confirm button below the fold on a small phone; fixed, walked again |
| S4 Confirmation to both, calendar blocks | LK | Partly | Calendar block and `system_blocks_calendar` are done and walked. The guest's email is not built: "deployed" is missing for that half |
| S5 Deploy and instrument | NK | Yes | Done on the first evening; reconcile needed a second try (see the schema file) |

**Slip rule:** fired, as written. The guest's email moved to Sprint 2; the guest sees the confirmation on screen only. The calendar block stayed in S4.

## The gate

| Rung | Reached? | Evidence: a link or a number | If not: owner, and by when |
|---|---|---|---|
| 1 Production URL loads on a phone | Yes | Live product row in README | |
| 2 Journey completes there | Yes | LK's walk in the lab, request `r_0431` on the test house | |
| 3 North star event in Activity, from production | Yes | Library `posthog-node`, production path, seen by NK | |
| 4 Counts reconcile | Yes | PostHog 3 = database 3, after the double-fire fix | |
| 5 Dashboard, linked in README | Yes | Analytics dashboard row in README, three tiles | |

## Real hours before Lab 8

| Initials | Hours free | When, specifically |
|---|---|---|
| NK | 5 | Tue 20:00 to 22:00, Sun 10:00 to 13:00 |
| GT | 6 | Mon, Wed, Sat evenings, 2h each |
| LK | 4 | Wed 20:00 to 22:00, Sat 15:00 to 17:00 |
| **Total** | **15** | |

## Stories this week

### S6 · Host declines a request · owner NK · reviewer GT · 3 h

**As** a host with a request for dates I cannot take, **I** decline with one tap and a reason **so that** the guest is not left waiting and the request stops sitting in my list.

- Given my private link with one pending request, when I tap Decline and pick `full`, `dates`, or `other`, then the request shows Declined
- And the dates stay open for other guests
- And `host_declines_request` fires once from the server with `host_id`, `request_id`, `reason`

Why now: two of three real requests are still pending, and a host has no way to say no.

### S4b · Guest gets the confirmation by email · owner LK · reviewer NK · 3 h

Slipped from Sprint 1. Done when a confirmed guest receives one email with the house name and dates, and `system_sends_confirmation` fires with `channel` = `email`, `recipient_role` = `guest`.

### F1 · Four link cards, printed and delivered · owner NK · reviewer LK · 2 h

One card per host, each with that host's guest link ending in `?src=card`. LK scans each card on a phone before it leaves the house. Done when four cards are with four hosts and each host has opened their private link once with NK on the phone.

### F2 · Mid-week look · owner GT · 1 h

Sum: 9 of 15 hours. The other six are held for whatever the first real users break.

## Field week: who uses it

| Code name and role | Log or session they come from | How the link reaches them | Sent by, and by when | Opened? (fill in during the week) |
|---|---|---|---|---|
| Oni-1, host, 6 rooms | Log 01, prototype session 1 | Printed card, delivered in person | NK, done | Yes; she forwarded the guest link on WhatsApp herself |
| Oni-2, host, 4 rooms | Log 03 | Printed card, in person | NK, Sunday | |
| Ambrolauri-1, host, 8 rooms | Log 05, prototype session 3 | WhatsApp message with both links, then a call | GT, Monday | |
| Oni-3, host, 5 rooms | Log 07 | Her nephew opens it with her on her phone; printed card | LK, Wednesday | |

**What we tell them:** "This is the booking page we showed you, now working. Give this link to a guest instead of taking the dates by message. You will see the request here and confirm with one tap. It is a student project; we count visits and bookings, never names."

## Prediction

**By Lab 8:** 3 confirmed direct bookings (`host_confirms_first_direct_booking` plus `host_confirms_repeat_booking`) from real hosts, not our test house. Also: 4 hosts open their private link, 6 guest requests.

**We are wrong if:** fewer than 2 hosts confirm anything.

**Mid-week look:** GT opens the dashboard on Wednesday evening and writes one line here.

## The DECISIONS.md line

`Wk7 · Gate passed: live at the README's Live product link, north star event firing from production, PostHog 3 = database 3 · evidence: README links, 03-build/analytics/event-schema.md · owner: NK`
