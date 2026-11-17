# Running a Field Week

## The concept

A field week is seven days in which a small number of real people use your live product in their own lives, and you watch what they do without standing beside them. Three to five people from your ICP. Not classmates. Each gets the production link through a channel that fits their week. Before it starts you write one prediction with a "we are wrong if" line. At the end, Lab 8 reads the events against the prediction.

It is the Week 2 interview turned inside out. In an interview you ask about past behavior because people cannot report their future behavior honestly. In a field week you stop asking. The behavior happens, and the events record it.

## Why it matters

In 2009 Airbnb was earning about two hundred dollars a week and going nowhere. The founders were in California. Their few hosts were in New York. On the advice of their accelerator they flew to New York, went to hosts' homes, and sat with them. They saw things no dashboard had told them: listings with poor photos, hosts unsure what to charge, people confused by steps the founders thought were obvious. They fixed what they saw, host by host, and revenue doubled within weeks. The lesson their investor later wrote up under the title "Do Things That Don't Scale" was not about photos. It was that with a handful of users, you go and get each one by hand.

Your product has zero real users today. Posting the link in a group chat will get you opens from people who are curious about you, not people who have the problem. Three hosts, each handed the link by a teammate who then stays to see the first open, is a field week.

## Worked example, step by step

Sakhli, Lab 7, checkpoint 4.

Step one: pick from the logs, not from the contact list. Four hosts the team has already interviewed or tested with: Oni-1, Oni-2, Ambrolauri-1, Oni-3. Each one is a log number, so the team knows her week before the week starts.

Step two: one teammate per person, with a day. NK takes the two in Oni, in person. GT takes Ambrolauri-1 by message and a call. LK takes Oni-3, whose nephew handles her phone.

Step three: the channel fits the person. Oni-1 gets a printed card for her counter, because log 01 says guests ask for her number at the door. Ambrolauri-1 lives on WhatsApp. Every guest link ends in `?src=card` or `?src=whatsapp`, so the first event says which door worked.

Step four: the words. No pitch, no feature list. "This is the booking page we showed you, now working. Give this link to a guest instead of taking the dates by message. You will see the request here and confirm with one tap. It is a student project; we count visits and bookings, never names."

Step five: stay for the first open. NK does not leave the card and go. She watches Oni-1 open the private link once, and says nothing while she does.

Step six: the prediction, before any real data. "By Lab 8: 3 confirmed direct bookings from real hosts. Also 4 hosts open their private link, 6 guest requests. We are wrong if fewer than 2 hosts confirm anything." Committed in the lab.

Step seven: one mid-week look, by one named person. GT opens the dashboard on Wednesday and writes one line in the sprint file. One look, so the team is not refreshing a dashboard instead of delivering cards.

Step eight: do not rescue. When a request sits unconfirmed for a day, the team does not message the host to remind her. A host who does not confirm is the finding. Reminding her erases it.

## Common mistakes and how to spot them

**Friends and classmates as users.** They open it because they like you. Spot it: each person in your table has a log number or a session number beside them.

**A broadcast instead of a hand-off.** One message to a group, fifty opens, no requests. Spot it: your table has a teammate's initials and a day on every row.

**Sending a preview link.** The tester meets a login wall and says nothing. Spot it: open the exact link you are sending in a private window on a phone.

**A prediction written on Thursday.** By then it is a description. Spot it: the commit that added the prediction is from the lab.

**Helping.** Sitting beside the user and pointing. Spot it: if you spoke during their first use, log it as a moderated session, not a field event.

**Testing on their record.** Your own clicks on a real host's link become her requests. Spot it: your team's test record is the only one any teammate touches.

**No way for them to say something broke.** Spot it: every person has one named teammate they already know how to reach.

## Check yourself

1. For each person in your field table: which log or session do they come from, and who on your team hands them the link?
2. What is your prediction, and what number would make you say you were wrong?
3. A real user gets stuck on day two and does nothing further. What do you do, and what do you write down?
