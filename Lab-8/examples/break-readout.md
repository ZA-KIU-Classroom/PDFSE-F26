# Field-week readout

**This is the Sakhli team's file.** Theirs lives at `03-build/analytics/break-readout.md`; yours goes to the same path. Copy the shape, not the content.

**Our state:** A: real people used it.

## 1. Is it real?

| Source | Count of `host_confirms_first_direct_booking` plus `host_confirms_repeat_booking` | Window | How it was counted |
|---|---|---|---|
| PostHog | 4 | Lab 7 to Lab 8 | Trends insight, total count, internal filter on (`host_id is not h_test`) |
| Database | 4 | same | `select count(*) from requests where status = 'confirmed' and host_id <> 'h_test' and confirmed_at > '<end of Lab 7>';` |

**Match:** yes. Checked by NK.

## 2. Prediction against reality

**Our prediction, pasted from `sprint-2.md` exactly as committed:** By Lab 8: 3 confirmed direct bookings from real hosts, not our test house. Also: 4 hosts open their private link, 6 guest requests. We are wrong if: fewer than 2 hosts confirm anything.

| What we predicted | Predicted | Real |
|---|---|---|
| Confirmed direct bookings | 3 | 4 |
| Guest requests | 6 | 11 |
| Hosts who opened their private link | 4 | 3 |

**Did "we are wrong if" fire?** No. 2 hosts confirmed. One fewer and it would have.

## 3. Where people stop

| Journey step | Count, real people only |
|---|---|
| `guest_opens_host_link` | 23 (whatsapp 14, card 6, instagram 2, other 1) |
| `guest_requests_dates` | 11 |
| Confirmed (`host_confirms_first_direct_booking` 2, `host_confirms_repeat_booking` 2) | 4 |
| `host_declines_request` (live since Tuesday) | 2 |
| No answer after 48 hours (requests still `pending`) | 5 |

**Widest drop:** between the request and any answer: 11 requests, 6 answered, 5 silent.

## 4. Who is standing at the drop

**The actor:** the host.

| Host | Requests received | What she did | What she did not do |
|---|---|---|---|
| Oni-1 | 5 | Confirmed 3, declined 1 | Answered 1 |
| Ambrolauri-1 | 3 | Confirmed 1, declined 1 | Answered 1 |
| Oni-2 | 3 | Opened her private link once, with NK | Answered any |
| Oni-3 | 0 | Nothing | Opened her private link; no guest ever saw her page |

**One timing that sizes the drop:** hours from request to answer, for the 6 answered: fastest 40 minutes, median 14 hours, slowest 31 hours. From `select extract(epoch from (coalesce(confirmed_at, declined_at) - created_at)) / 3600 from requests where status <> 'pending' and host_id <> 'h_test';`

## 5. What the data refuses to say

| Question | Who we ask | Asked by, and by when |
|---|---|---|
| Why did Oni-2 answer none of three requests? | Oni-2 | NK, done: log 11. "I saw them come. I wanted to check the notebook first, in the evening. Then it was the next day." |
| Did Oni-3 reject the product or never see it? | Oni-3 | NK, done: log 12. "My nephew was going to show me. He went back to Tbilisi on Sunday." |
| Did the 5 silent guests book somewhere else? | Two of the guests, through the contact they left | GT, by Friday |

## 6. Claims

**Direction:** Hosts answer more slowly than guests ask: 11 requests in a week, a 14 hour median to answer, 5 never answered. Guests arrive without us: 14 of 23 opens came from a WhatsApp forward the team did not send.
**Not yet:** "Hosts do not notice requests." Oni-2 noticed all three and still did not answer; we have asked one host of four.

## 7. What changes

**Comes off the plan:** the Instagram door and the photo gallery. 23 opens and 11 requests from three hosts say guests are not the scarce side.
**Goes on:** host response time. 5 of 11 requests unanswered.

`Wk8 · Field-week read: predicted 3 bookings, real 4; widest drop after the request (5 of 11 unanswered), actor: host; Instagram door and gallery back on the cut list, host response time next · evidence: 03-build/analytics/break-readout.md, 01-discovery/interview-logs/11-host-oni.md, 12-host-oni.md · owner: NK`

## 8. Who is next

**Our field table as a funnel:** asked 4 · link delivered 4 · private link opened 3 · got a request 3 · answered at least one 2

| Next person | Channel, and our evidence for it | Sent by | Sent in the lab? |
|---|---|---|---|
| Oni-3, host (second try) | In person. Both hosts who confirmed were set up face to face. | NK, Thursday | Yes: asked for a time |
| Oni-4 and Oni-5, hosts | Introduced by Oni-1. Hosts forward things to each other: 14 of 23 opens. | NK | Yes: asked Oni-1 for the two names |
| Ambrolauri-2 and Ambrolauri-3, hosts | Introduced by Ambrolauri-1. Same evidence. | GT | Yes |
| Guesthouse association, Ambrolauri | One mention in log 05. Weak evidence, one message. | LK | Yes |

**The exact message we sent (to a host named by Oni-1):** "Hello, I am NK. [Host] in Oni gave me your number. She took three guest bookings last week through a page we set up on her phone. Can I come by on Thursday for ten minutes and set up yours?"

**Target before Lab 9:** 6 new hosts holding a working link.
