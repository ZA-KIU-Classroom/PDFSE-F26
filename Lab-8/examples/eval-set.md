# Eval set (starter)

**This is the Sakhli team's file as it stood before Lab 9.** Theirs lives at `03-build/evals/eval-set.md`; yours goes to the same path. Ten of their thirty cases are shown. Copy the shape, not the content.

## The feature, in four lines

- **Input:** a guest's inquiry, in any language, arriving through the host's Sakhli page
- **Grounded in:** availability for the dates asked (from `blocked_dates` and confirmed `requests`), price per night and listing text (from `hosts`)
- **Output:** a draft reply in the guest's language, with a Georgian copy for the host
- **Approved by:** the host, on her private page; nothing is sent until she taps Send

**The number from our readout that should move if it works:** hours from request to answer; today a 14 hour median on 6 answered requests.

**Version zero lives at:** `03-build/evals/prompt-v0.md`

## Cases

| # | Source | Input, exactly as it would arrive | Facts that were true at the time | A good output must |
|---|---|---|---|---|
| 03 | Field week | "Do you have a room 14 to 16 Aug for 2?" | Dates free; 80 GEL per night | Say yes, give the price, in English |
| 07 | Field week | (Georgian) "We want two nights from 20 August" | Dates free | Say yes, in Georgian |
| 11 | Field week | (Russian) "One night, tonight, is it possible?" | Tonight free | Say yes, in Russian, without asking for information already given |
| 14 | Log 05 | "Are you free next weekend?" | No dates given | Ask which dates; not guess |
| 17 | Edge | "22 to 24 Aug, two people" | 23 Aug blocked by the host, by hand | Say those dates are not all free; never say yes |
| 19 | Log 08 | (German) "Is breakfast included?" | Listing says nothing about breakfast | Say the host will check; not invent an answer |
| 21 | Edge | "Just the night of 23 Aug" | 23 Aug blocked | Say no; offer nothing the calendar does not show |
| 22 | Edge | "We are nine people, one night, 5 Sep" | Six rooms; dates free | Not promise space for nine; say the host will confirm |
| 24 | Log 02 | "Is there parking? We come by car" | Listing says nothing about parking | Say the host will check |
| 26 | Field week | (Georgian) "29 to 31 August" | 30 Aug blocked | Say those dates are not all free, in Georgian |

**The worst thing this feature could say confidently and wrongly, and the case number that tests it:** "Yes, those dates are free" when one of them is blocked. Cases 17, 21 and 26.

## Checks (drafted in the Week 9 session, finished in Lab 9)

| Check | Kind | Passes when |
|---|---|---|
| Availability | code | What the draft says about the dates matches the calendar |
| Language and tone | judge, spot-checked by NK | Same language as the guest; reads like a host, not a company |
| No invented facts | code where the listing has the field, human otherwise | Every claim in the draft is in the facts given |

## The DECISIONS.md line

`Wk8 · AI feature: draft the host's reply to a guest inquiry, from her calendar and listing, to move hours-to-answer; the host approves every message · evidence: 03-build/analytics/break-readout.md, logs 02, 05, 08, 11 · owner: LK`
