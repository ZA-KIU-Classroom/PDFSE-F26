# PostHog Wiring: every schema row becomes one capture call

*Setup guide. Companion to `SHIP-STACK-SETUP.md` step 3. Code is for Next.js 16 App Router; the rules apply to any stack.*

## The three rules

1. **Names are copied, never typed.** Open `03-build/analytics/event-schema.md`, select the name, paste. A typo is a second event with half your count and no error.
2. **A person's event fires from the browser, after the server said yes. A system event fires from the server, after the write commits.** A guest's request is the guest's event: fire it in the click handler once the response is OK. The calendar block is the system's event: fire it in the route, after the insert, with `await posthog.flush()` before returning.
3. **The id is the only thing that leaves your database.** `host_id`, `request_id`, counts, durations, enums. Never a name, phone, email, or message text. Same rule as your interview logs, one layer down.

## Client side: a person's event

`app/app/h/[slug]/request-form.tsx` (a client component):

```tsx
"use client";
import posthog from "posthog-js";

export function RequestForm({ hostId }: { hostId: string }) {
  async function onSubmit(formData: FormData) {
    const res = await fetch("/api/requests", { method: "POST", body: formData });
    if (!res.ok) return; // show an error; do not fire the event
    const { request_id, nights, party_size } = await res.json();
    posthog.capture("guest_requests_dates", {
      host_id: hostId,
      request_id,
      nights,
      party_size,
    });
  }
  return <form action={onSubmit}>{/* date picker, party size, contact, Request button */}</form>;
}
```

The event fires once, in the handler, after success. Never inside the component body and never in a `useEffect` that runs on render: both double-fire on re-render (Week 5, silent failure three).

The page-open event is the one exception where firing on load is correct:

```tsx
"use client";
import { useEffect } from "react";
import posthog from "posthog-js";

export function OpenTracker({ hostId, source }: { hostId: string; source: string }) {
  useEffect(() => {
    posthog.capture("guest_opens_host_link", { host_id: hostId, source });
  }, [hostId, source]);
  return null;
}
```

`source` comes from the query string (`?src=card`); read it in the server page with `searchParams` and pass it down. Default it to `"other"` when absent.

## Server side: a system event

`app/app/api/requests/[id]/confirm/route.ts`:

```ts
import { NextResponse } from "next/server";
import { sql } from "@/lib/db";
import { posthog } from "@/lib/posthog";

export async function POST(_req: Request, { params }: { params: Promise<{ id: string }> }) {
  const { id } = await params;
  const t0 = Date.now();

  const [row] = await sql`
    update requests set status = 'confirmed', confirmed_at = now()
    where id = ${id} and status = 'pending'
    returning id, host_id, check_in, check_out, nights`;
  if (!row) return NextResponse.json({ error: "not pending" }, { status: 409 });

  const [{ count }] = await sql`
    select count(*)::int as count from requests
    where host_id = ${row.host_id} and status = 'confirmed'`;

  await sql`insert into blocked_dates (host_id, request_id, check_in, check_out)
            values (${row.host_id}, ${row.id}, ${row.check_in}, ${row.check_out})`;

  posthog.capture({
    distinctId: row.host_id,
    event: count === 1 ? "host_confirms_first_direct_booking" : "host_confirms_repeat_booking",
    properties: { host_id: row.host_id, request_id: row.id, nights: row.nights, is_first_for_host: count === 1 },
  });
  posthog.capture({
    distinctId: row.host_id,
    event: "system_blocks_calendar",
    properties: { host_id: row.host_id, request_id: row.id, ms_since_confirm: Date.now() - t0 },
  });

  await posthog.flush(); // without this, the function can end before the events leave
  return NextResponse.json({ ok: true });
}
```

Why the host's confirm fires here and not in the browser: the confirm is only real once the database row says `confirmed`, and the event must not claim a booking the update rejected. Firing on the server after `returning` gives you that for free. The `distinctId` is the host's internal id, so every host event stitches to one person in PostHog without the host ever logging in.

## Identify, and why you mostly do not need it

`posthog.identify(id)` on the client links the browser's anonymous id to a known person. Sakhli's hosts never log in; they open a tokenized link. So the host page calls, once, on load:

```ts
posthog.identify(hostId);
```

and nothing else. Guests stay anonymous: their events carry `request_id` and `host_id`, which is all the Week 10 funnel needs. Do not identify with an email or a phone; the id your app made up is the identity.

## Verify, in this order

1. **Localhost, Activity view.** Do the action; the event appears within seconds with every property you expected. Click it; check the property names match the schema exactly.
2. **Production, Activity view, on a phone.** Same action at the Vercel URL. If localhost works and production does not, it is an env var or the host region.
3. **Count it twice.** The reconcile step in `SHIP-STACK-SETUP.md` step 5. Only then build a dashboard tile.

## Diagnostics, in silent-failure order

| You see | It is | Check |
|---|---|---|
| Nothing arrives, no errors | Capture never initialized, or key missing in production | Browser console: `posthog.get_distinct_id()` returns a string if init ran. Vercel env vars for `NEXT_PUBLIC_POSTHOG_KEY`. |
| Nothing arrives, network tab shows requests to `/ingest` failing | Proxy rewrites wrong, or `skipTrailingSlashRedirect` missing | Compare `next.config.ts` to the block in the setup guide; region must match the project. |
| Two events with similar names | Typed, not copied | Fix the string in code; in PostHog, Data management, mark the stray event as hidden. |
| Count exactly double, or climbs on refresh | Capture on render, or `useEffect` without deps | Move into the handler or the route. |
| Server event missing, client events fine | No `flush()` before return, or `POSTHOG_KEY` (server var, no prefix) missing | Add the await; check the server var in Vercel. |
| A tester you watched confirm, nothing arrives | Ad blocker, and the proxy is not in place | Check `/ingest` is the api_host and the rewrites exist; the proxy is the fix. |
| Events arrive from your own testing and pollute counts | Your laptop and your teammates' phones | In PostHog, Settings, Project, add your own ids to internal users; filter them in every insight. Also exclude the five testers by `host_id` when you count real hosts in Week 10. |

## What Week 7 adds

The dashboard: an activation funnel (open, request, confirm), the north star trend by month with `host_id` breakdown, and one retention view. Everything on it filters on the names you copied this week. If the names are right now, Week 7 is forty minutes of clicking. If they are wrong, Week 7 is debugging.
