# Team Repo Setup

*Done in Lab 2, step C0. About 10 minutes. One person drives, the whole team watches. Come back to the structure and the map below all semester.*

Your team keeps one repository for the whole semester. Every interview, decision, design, line of code, and pitch slide lives in it. Milestones 1, 2, and 4 are submitted as a tag on this repo plus an LMS form, and at Week 15 the repo itself is graded (Milestone 4, 15 points). Set it up properly once, today.

## Already have a repo from Lab 1?

- **You accepted the GitHub Classroom link** (your repo lives under `ZA-KIU-Classroom`): keep it, and keep its name. The professor already has access, so skip steps 1 and 2. Teammates who have not joined yet accept the same Classroom link and choose your team. If the repo has no `.gitignore` file, add one: **Add file**, then **Create new file**, name it `.gitignore`, and pick the `Node` template. Then do steps 3 to 7. At Week 15 the professor makes Classroom repos public for you.
- **You made a repo on your own account:** keep it, rename it to the convention in step 1 (Settings, then Rename), and check it against steps 2 to 7.

## 1. Create the repo (one person, the "repo owner")

1. On github.com, click **+** (top right), then **New repository**.
2. **Owner:** your own account.
3. **Repository name:** `pdfse-f26-<team-name>`, lowercase, hyphens instead of spaces. Example: `pdfse-f26-bandersnatch`.
4. **Description:** your team name plus one line on the problem you are investigating.
5. **Visibility: your choice.** Public builds a portfolio employers can see from day one; Private keeps early work inside the team. Either way the repo must be **Public by Week 15** for the portfolio review (only the repo owner can switch it), so write everything from today as if a stranger will read it.
6. Tick **Add a README file**. Set **.gitignore** to `Node` (or `Python`, if that is your stack).
7. Click **Create repository**.

## 2. Invite your team and the professor

1. In the repo: **Settings**, then **Collaborators** (left menu), then **Add people**.
2. Add every teammate by their GitHub username.
3. Add the professor: **`ZA-KIU`**. This is required. A repo the professor cannot open counts as not submitted.
4. Everyone gets an invitation by email and in GitHub notifications. **Invitations expire after 7 days.** Teammates accept now, in the lab.

## 3. Create the folder structure

Git does not store empty folders, so each one gets an empty `.gitkeep` file.

**First time using git on this laptop?** Tell git who you are, with the email on your GitHub account, or your commits will not count as yours:

```bash
git config --global user.name "Your Name"
git config --global user.email "the-email-on-your-github-account"
```

Clone the repo, then run this from inside it (on Windows, use Git Bash):

```bash
mkdir -p 00-foundation \
  01-discovery/interview-logs/practice 01-discovery/synthesis \
  02-design/user-testing \
  03-build/architecture 03-build/sprints 03-build/analytics \
  03-build/experiments 03-build/evals/results 03-build/reliability \
  04-gtm/financials 05-fundraising 06-strategy 07-legal 08-final \
  members app docs
touch DECISIONS.md
printf '# AI usage log\n\nOne line per AI-assisted piece of work.\nFormat: Wk<N> · who · tool · what it produced · what you checked or changed\n\n' > docs/ai-usage-log.md
find . -type d -empty -not -path "./.git/*" -exec touch {}/.gitkeep \;
git add . && git commit -m "Set up semester folder structure" && git push
```

No terminal? On github.com use **Add file**, then **Create new file**, type `00-foundation/.gitkeep` as the name, and commit. Repeat for each folder in the command above, then create `DECISIONS.md` (empty) and `docs/ai-usage-log.md` (copy the text from the `printf` line). Slower, same result.

`DECISIONS.md` stays empty on purpose: its first line is your problem pick, written in C1.

## 4. Move your Lab 1 work in

- Signed team contract to `00-foundation/team-contract.md`.
- Problem pool to `00-foundation/problem-pool.md`.
- Outreach tracker to `01-discovery/outreach-tracker.md`. **Before you commit it, replace every full name with a first name or code name plus a role** ("Tamar, host in Mestia"). Phone numbers, emails, and surnames never go in the repo; keep them in your team chat.

If any of this lives in a Google Doc or a chat, copy the text in now. From today, the repo is the only place work counts.

## 5. Every member: your own folder, your own first commit

Each teammate, **from their own account**, creates one file on github.com: **Add file**, then **Create new file**, named `members/<your-github-username>/pattern-journal.md`, with this inside:

```markdown
# Pattern journal · <your name> (@<github-username>)

Same prompt every week: Where did you apply this pattern this week, where did you exercise agency beyond your assigned lane, and what did you hack together to test something faster than the plan allowed? Link the DECISIONS.md lines you drove.

## Week 1 · Act like an owner, not a role

## Week 2 · Evidence over opinion
```

This does two jobs. It proves everyone can push, today, not the night before Milestone 1. And it is where your individual work lives:

- **Pattern journal:** one entry per week, written the week it happens; a journal written in one night reads like one. Weeks 1 to 4 are graded inside Homework 1, Weeks 5 to 7 inside Homework 2.
- **`hw1.md`** (Week 4): your personal interview log (every interview you asked or logged, with links to the log files; at least 2 you conducted), your journal for Weeks 1 to 4, and the DECISIONS.md lines you drove.
- **`hw2.md`** (Week 7): your ship report (what you personally built and deployed, with commit links), your journal for Weeks 5 to 7, and your DECISIONS.md lines.

Both homeworks are then uploaded to the LMS, as each HOMEWORK.md says.

## 6. Write the README

Replace the default README with this. Fill in what you have; the rest stays "coming" until its week.

```markdown
# <Team name>

**Investigating:** <one line, from the first line of DECISIONS.md>
**Team:** <name> (@github) · <name> (@github) · <name> (@github)

| Link | Status |
|---|---|
| Prototype | coming Week 5 |
| Live product | coming Week 7 |
| Analytics dashboard (PostHog) | coming Week 7 |
| 12-month model | coming Week 12 |
| Pitch deck | coming Week 13 |
| One-pager | coming Week 15 |

See DECISIONS.md for every product decision and the evidence behind it.
```

## 7. Post the link

Post your repo URL in your lab group's Teams channel, with your team name. The professor checks access from that list.

---

## The structure for the whole semester

```
pdfse-f26-<team-name>/
├── README.md                   Team, problem, and the five live links
├── DECISIONS.md                Every decision + its evidence (from Lab 2)
├── 00-foundation/
│   ├── team-contract.md        Lab 1
│   ├── problem-pool.md         Lab 1
│   ├── four-filters-scorecard.md   Lab 2
│   └── icp.md                  Lab 2
├── 01-discovery/
│   ├── outreach-tracker.md     Lab 1, kept current
│   ├── problem-hypothesis.md   Lab 2, before your first real interview
│   ├── interview-script-v1.md  Lab 2
│   ├── interview-script-v2.md  Lab 3
│   ├── interview-logs/         01-host-oni.md, 02-...  (real interviews only)
│   │   └── practice/           practice interviews, never counted
│   ├── synthesis/              affinity-map.md (or a board export), patterns-analysis.md  (Labs 3 to 4)
│   ├── problem-statement.md    Lab 4
│   └── competitive-landscape-seed.md   Lab 4
├── 02-design/
│   ├── prototype-plan.md       Lab 4
│   └── user-testing/           test-plan.md, usability-findings.md  (Week 5)
├── 03-build/
│   ├── mvp-boundary.md         Lab 6
│   ├── architecture/           architecture.md + one diagram  (Lab 6)
│   ├── sprints/                sprint-1.md, then one per sprint  (from Lab 6)
│   ├── analytics/              event-schema.md (Lab 5), break-readout.md (Lab 8)
│   ├── experiments/            experiment-1.md: design, then results  (Lab 8)
│   ├── evals/                  eval-set.md + results/  (Lab 9)
│   └── reliability/            slo-sheet.md  (Lab 9)
├── 04-gtm/
│   ├── financials/             unit-economics.md + model export  (Lab 10)
│   └── pricing-test.md         Lab 10
├── 05-fundraising/             pitch-deck-v1.pdf (Lab 11), pitch-deck-final.pdf,
│                               one-pager.pdf (Week 15)
├── 06-strategy/                competitive-analysis.md, moat-statement.md,
│                               positioning.md  (Lab 11)
├── 07-legal/                   privacy-notice.md, consent flow described  (Lab 9)
├── 08-final/                   integration-checklist.md (your team's run of it), case-study.md  (Lab 12)
├── members/<github-username>/  pattern-journal.md, hw1.md, hw2.md  (each of you)
├── app/                        Your product's code (from Week 6)
└── docs/ai-usage-log.md        Every AI-assisted piece of work, all semester
```

Every lab names the exact file it produces, and it will always be one of these. If a lab and this page ever disagree, ask in Teams.

## What gets graded from this repo

| Week | Lab | What you commit | Feeds |
|---|---|---|---|
| 1 | 1 | Contract, problem pool, outreach tracker | Milestone 1 |
| 2 | 2 | This setup, first DECISIONS.md line, scorecard, ICP, hypothesis, script v1, 3+ real logs | Milestone 1, Homework 1 |
| 3 | 3 | 6+ real logs, affinity map draft, script v2, prediction verdict in DECISIONS.md | Milestone 1, Homework 1 |
| 4 | 4 | Synthesis, problem statement, landscape seed, tag `m1-discovery` + LMS form; prototype plan for Lab 5 | **Milestone 1 (10)**; **Homework 1 (5)** by LMS |
| 5 | 5 | Prototype link, event schema with north star, test plan, 10 logs total | Milestone 2 |
| 6 | 6 | MVP boundary, architecture, Sprint 1 plan, code in `app/` | Milestone 2, Homework 2 |
| 7 | 7 | Live URL and dashboard in README, north star event firing | **Gate** for Milestone 2; **Homework 2 (5)** by LMS |
| 10 | 8 | Break readout, experiment 1 | Milestone 2 |
| 11 | 9 | Eval set and results, SLO sheet, privacy notice, pivot-or-persevere line, tag `m2-quality` + LMS form | **Milestone 2 (10)** |
| 12 | 10 | Unit economics, 12-month model, pricing test | Milestones 3 and 4 |
| 13 | 11 | Competitive analysis, moat statement, positioning, pitch deck v1 | Milestones 3 and 4 |
| 14 | 12 | Integration checklist run, case study | Milestone 4 |
| 15 | 13 | Final deck, one-pager, tag `m4-final`, repo Public, final submission form | **Milestones 3 and 4 (30)** |

Bold means graded that week; everything else feeds a later milestone. Every week: `DECISIONS.md`, `docs/ai-usage-log.md`, and your own `members/` folder.

## Naming and format rules

- **Interview logs:** `NN-role-place.md`, numbered in the order you ran them: `01-host-oni.md`, `02-student-kutaisi.md`. Practice interviews go in `interview-logs/practice/` and never count toward any number.
- **DECISIONS.md:** one line per decision, newest at the bottom, in this shape: `Wk<N> · <decision> · evidence: <links> · owner: <initials>`, plus any field a lab asks for (Lab 2 adds `runner-up:`). The commit records the date. Never delete a line. A reversed decision gets a new line that links the old one.
- **Decks and sheets:** commit a PDF (or CSV) export to the folder, and put the editable link in the README table.
- **Screenshots and images:** in the same folder as the file that shows them.

## House rules

- **If it is not committed, it did not happen.** Work in a Google Doc counts only once it is in the repo.
- **Commit as yourself.** Everyone commits their own work from their own account. The commit history is read at every milestone and is 2 points of Milestone 4.
- **Write commit messages a stranger understands.** "Add interview log 04: host in Mestia", not "update".
- **Code lives in `app/`, in this repo.** Do not split it into a second repo; the history here is what gets graded.
- **No personal data, ever.** Code names in logs and trackers. No surnames, phone numbers, emails, or addresses.
- **No secrets.** API keys go in a `.env` file. Check that `.gitignore` lists `.env` before your first commit of code.
- **Milestones are a git tag plus a form.** When a milestone is ready, tag the commit you are submitting, push the tag, then submit the LMS form (the final one in Week 15 is a Google Form):

```bash
git tag m1-discovery          # Week 4. Later: m2-quality (Week 11), m4-final (Week 15)
git push origin m1-discovery
```

## Troubleshooting

| Problem | Fix |
|---|---|
| Teammate cannot push | They have not accepted the invite. Check Settings, then Collaborators, for "Pending". |
| Invite expired | Remove them and invite again. |
| Folders missing after push | Empty folders are not stored. Check each has a `.gitkeep`. |
| Two people edited the same file | Pull before you start; commit small and often. If a merge conflict appears, ask in the lab. |
| Pushed something personal or a secret by mistake | Tell the professor the same day, and rotate any key. Deleting the file is not enough: it stays in the history. |
| Tagged the wrong commit | `git tag -d m1-discovery`, `git push origin :refs/tags/m1-discovery`, then tag again. |
