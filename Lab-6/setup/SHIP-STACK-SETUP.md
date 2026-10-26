# Ship Stack Setup: from empty `app/` to a measurable product at a public URL

*Setup guide, not a concept guide. Verified against the vendors' docs as of the Week 6 build. One person drives, the whole team watches, about 90 minutes. The Week 7 lab assumes this is done or mostly done.*

This is the reference stack from `Lab-6/examples/architecture.md`: Next.js on Vercel, Postgres on Neon, PostHog for events. If your team chose something else, read `setup/not-nextjs.md`; the rules are the same, the commands differ. Google Analytics is not used in this course: PostHog is the analytics tool, because it does custom events, funnels, and the live view you need for the Week 7 gate and Milestone 2.

**What you have at the end:** a public HTTPS URL, a database behind it, every event in your schema firing under its exact name and visible in PostHog, and a reconcile check that proves the count is real. That is the Week 7 gate.

## Before you start

- Node.js 20.9 or newer on the driver's laptop (`node -v`). Next.js 16 does not run on Node 18.
- The team repo cloned, on `main`, clean.
- Three accounts, each created by the teammate who will own that layer: GitHub (everyone has one), Vercel (sign in with GitHub; one teammate's personal Hobby account deploys the whole team's repo), Neon and PostHog (free, no card). Use the same login email across them so the Week 7 tracker can find you.
- `03-build/analytics/event-schema.md` open. Every event name below is copied from it, never typed.

## Step 1: the app lives in `app/` (10 min)

From the repo root:

```bash
npx create-next-app@latest app --typescript --app --eslint --src-dir=false --import-alias "@/*"
cd app
```

Accept the defaults for anything it asks. Then confirm the repo's `.gitignore` (at the repo root) lists `.env*` and `node_modules`; `create-next-app` adds its own `.gitignore` inside `app/`, which is fine, but the root one is the one that protects you if you ever put a key in the wrong folder.

Run it once: `npm run dev`, open `http://localhost:3000`, see the default page. Commit: `git add app && git commit -m "Create Next.js app in app/" && git push`.

Vercel needs to know the app is in a subfolder. That is one setting in Step 4.

## Step 2: the database on Neon (15 min)

1. In the Neon console, **New Project**. Name it after your team. Region: pick the closest to your users (Frankfurt for Georgia). Save the password it shows; it is shown once.
2. Click **Connect**, copy the connection string. It looks like `postgresql://user:password@host/dbname?sslmode=require&channel_binding=require`.
3. In `app/`, create `.env.local` (never committed) with:

```
DATABASE_URL="postgresql://...the string you copied..."
```

4. Install the serverless driver, which works over HTTP and needs no SSL setup:

```bash
npm install @neondatabase/serverless
```

5. Create `app/lib/db.ts`:

```ts
import { neon } from "@neondatabase/serverless";
export const sql = neon(process.env.DATABASE_URL!);
```

6. Create your tables. The Neon console has a **SQL Editor**; paste your schema there. Sakhli's two tables and the overlap rule are in `setup/neon-and-data.md`. Yours come from your journey: one table per thing a step creates or changes.

7. Prove the connection from a page. Replace the body of `app/app/page.tsx` with a server component that runs `const rows = await sql\`select now()\`` and renders it. Add `export const dynamic = "force-dynamic";` at the top so it runs on every request. Reload localhost; a timestamp means the database is reachable.

Free plan facts that matter: the database suspends after five minutes idle and wakes on the next query, so the first request after a quiet hour takes a second or two. That is normal, not a bug; mention it in your SLO reasoning in Week 11. 100 compute-hours per project per month is far more than a pilot uses.

## Step 3: PostHog, client and server (25 min)

Full detail, diagnostics, and the PII rule are in `setup/posthog-wiring.md`. The short version:

1. In PostHog, create one project (free plan: one project, unlimited teammates; invite every teammate from **Settings** so any of you can open the live view in the lab). Copy the **Project API key** from **Settings, Project**. Note whether your project is on the US or EU cloud; the host below must match.

2. Add to `app/.env.local`:

```
NEXT_PUBLIC_POSTHOG_KEY="phc_..."
NEXT_PUBLIC_POSTHOG_HOST="/ingest"
POSTHOG_KEY="phc_..."
POSTHOG_HOST="https://eu.i.posthog.com"
```

(`us.i.posthog.com` if your project is on US cloud. The first two reach the browser; the second two stay on the server.)

3. Install: `npm install posthog-js posthog-node`.

4. Client init, one file, `app/instrumentation-client.ts` (Next.js 15.3 and newer):

```ts
import posthog from "posthog-js";

posthog.init(process.env.NEXT_PUBLIC_POSTHOG_KEY!, {
  api_host: process.env.NEXT_PUBLIC_POSTHOG_HOST,
  ui_host: "https://eu.posthog.com",
  defaults: "2026-08-30",
  capture_pageview: true,
});
```

5. The reverse proxy, so ad blockers do not eat your events (silent failure number four from Week 5). In `app/next.config.ts`:

```ts
import type { NextConfig } from "next";

const nextConfig: NextConfig = {
  skipTrailingSlashRedirect: true,
  async rewrites() {
    return [
      { source: "/ingest/static/:path*", destination: "https://eu-assets.i.posthog.com/static/:path*" },
      { source: "/ingest/array/:path*", destination: "https://eu-assets.i.posthog.com/array/:path*" },
      { source: "/ingest/:path*", destination: "https://eu.i.posthog.com/:path*" },
    ];
  },
};
export default nextConfig;
```

(`us-assets` and `us.i` for US cloud. The static and array rules must stay above the catch-all.)

6. Server client, `app/lib/posthog.ts`, for events that fire after a database write:

```ts
import { PostHog } from "posthog-node";

export const posthog = new PostHog(process.env.POSTHOG_KEY!, {
  host: process.env.POSTHOG_HOST,
  flushAt: 1,
  flushInterval: 0,
});
```

7. The rule for which side fires an event: **a person's event fires from the browser, after the server has said yes; a system event fires from the server, after the write commits.** Both use the names from your schema, copied. Code for both shapes is in `setup/posthog-wiring.md`, including the `await posthog.flush()` that every server route must call before it returns, or the event is lost when the function ends.

8. Verify on localhost before you deploy: run `npm run dev`, do the one action, open PostHog's **Activity** view, and watch the event arrive with its properties. If it does not, the diagnostics table in `setup/posthog-wiring.md` is in silent-failure order.

## Step 4: deploy on Vercel (15 min)

1. On vercel.com, signed in with GitHub: **Add New, Project**, import your team repo. If the repo is on a teammate's account, that teammate does this step; Vercel's free plan has no team seats, so one personal account deploys, and everyone else pushes to GitHub.
2. **Root Directory:** click Edit and set it to `app`. Framework preset: Next.js is detected. Build settings: leave them.
3. **Environment Variables:** add the five from `.env.local`, one at a time, exactly as named. Leave them scoped to all environments. A variable you add later needs a redeploy before it exists.
4. **Deploy.** Two to three minutes. The URL is `https://<project>.vercel.app`.
5. Open it on a phone. Do the one action. Open PostHog Activity. Your first production event is there, or it is not, and the diagnostics table says why.
6. Put the URL in the **Live product** row of your team README and commit.

From now on every push to `main` redeploys production. Pushes to other branches get preview URLs; previews are protected behind a Vercel login by default, so **user tests run on the production URL**, never a preview link.

Terms you are agreeing to: the Hobby plan is for personal, non-commercial use. A class project is fine. If your product starts taking money, that is the Week 12 conversation and a Pro plan.

## Step 5: the reconcile check (10 min)

The Week 5 habit, made real before you believe your first number.

1. In PostHog, **Product analytics, New insight**: count of your north star event, last 7 days.
2. In the Neon SQL Editor: `select count(*) from <your table> where status = 'confirmed' and created_at > now() - interval '7 days';` (adjust names).
3. Equal: write both numbers and the date under **Reconcile plan** in your event schema. Different: the diagnostics table, then fix, then count again. Do not deploy a dashboard tile until they match once.

## Step 6: what goes in the repo (5 min)

- `app/` with the code. No `.env.local` anywhere in the history (check: `git log --all -- 'app/.env.local'` prints nothing).
- `app/.env.example` listing the five variable names with empty values, so a teammate can set up in two minutes.
- README: Live product row filled; Analytics dashboard row filled in Week 7 once the dashboard exists.
- `docs/ai-usage-log.md`: one line per AI-assisted piece of this setup, same format as always.
- One DECISIONS.md line if the stack you deployed differs from `03-build/architecture/architecture.md`, with the reason.

## If it breaks

| Symptom | Likely cause | Fix |
|---|---|---|
| Vercel build fails, local build passes | Root Directory not set to `app`, or a dependency missing from `package.json` | Project Settings, General, Root Directory. Then `npm run build` locally and fix whatever it prints. |
| Page loads on Vercel, database query fails | `DATABASE_URL` not in Vercel env vars, or added after the last deploy | Add it, then Deployments, Redeploy. |
| Events on localhost, none in production | `NEXT_PUBLIC_POSTHOG_KEY` missing in Vercel, or the host region does not match the project | Check both, redeploy. |
| Events arrive with the wrong name | Typed, not copied | Copy from the schema; delete the stray event name in PostHog's Data management so it stops confusing the funnel. |
| Count is exactly double | Capture call inside a component render or a `useEffect` without a guard | Move it into the click handler, or the server route. |
| Server event never arrives | Route returned before `flush()` finished | `await posthog.flush()` before the `return`. |
| First request after a quiet hour is slow | Neon cold start, free plan | Normal. Note it; do not fix it this sprint. |
| Teammate cannot see the Vercel project | Hobby plan has no team seats | They do not need to. They push to GitHub; the owner's Vercel deploys. The owner shares the URL and the Deployments page screenshots if needed. |
