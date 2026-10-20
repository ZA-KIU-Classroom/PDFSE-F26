# Writing an Event Schema

## The concept

An event schema is the list of things your product will notice and record, written down before any code records them. Each event has four parts: a name in actor_verb_object form, who fires it, the properties attached to it, and one teammate who owns it. The events sit on the AARRR skeleton, Acquisition, Activation, Retention, Referral, Revenue, so that you can see which step of a user's journey each one belongs to.

The schema is the contract between the metric you chose and the code you will write. Your north star is a sentence; the schema turns it into arithmetic over named events. If the schema is wrong, the dashboard in Week 7 will be confidently wrong, and you will not know.

## Why it matters

Instrumentation added after the fact is almost always inconsistent. One teammate names an event `bookingConfirmed`, another `host_confirm`, a third fires it on page load. By the time anyone looks at the dashboard there are three events that mean roughly the same thing, with three partial counts, and a graph that looks healthy because the three overlap. Nobody can say what the real number is.

The failure story is the Spring team whose dashboard showed forty activations. One teammate, before the slide went up, reconciled it against the database and the message threads. Twelve were real. The event had been bound to the render of the confirmation screen rather than the tap of the confirm button, so every refresh, every back-and-forward, every curious teammate opening the page counted as a user getting value. The team had a schema; it just did not say which action fired the event. One missing column cost them a week of believing a number that was not true. "Your metric is only as good as your instrumentation" is the sentence they wrote at the top of the corrected file.

## Worked example, step by step

Sakhli's schema, built in Lab 5.

Step one: write the north star at the top, word for word from the worksheet, and name the event or events that count it. Confirmed direct bookings per active host per month. Events: `host_confirms_first_direct_booking`, `host_confirms_repeat_booking`. Then write the arithmetic: first confirms plus repeat confirms, per host with at least one confirm in the window, per month. If you cannot write that line, the north star is not countable yet.

Step two: decide which AARRR steps the product can actually fire before Week 7. Sakhli: acquisition, activation, retention. Referral and revenue stay empty, with a one-line note saying why. An empty step is honest. An invented event is something you will delete in Week 7, after it has confused you.

Step three: one row per event, four columns. `guest_opens_host_link`, fired by guest, properties host_id and source, owner GT. The source property is the one that matters here: card, instagram, whatsapp. It costs nothing to add now and in Week 10 it answers which channel brings guests. `guest_requests_dates`, fired by guest, marked as a precursor. `host_confirms_first_direct_booking`, fired by host, with is_first_for_host so activation can be counted separately from the running total. `host_confirms_repeat_booking`, fired by host, with days_since_last_confirm so the gaps between bookings are visible before the monthly count drops.

Step four: the failure path. `host_declines_request`, with a reason property. The team added this after the lab, because a decline is information: full, wrong dates, or something else. Without it, a declined request and an ignored request look identical in the data.

Step five: the reconcile plan at the bottom. Which event is most likely to fail silently, how, and the check that would catch it. Sakhli predicted a double fire on the confirm event, and the check is to count confirmed bookings in their own database for the same week and compare. That line is a promise to their Week 7 selves.

## Common mistakes and how to spot them

**Names in two shapes.** `BookingConfirmed` in one place, `host_confirms_booking` in another. Spot it: read every name aloud; each must start with an actor and contain a verb. If two names could describe the same moment, merge them now.

**No "fired by" column, or "the app" for everything.** Spot it: for the north star event, the firer must be the person who receives the value. If every row says "system", you have described what your database does, not what your users do.

**Personal data in properties.** A guest name, a phone number, message text. Spot it: for each property, ask whether you would be comfortable with it on a dashboard a stranger could see. If not, it is not a property; it stays in your database under the consent terms from Week 2.

**Events on steps you cannot fire yet.** A `host_refers_host` event for a product with three users. Spot it: if you cannot name the button or action in your prototype that fires the event, the row is a wish.

**Precursor as north star.** `guest_requests_dates` marked with the star. Spot it: the north star event must be the moment value lands. A request is interest.

**No owner, or "team".** Spot it: initials in every row, and the reconcile plan names one person. If nobody owns an event, nobody checks it fires.

## Check yourself

1. Can you write your north star as arithmetic over named events, in one line?
2. For each event, who fires it, and is the north star event fired by the person your problem statement is about?
3. Which event will you reconcile against ground truth in Week 7, how, and who runs the check?
