# Identify, Properties, and Privacy

## The concept

Three decisions about every event, all of them about people.

Who did it. PostHog gives each browser a random id and treats it as an anonymous person. `identify` is you telling PostHog that this browser belongs to a known person, using an id your own app made up. On the server, the same decision is the `distinctId` you pass with each event.

What rides along. Properties are the details attached to an event. The rule: ids your app invented, counts, durations, and short fixed lists of values. Never a name, a phone number, an email, an address, or free text someone typed.

What you tell them. If real people use your product this week, the page says what you count, in sentences that are true.

## Why it matters

In 2018 Twitter asked all of its users, more than three hundred million accounts, to change their passwords. Passwords were stored safely in the database, hashed, as they should be. But a bug had also written them, unmasked, to an internal log before the hashing step. Nobody had decided to store passwords in plain text. Someone had logged a whole object because it was convenient, and the log became a second copy that the careful part of the system knew nothing about.

Analytics is exactly that kind of second copy. Your database holds a guest's phone number under the terms you told the guest. The moment that number rides on an event, it also lives in another company's system, in dashboards any teammate can open, and in exports. You cannot easily take it back. The request's id points at the same person without carrying them.

## Worked example, step by step

Sakhli, deciding all three for its seven events.

Step one: who needs to be one person over time? The north star is per host, so a host must be the same person on Monday and on Friday. Guests pass through once.

Step two: identify the host, once, with an internal id. The private host page calls `posthog.identify(hostId)` when it loads, where `hostId` is the database key, `h_7f3a`. Not her name. Not her phone. The route that confirms a booking on the server passes the same value as `distinctId`, so browser events and server events land on one person.

Step three: leave guests anonymous. Their two events carry `host_id` and `request_id`. That is enough to follow one request from open to confirm.

Step four: read every Properties cell in the schema and ask of each one, could this identify a human? `source` has four allowed values: fine. `nights`, `party_size`, `ms_since_confirm`: numbers. `reason` on a decline: three allowed values, not a text box. Nothing else.

Step five: catch the convenient mistake. LK's first version of the request route captured the event with `properties: body`, the whole submitted form. That form holds the guest's first name and contact. Caught by reading one expanded row in Activity during the walk; replaced with four named properties.

Step six: write the line on the page. At the bottom of the guest page, in Georgian and English: "Sakhli is a student project. We count visits and booking requests to see if it works. Your name and contact go only to the host you are writing to." Then the check: open the tables and read the column names. The requests table has `guest_first_name` and `guest_contact`. The line says they go to the host. The host page shows them to the host and nowhere else. The line is true.

Step seven: leave session replay off. It records what people see and type. Turning it on this week would make the line on the page false.

## Common mistakes and how to spot them

**Everyone is one person.** A hard-coded id left in from testing, so every host is `test`. Spot it: PostHog's Persons list shows one person with all the events; "per host" always equals the total.

**Nobody is anyone.** `identify` never called, so a returning host is a new anonymous person each visit and retention stays empty forever. Spot it: the Person column on a host's events shows a random string.

**Identifying with contact details.** An email or phone as the id. Spot it: read the Person column aloud. If you would not put it in an interview log, it does not go there.

**The whole object as properties.** Spot it: expand one row in Activity and read every property name. More properties than the schema row lists means something extra is riding along.

**Free text.** A notes field, a message body, a search query. People type names and numbers into all of them. Spot it: any property whose value a user typed.

**A privacy line that describes the product you meant to build.** Spot it: read your column names against the line, one by one.

## Check yourself

1. Which of your users need to be the same person across visits, and what id do you pass for them?
2. Expand your north star event in Activity. Does it carry exactly the properties in your schema row, and nothing else?
3. Write the two or three sentences your page will show. Which table and column would prove each sentence true?
