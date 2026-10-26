# Messages Out: email, and why it is probably on your cut list

*Setup guide. Read before you write a story that sends anyone anything.*

## The fact that changes your sprint plan

Transactional email services let you send to real people only from a domain you own and have verified. On Resend's free plan you can send from `onboarding@resend.dev` without a domain, but only to the email address on your own Resend account; any other recipient gets a 403. Verifying a domain means owning one (about 10 to 15 USD a year) and adding DNS records, which takes an evening the first time.

So before you write "the guest receives an email" into a story, answer one question: **does a teammate own a domain, right now?**

- **Yes:** verify it in Resend (Domains, Add Domain, paste the DNS records at your registrar, wait for the green check). Free plan: 3,000 emails a month, 100 a day, one domain. Then the code below.
- **No:** the email is on the cut list for Sprint 1, with the reason "no verified domain; confirmation is on screen and the guest has the host's phone number." The value still lands: the booking is in one calendar. Sakhli's slip rule already moves the email to Sprint 2 under pressure; a team with no domain moves it there on day one and says so in DECISIONS.md.

WhatsApp Business API, SMS gateways, and Telegram bots all need either business verification, a paid number, or an approval queue longer than the sprint. None of them belong in Sprint 1. A `tel:` link and a `https://wa.me/<number>` link on the confirmation screen cost nothing and work on every phone.

## If you have a domain: Resend in one route

1. Resend dashboard, **API Keys, Create API Key**, permission Sending access, restricted to your domain. Copy it once; it starts with `re_`.
2. `app/.env.local`: `RESEND_API_KEY="re_..."`. Add it to Vercel too.
3. `npm install resend`.
4. In the confirm route, after the database write and before `flush()`:

```ts
import { Resend } from "resend";
const resend = new Resend(process.env.RESEND_API_KEY);

const { error } = await resend.emails.send({
  from: "Sakhli <bookings@yourdomain.ge>",
  to: [row.guest_contact],
  subject: `Confirmed: ${row.check_in} to ${row.check_out}`,
  html: `<p>${hostName} confirmed your stay from ${row.check_in} to ${row.check_out}.</p>`,
});

posthog.capture({
  distinctId: row.host_id,
  event: "system_sends_confirmation",
  properties: { host_id: row.host_id, request_id: row.id, channel: "email", recipient_role: "guest", delivered: !error },
});
```

The event fires whether or not the send succeeded, with `delivered` saying which. In Week 10 that property is how you find out the email never arrived, rather than assuming it did.

## Either way: the host's confirmation is a screen

Nino does not use email (log 01). Her confirmation is the host page re-rendering with the request marked Confirmed, and `system_sends_confirmation` fires with `channel: "screen"` and `recipient_role: "host"`. One event name, two channels, told apart by a property. That is why `channel` is on the event.
