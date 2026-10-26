# Neon and Your Data: two tables and one rule

*Setup guide. Companion to `SHIP-STACK-SETUP.md` step 2. Sakhli's schema is the worked example; yours comes from your journey.*

## Which tables

Read your journey in `03-build/mvp-boundary.md`. Each step either creates something, changes something, or reads something. Everything created or changed needs a row somewhere. Sakhli: step 2 creates a request, step 3 changes its status, step 5 creates a blocked date range. Two tables. Hosts are a third, tiny table because the link page needs a name and a photo.

Anything your journey does not touch is not a table this sprint. No users table if nobody logs in. No reviews table because reviews are on the cut list.

## Sakhli's schema, paste into the Neon SQL Editor

```sql
create table hosts (
  id          text primary key,            -- slug used in the URL: 'nino-oni'
  name        text not null,
  admin_token text not null unique,        -- long random string, printed on Nino's card
  created_at  timestamptz not null default now()
);

create table requests (
  id           text primary key default gen_random_uuid()::text,
  host_id      text not null references hosts(id),
  check_in     date not null,
  check_out    date not null,
  nights       int  generated always as (check_out - check_in) stored,
  party_size   int  not null,
  guest_name   text not null,              -- first name only; stays in this table, never on an event
  guest_contact text not null,             -- email or phone; same rule
  status       text not null default 'pending',  -- pending | confirmed | declined
  created_at   timestamptz not null default now(),
  confirmed_at timestamptz
);

create table blocked_dates (
  id         bigserial primary key,
  host_id    text not null references hosts(id),
  request_id text not null references requests(id),
  check_in   date not null,
  check_out  date not null,
  created_at timestamptz not null default now()
);

insert into hosts (id, name, admin_token)
values ('nino-oni', 'Nino''s Guesthouse, Oni', encode(gen_random_bytes(24), 'hex'));
```

## The one rule: no overlapping confirmed bookings

This is the value hypothesis in SQL. Two date ranges overlap when one starts before the other ends and vice versa. Check-out day is free for a new check-in, so the comparison is strict on both ends:

```sql
-- true if the requested range collides with an existing block for this host
select exists (
  select 1 from blocked_dates
  where host_id = 'nino-oni'
    and check_in  < date '2026-08-16'   -- requested check_out
    and check_out > date '2026-08-14'   -- requested check_in
) as blocked;
```

Run it in the request route before inserting, and again in the confirm route before blocking. Both, because two guests can request the same dates while they are still pending; the second confirm must fail.

Test it on the deployed URL in the Week 7 lab with two overlapping requests: confirm the first, confirm the second, the second must be refused. This was named in the architecture example as the thing most likely to break on deploy day. It is the off-by-one on `check_out` that lets a double-booking through.

## Querying from Next.js

`app/lib/db.ts` exports `sql`. Tagged templates are parameterized; never build SQL with string concatenation.

```ts
import { sql } from "@/lib/db";

const pending = await sql`
  select id, check_in, check_out, nights, party_size, guest_name
  from requests where host_id = ${hostId} and status = 'pending'
  order by created_at`;
```

Server components that read the database need `export const dynamic = "force-dynamic";` at the top of the page file, or Next.js may build the page once and never query again.

## Free plan facts

One gigabyte of storage per project, one hundred compute-hours per project per month, ten branches. Computes suspend after five minutes idle and wake on the next query; the wake costs a second or two and shows up as a slow first request after a quiet period. For the Week 11 SLO, measure from the confirm tap, not from the page open, so the cold start does not land in your number.

## What never goes in

Card numbers. Passwords (there are none; the host link is the credential). Message text from WhatsApp. Anything from your interview logs. A guest's contact lives in one column of one table and is deleted when the stay is over; write that sentence into `07-legal/privacy-notice.md` in Week 11 because it will be true.
