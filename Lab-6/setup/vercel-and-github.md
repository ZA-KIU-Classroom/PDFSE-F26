# Vercel and GitHub: the deploy loop and the board

*Setup guide. Companion to `SHIP-STACK-SETUP.md` step 4, plus the board from the Week 6 session.*

## The loop you are setting up

Push to `main` on GitHub. Vercel builds `app/` and deploys it to your production URL in two to three minutes. That is the whole continuous deployment story for Sprint 1. No GitHub Actions, no Docker, no CI config. Every merged story is live before the reviewer opens their phone.

## One-time setup

1. **Who deploys.** Vercel's free plan has no team seats, so one teammate's personal account owns the Vercel project. Pick the teammate who already has a Vercel account or the repo owner. Everyone else never touches Vercel; they push to GitHub.
2. **Import.** vercel.com, sign in with GitHub, **Add New, Project**, pick the team repo. If the repo is on another teammate's GitHub account, Vercel asks for access to that account's repos; the repo owner grants it once.
3. **Root Directory: `app`.** Click Edit beside Root Directory before the first deploy. Forgetting this is the single most common build failure.
4. **Environment variables.** Paste each one from `app/.env.local`, name and value, before the first deploy. `NEXT_PUBLIC_` ones reach the browser; the rest stay on the server. A variable added after a deploy does not exist until you redeploy (Deployments, three dots, Redeploy).
5. **Deploy.** Then open the URL on a phone.

## Production versus preview

- `main` is production. Its URL is the one in your README, the one testers use, the one PostHog counts.
- Any other branch, and any pull request, gets a preview deployment with its own URL. Previews sit behind Vercel Authentication by default, so a tester without a Vercel login sees a sign-in wall. Never send a tester a preview link.
- Runtime logs on the free plan are kept for one hour. If a route fails in production, reproduce it and read the log within the hour, or add a `console.error` that you can see in the Vercel Logs tab right after.

## The board

From the Week 6 session: one board, four columns, one card per story, owner on every card.

GitHub Projects, inside the team repo: **Projects** tab, **New project**, Board layout. Rename the columns to Next, Doing, Review, Done. Add one draft card per story from `03-build/sprints/sprint-1.md` with the owner's name in the title (`S3 Host confirms · NK`). Link the board from the team README.

Trello or a pinned Telegram message with four headings does the same job. What matters is that at 22:00 on a Wednesday every teammate can see who is on what without asking.

## Merging daily

- Work on `main` directly if you are two people and talk constantly. Work on short branches (`s3-host-confirm`) if you are three or four, and merge the same day.
- Before you start: `git pull`. Before you stop: commit, push. A branch older than one day is a message in the team chat.
- A merge conflict in a file an AI tool generated: do not guess. Open the file, read both sides, keep the one that matches the acceptance criteria, run `npm run build`, then commit.
- Commit messages a stranger understands: `Add confirm route with calendar block and events`, not `fix`.

## The reviewer's loop

Owner merges to `main`. Vercel deploys. Reviewer opens the production URL on their phone, runs the story's acceptance criteria top to bottom, opens PostHog Activity to see the event, and moves the card to Done or back to Doing with one line saying what they saw. The reviewer does not fix. That loop is the definition of done, executed.

## Hobby plan terms, in one paragraph

Free, personal, non-commercial. A class project qualifies. 100 GB of transfer and a million function invocations a month, which a pilot with fifty users does not approach. 100 deployments a day. If the product starts charging money, that is the Week 12 pricing conversation and a Pro plan at that point, not now.
