# Prototype Test Plan

**This is the Sakhli team's file.** Theirs lives at `02-design/user-testing/test-plan.md`; yours goes to the same path. Copy the shape, not the content.

**Prototype v1 link:** (the same link as the Prototype row in the team README; a phone-sized clickable flow, five screens)

**Riskiest assumption under test:** A host will confirm a booking on her phone instead of answering on WhatsApp and writing it in the notebook.

## The frozen test (copied from `02-design/prototype-plan.md`, section 5, unchanged)

**Task, read aloud word for word:** "A family just asked for 14 to 16 August. Show me what you would do."

**Success:** Finds the request and taps confirm within 60 seconds, without asking us anything.

**Failure behaviors:**
1. Opens WhatsApp instead.
2. Asks what to press.
3. Taps the guest's button.
4. Reaches for the notebook and says she would not trust the screen.

**Decision rule (out of 5):** 3 or more fail: the assumption is weakened. Before building anything else, test a version where the confirmation arrives inside WhatsApp.

**Predicted first mistake:** Taps Request dates, the guest's button.

## Five testers

| # | Code name | Role | Why they fit the ICP | Runner | Logger | Target day | Status |
|---|---|---|---|---|---|---|---|
| 1 | Oni-1 | Host, 6 rooms, Oni | Log 01. Booking.com plus WhatsApp, double-booked this season | NK | GT | Lab week, Wed | done |
| 2 | Oni-3 | Host, 4 rooms, Oni | Log 03. Paper notebook by the phone, 3am phone checks | NK | GT | Lab week, Thu | booked |
| 3 | Amb-5 | Host, 8 rooms, Ambrolauri | Log 05. Calls the neighbor before answering when full | GT | LK | Lab week, Sat | booked |
| 4 | Mes-9 | Host, 5 rooms, Mestia | New; introduced by Oni-1. Two channels, no son who writes English | LK | NK | Following week, Mon | messaged |
| 5 | Oni-7 | Host, 3 rooms, Oni | Log 07. Refunded a family after a double-book | GT | LK | Following week, Tue | messaged |

## Session protocol (same every time)

1. The tester opens the link on their own phone. Not yours.
2. The runner reads the task word for word, then says nothing.
3. The logger starts the timer on the last word of the task and writes: time to first tap, time to the one action, every unprompted sentence verbatim.
4. When the tester stops, or at 3 minutes, the runner asks one question only: "What were you expecting to happen?"
5. The logger writes the verdict against the rule before anyone discusses the session.
