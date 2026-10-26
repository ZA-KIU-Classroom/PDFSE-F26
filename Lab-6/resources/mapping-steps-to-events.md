# Mapping Steps to Events

## The concept

The boundary says what you build. The event schema from Lab 5 says what you can read. The mapping puts the two side by side: one row per journey step, with the event that fires when a person completes it. A step with no event is a step you will not be able to see over the break. An event with no step is either a precursor or failure path that belongs in the schema anyway, or a wish.

The rule is short. A journey step with no event is not done. An event with no journey step is a rumor. Every gap gets closed in one of two directions: add the event with its four parts, or cut the step.

## Why it matters

Over the exam break your product is live and nobody is watching it. The only record of what happened is the events. If the host's confirmation fires an event but the calendar block does not, you will come back in Week 10 knowing how many bookings were confirmed and not knowing whether any of them were actually protected from double-booking, which is the whole value hypothesis. The step that mattered most will be invisible.

The failure story is from Spring. A team building a food-order tool for a university canteen instrumented the order submission and nothing after it. The break data showed eighty-one orders submitted. They presented it as traction. In Week 11, preparing the quality audit, one teammate checked the kitchen's own records: thirty-four of the eighty-one orders had never been marked ready, because the kitchen's screen had a bug that hid orders placed after 13:00. A healthy-looking funnel, a product failing almost half its users at the value step, and no event there to say so.

A row for "kitchen marks order ready" would have shown the gap in Week 6.

## Worked example, step by step

Sakhli, Lab 6, checkpoint 1.

Step one: write the journey in the left column. Five steps: guest opens link, guest requests dates, host confirms, both receive confirmation, calendar blocks dates.

Step two: open the Lab 5 schema and copy, never retype, the event beside each step it already covers. Steps one, two, and three match `guest_opens_host_link`, `guest_requests_dates`, and `host_confirms_first_direct_booking` (with `host_confirms_repeat_booking` for later confirms). Three rows filled.

Step three: mark the gaps. Steps four and five have nothing. Both are system actions, which is why a schema written around what people do missed them.

Step four: for each gap, decide add or cut. Cut is not available here: without step five the value does not land, and without step four the notebook comes back. So both get events.

Step five: write each new event in four parts and add it to the schema file in the same commit. `system_sends_confirmation`: fired by the system, properties `host_id`, `request_id`, `channel`, `recipient_role`, owner LK. `system_blocks_calendar`: fired by the system, properties `host_id`, `request_id`, `ms_since_confirm`, owner LK.

Step six: ask what each new event lets you read in Week 10. The confirmation event, split by `recipient_role` and `channel`, shows whether the guest's copy ever went out. The calendar event's `ms_since_confirm` shows how long the block took, which becomes the Week 11 SLO: ninety-nine percent of confirmations reflected within five seconds. An event that answers no question is decoration.

Step seven: check the other direction. The schema has `host_declines_request`, which is on no journey step. It is a failure path: it tells you why confirms are low when they are. It stays, with a one-line note saying so.

## Common mistakes and how to spot them

**Retyping the event name.** `host_confirm_booking` in the mapping, `host_confirms_first_direct_booking` in the schema. Spot it: select the name in the schema, copy, paste. Any name typed by hand is silent failure number two from Week 5, arriving a week early.

**Folding a system step into the person's event.** "The confirm event covers the calendar block too." Spot it: ask whether the two things can fail separately. If the confirm can succeed and the block can fail, they need two events, or the block's failure is invisible.

**Adding an event with no owner.** Spot it: four parts or nothing. The owner is the person who opens the live view in the Week 7 lab and confirms the event arrived.

**Cutting a step to close a gap.** The step was essential, the event was work, so the step goes. Spot it: run the smallest test from the boundary guide. If the value does not land without the step, add the event.

**Properties that identify a person.** A guest's name on `system_sends_confirmation` because it was convenient. Spot it: the Week 5 rule holds for system events too. `request_id` points at the database row; the name stays in the row.

## Check yourself

1. Which journey step had a gap, and what did you do about it: add, with four parts, or cut, with a reason?
2. For each event you added today, what question does it answer in Week 10 that no other event answers?
3. Is there an event in your schema that is on no journey step? Why does it stay?
