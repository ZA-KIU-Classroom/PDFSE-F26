# Choosing a Stack You Can Deploy

## The concept

The architecture decision in Lab 6 is not "what is the best technology for this product." It is "what can this team deploy at a public URL, with a database behind it, by the Week 7 lab." The best reason for any layer is that a teammate has deployed it before. The second best is a hosted free tier that removes something you would otherwise run yourself. Novelty is a cost Sprint 1 cannot afford.

The architecture file has one diagram and one line per layer. The line answers the deploy question, names the person or the free tier that makes it true, and nothing else.

## Why it matters

The Week 7 gate is a date, not a goal. Every hour spent learning a framework nobody on the team has used is an hour not spent on the journey. The teams that miss the gate rarely have the hardest product. They chose a stack for the portfolio and found on deploy day that the hosting needs a card, the database needs a server, or the deploy needs a config file nobody understood.

The failure story is from Spring. A team of three chose a backend framework one member had read about but none had deployed, because "it is what real companies use." The product ran on a laptop by Week 6. On the deploy day they learned the free hosting tier did not support it, the paid tier needed a card none of them had, and the alternative host needed a container file that took a full evening to get right. They deployed two days after the gate with no analytics, and the break collected nothing. On a framework any of them had used before, their three screens were a four-hour deploy.

## Worked example, step by step

Sakhli, Lab 6, checkpoint 2.

Step one: list the layers the journey needs by reading the boundary. A guest page, a request form, a host page, a place to store requests and blocked dates, a way to send the guest a confirmation, and events. That is hosting, app, database, messages out, analytics. Sign-in is a question, not a given.

Step two: ask who has deployed what. GT has put two class projects on Vercel. GT and LK know React. NK has used Postgres at work. Nobody has run a server or used the WhatsApp API.

Step three: choose from what the answers allow. Hosting: Vercel, because GT has done it and the free tier gives HTTPS and a URL in minutes. App: Next.js, because the team knows React and server routes mean no separate backend to host. Database: Postgres on Neon, because it is hosted and free and NK knows the query language; the whole data model is two tables and a date-range check. Messages out: Resend for the guest's email, because it is one API call on a free tier; the host's confirmation is a screen, not an email, because Nino does not use email. Analytics: PostHog, fixed by the course.

Step four: decide what not to have. No login: the host gets a private link with a long random token, printed on the card. No file storage: the one house photo is a static file in the repo. No background jobs. No WhatsApp API, because approval takes longer than the sprint.

Step five: trace the journey through the stack, with the event each step fires and where. The open event fires on the client with `source` from the query string. Everything from the request onward fires on the server after the write commits, so no event claims a row that was never inserted.

Step six: name where secrets live and the one thing most likely to break. `.env`, listed in `.gitignore`, checked before the first push. Most likely to break: the date-range overlap check, where an off-by-one on the end date lets a double-booking through. That becomes the first thing tested on the deployed URL in Week 7.

## Common mistakes and how to spot them

**Choosing for the portfolio.** A framework nobody has deployed, because it looks good on a CV. Spot it: for each layer, name the teammate who has deployed it. If no name, the line fails.

**A server you have to run.** A database that needs a machine, a queue, a container. Spot it: ask what happens when your laptop is closed. If the answer is "the product goes down," pick a hosted layer.

**Login first.** Accounts, passwords, password reset, before the first real action. Spot it: ask whether the journey's last step can be reached with a private link instead. Usually it can, and login goes on the cut list.

**Secrets in the repo.** An API key in a config file, committed. Spot it: `.gitignore` lists `.env` before the first commit of `app/`, and the first commit is checked by someone other than the person who made it. A key in the history stays in the history.

**Events on the client for server actions.** The confirm event fires when the button is tapped, before the database says yes. Spot it: for every event after a write, fire it on the server after the write commits.

## Check yourself

1. For each layer in your table, which teammate has deployed it before, or which free tier removes the need to run it?
2. What does your journey's last step need from the stack that the first step does not, and is that layer the one most likely to break?
3. Is `.env` in `.gitignore` right now? Who checked?
