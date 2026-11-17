# Homework 2 · GT (@gt-sakhli) · Sakhli

**This is one Sakhli teammate's file.** Theirs lives at `members/gt-sakhli/hw2.md`; yours goes to `members/<your-github-username>/hw2.md`. Copy the shape, not the content. Commit hashes here stand in for full links; yours are full links.

## 1. Ship report

| What I shipped | Story or rung | Commit link(s), from my account | Live at the production URL? | Walked or checked by |
|---|---|---|---|---|
| Guest link page: house name, one photo, date picker that refuses blocked dates | S1 | `a41c7e2`, `b09d3f1` | Yes | LK |
| Request form and the `guest_requests_dates` capture, after the server's OK | S2 | `c77e120` | Yes | NK |
| Deleted the leftover capture call in the Confirm button | Rung 4 | `3f2a91c` | Yes | NK reran the reconcile: 3 and 3 |
| Walked S3 on my phone and sent it back: Confirm was below the fold | S3 (as reviewer) | `d5e8a44` (my note in `sprint-1.md`) | Yes, after NK's fix | Me, twice |
| Session 4 of our frozen test, run on the deployed first screen and logged | Test plan, session 4 | `e2b6f90` | n/a | LK read the log |

**The piece I am least sure works for a real person, and how I will know by Lab 8:** the date picker on an older Android phone. Ambrolauri-1's guests are mostly on older phones. I will look at `guest_opens_host_link` against `guest_requests_dates` for her `host_id` on Wednesday: opens with no requests means the picker, and I will call her.

**One thing I did that was not my assigned story:** the double-fire fix. The confirm was NK's story, but the stray call was mine, left over from the prototype. I found it by searching the code for the event name after the reconcile came back 6 against 3.

## 2. Pattern journal, Weeks 5 to 7

### Week 5 · One metric that matters

I argued for "hosts signed up" as our north star because it was the number I thought we could move fastest. NK pointed out that a host can sign up and never confirm one booking; Oni-3 has three apps her nephew installed and uses none. I lost the argument, and correctly. Beyond my lane: I wrote the `source` property into the schema after noticing we had no way to tell the card from Instagram. My hack: I tested the prototype with my landlord before any host, to find the embarrassing bugs first.

### Week 6 · The smallest complete journey

I cut the photo gallery, which I had already half built. That was the hard one, because it was the best-looking thing we had. The reason in the cut list is mine: one photo is a field, and a gallery was asked for by nobody in ten logs. Beyond my lane: I sized LK's story with him when his first estimate was two hours for email plus calendar. My hack: a plain HTML date input for two days, so S2 could be walked before the real picker existed.

### Week 7 · Ship to learn

The request from Oni-1's cousin taught me more than my own testing did. I had assumed guests arrive from the card. The first real one arrived from WhatsApp, and we only know because of the `source` property. Beyond my lane: I ran the search that found the double-fire. My hack: I did not write this entry in its own week; I am writing it the day after the lab, and it shows.

## 3. My DECISIONS.md lines

> `Wk5 · North star: confirmed direct bookings per active host per month; rejected app downloads (presence, cumulative) and hosts signed up (presence) · evidence: 03-build/analytics/event-schema.md, 01-discovery/interview-logs/01-host-oni.md, 03-host-oni.md, 07-host-oni.md · owner: NK`

I am not the owner, but one rejected decoy was my proposal, and the line records why it lost: it counts presence, not value delivered.

> `Wk7 · North star fires from the server only; removed the capture call left in the Confirm button after PostHog 6 against database 3 · evidence: 03-build/analytics/event-schema.md (Gate reconcile), commit 3f2a91c · owner: GT`

The evidence is the two counts before the fix and the two counts after it, both kept in the schema file.

## 4. My person this week

**The field-week person I am responsible for:** Ambrolauri-1, host, 8 rooms · **how and when the link reaches them:** a WhatsApp message with both links on Monday, then a call the same evening to open the private link together.
