# Experiment 1

**This is the Sakhli team's file.** Theirs lives at `03-build/experiments/experiment-1.md`; yours goes to the same path. Copy the shape, not the content.

**The drop this is about:** between the request and any answer: 11 requests, 6 answered, 5 silent.

**Baseline, measured before any change:** median 14 hours from request to answer, on 6 answered requests; 6 of 11 answered within 48 hours. Read from the `requests` table (query in the readout, section 4).

## The bet

| Part | Ours |
|---|---|
| Hypothesis | Hosts answer late mainly because they do not notice that a request has arrived. |
| Change | For 7 days, GT sends the host one WhatsApp message within 10 minutes of every request: "A guest has asked for dates on your Sakhli page." By hand. No code. |
| Metric | Hours from `created_at` to `confirmed_at` or `declined_at`, per request, median. Same query as the baseline. |
| Success threshold | Median under 4 hours, across at least 10 requests. |
| Failure threshold | Median still over 10 hours, or fewer than half of requests answered within 24 hours. |
| Decision rule | Success: build the automatic nudge in Sprint 3. Failure: noticing is not the problem; NK sits with one host, enters her notebook bookings into Sakhli by hand, and we test that for a week. Fewer than 10 requests: run 7 more days and claim nothing. |

**Who runs it:** GT · **Starts:** the morning after Lab 8 · **Ends:** 7 days later

**What we will not change while it runs:** the host page, the confirm button, the guest's on-screen confirmation. The guest email (S4b) ships only after the experiment ends.

**What we already suspect:** log 11 says one host noticed every request and still waited, because her older bookings are only in the notebook. If she is typical, this experiment fails, and the decision rule already says what we do then. We run it anyway: it costs nothing, and it tells us how many hosts are like her.

## Run log

- Day 1: 2 requests (Oni-1, Ambrolauri-1). Both messages sent inside 10 minutes. GT watched PostHog Activity from 09:00 to 22:00; a request at 23:40 was messaged at 08:05 next day and is marked late.

## Result (filled in when it ends, not before)

Not yet.
