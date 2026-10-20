# North Star Worksheet

**This is the Sakhli team's worksheet.** They did not commit it; they copied the last line to `DECISIONS.md` and the north star sentence to the top of `03-build/analytics/event-schema.md`. Do the same.

## 1. Three candidates

| # | Candidate |
|---|---|
| A | App downloads per month |
| B | Hosts signed up, total |
| C | Confirmed direct bookings per active host per month |

## 2. Three tests on each

| Test | A | B | C |
|---|---|---|---|
| 1. Counts value delivered, not presence | Fails. A download is a guest who found a link. Nino's double-booking problem is the same size after it. | Fails. Signing up costs Nino nothing and changes nothing. She has three apps her nephew installed. | Passes. A real guest in a real room through Sakhli instead of the notebook; one fewer booking that can be sold twice. |
| 2. Countable from one named event | Passes, trivially. | Passes. | Passes: `host_confirms_first_direct_booking` plus `host_confirms_repeat_booking`. |
| 3. Can go down, and that would mean something | Fails. Cumulative. | Fails. Cumulative. | Passes. Falls to zero in winter; that is the kill assumption, visible in the number. |

## 3. The survivor

**North star:** Confirmed direct bookings per active host per month.

**North star event:** `host_confirms_first_direct_booking` (first time), `host_confirms_repeat_booking` (after that).

**Who fires it, and why that person:** The host. The booking becomes real when she says yes; the guest's request is interest. The host is who the problem statement is about and who pays.

**The log numbers that show value lands at this moment:** 01 (sold the same room twice), 03 (checks the phone at 3am), 07 (gave the money back). The fear is about confirming a room she does not have. Confirming through one calendar is the moment that fear gets smaller.

## 4. The two decoys, with the test each failed

- Rejected **app downloads** because it fails test 1: presence, not value; also cumulative.
- Rejected **hosts signed up** because it fails test 1: presence; a sign-up changes nothing in Nino's August.

## 5. The line we committed

```
Wk5 · North star: confirmed direct bookings per active host per month; rejected app downloads (presence, cumulative) and hosts signed up (presence) · evidence: 03-build/analytics/event-schema.md, 01-discovery/interview-logs/01-host-oni.md, 03-host-oni.md, 07-host-oni.md · owner: NK
```
