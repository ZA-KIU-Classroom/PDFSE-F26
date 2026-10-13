# Prototype Plan

**This is the Sakhli team's file.** Theirs lives at `02-design/prototype-plan.md`; yours goes to the same path. Copy the shape, not the content.

## 1. The riskiest assumption

> We assume that a host will confirm a direct booking request by tapping it on her phone, instead of answering on WhatsApp and writing it in the notebook the way she does now.

**Why this one is riskiest:** Every host we met trusts the notebook (03, 05). If a host will not move one confirmation from the notebook to a screen, a shared calendar is useless, however well it syncs. No log tests this yet, which is why the prototype must.

## 2. The one action

> A host can see a guest's date request and confirm it, and see those dates blocked.

## 3. Fidelity

| Choice | Why it is the cheapest thing that can kill the assumption | Tool | Time |
|---|---|---|---|
| Clickable, phone-sized | The assumption is about tapping on her own phone. Paper cannot test a tap or a notification; code adds nothing the test needs. | An AI prototyping tool, exported as a link that opens on a phone | One evening |

## 4. Screens, each traced to evidence

| Screen | What the tester does on it | What earns it |
|---|---|---|
| 1. Request card | Sees "A family asks for 14 to 16 August, 2 adults, 1 child" | Requests arrive on many channels in the same hour (01, 03) |
| 2. Calendar for that week | Sees which rooms are free | The notebook is checked before every answer (03) |
| 3. Confirm | Taps confirm | The one action, section 2 |
| 4. Blocked week | Sees the dates marked as taken | The fear is selling the same room twice (01, 03, 05, 07) |

**Will not appear, even if a tool generates it:** guest reviews, online payment or deposits, a guest choosing a specific room, an AI chat assistant, multi-property dashboards. No log asked for any of them.

## 5. The test that can fail

- **Task, read aloud:** "A family just asked for 14 to 16 August. Show me what you would do."
- **Success looks like:** she finds the request and taps confirm within 60 seconds, without asking us anything.
- **Failure looks like:** she opens WhatsApp to answer instead; she asks "what do I press?"; she taps a guest-side button; she reaches for the notebook to check first and says she would not trust the screen.
- **Decision rule:** if 3 or more of 5 hosts fail, the assumption is weakened and we test a version where the confirmation arrives inside WhatsApp before building anything else.
- **Our prediction of the first thing a tester gets wrong:** tapping the big "Request dates" button, which is the guest's button, not hers.

## 6. Five testers

| Code name | From log, or new | Books them |
|---|---|---|
| Oni-1 | log 01 | LB |
| Oni-3 | log 03 | KT |
| Ambrolauri-5 | log 05 | MG |
| Oni-9 | new, the neighbor Oni-1 introduced | LB |
| Shovi-1 | new, the cousin from log 05 | MG |

---

## What to notice

- **Section 1 is about her hand, not our code.** "Can we sync calendars" is an engineering question with a known answer. "Will she tap instead of write" is the one that can kill the company.
- **The failure list has four observable behaviors.** You could tick each one while watching, without asking her opinion.
- **The "will not appear" list is written before the tool runs.** Next week's lecture shows what happens when the tool invents screens anyway.
