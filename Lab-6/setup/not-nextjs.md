# Not Using Next.js? The same five rules, your tools

*Setup guide. For teams whose architecture file names a different stack. The reference guides are written for Next.js because that is what the Sakhli example uses; nothing in the gate depends on the framework.*

The gate needs exactly five things, whatever you build with:

1. **A public HTTPS URL that a stranger's phone can open.** Not localhost, not a tunnel from your laptop, not a preview link behind a login.
2. **A hosted database that keeps running when your laptop is closed.**
3. **Every schema event fired under its exact copied name, with its properties, from the right side** (person's events from the browser after success; system events from the server after the write).
4. **The events visible in PostHog's Activity view, and a reconcile check against the database that matches once.**
5. **Secrets in environment variables on the host, never in the repo.**

## Hosting that fits a sprint

| Your app is | Host it on | Database | Notes |
|---|---|---|---|
| Static HTML, or a client-only React or Vue app | Vercel, Netlify, Cloudflare Pages, GitHub Pages | A hosted API you also deploy, or Supabase (Postgres plus an HTTP API, free tier) | Client-only means every event fires from the browser; a "confirm" that only changes browser state is not a confirm. You still need a server for the write. |
| Python (Flask, FastAPI, Django) | Render, Railway, Fly.io (all have free or trial tiers; check the current card requirement before you commit) | Neon Postgres, same as the reference stack | PostHog's `posthog-python` library; `posthog.capture(distinct_id, event, properties)`, and call `posthog.flush()` before the request returns on serverless hosts. |
| Node (Express, Hono) | Render, Railway, Fly.io, or Vercel as serverless functions | Neon | `posthog-node`, same code as `posthog-wiring.md`. |
| A mobile app (Expo or React Native, Flutter) | The app runs on the phone; the API still needs one of the hosts above | Neon or Supabase | `posthog-react-native` or `posthog-flutter`. A TestFlight or APK link counts as the public URL for the gate if a stranger can install it; coordinate with the instructor in the Week 7 lab. |
| A no-code or low-code tool | Its own hosting | Its own | Allowed only if you can fire custom events with properties to PostHog (most support a JavaScript snippet) and read your own data for the reconcile check. If it cannot do both, the journey is not measurable and the tool is not an option. |

## PostHog in any web page

The browser snippet from PostHog's **Settings, Project** page goes in your HTML `<head>`. It initializes `posthog` globally; then `posthog.capture("event_name", { ...properties })` from any script. The reverse proxy against ad blockers is harder without a framework; Cloudflare Pages and Netlify both have a documented rewrite recipe in PostHog's docs under Advanced, Proxy. If you skip the proxy, expect some tester events to vanish and say so in your reconcile plan.

## The one thing that does not change

The schema. Whatever fires the event, the string is copied from `03-build/analytics/event-schema.md`, the properties are the ones in the row, and the owner's initials are the person who opens Activity and sees it arrive. The Week 7 lab verifies that per team, on screen, in the same way for every stack.
