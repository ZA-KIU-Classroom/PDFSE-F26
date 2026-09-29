# Running and Logging an Interview

*Concept guide for Lab 2, practice round and homework. About 8 minutes to read.*

## The idea, in plain language

A script is a plan. The interview is where it meets a real person, and two things decide whether you leave with evidence or a pleasant memory: how you run it, and how you record it.

**Running it.** Interview in pairs: one asks, one logs, never both. The asker owns the eye contact and follows the story, using "and then what?" and silence to keep the person on specific past events. The logger writes their words verbatim and, at the end, asks one question the asker missed.

**Recording it.** One log file per interview, written within 24 hours, with at least three verbatim quotes: their words, in the language they spoke, not your summary. Surprises get a star. The log carries your prediction, so you see whether the interview confirmed it or broke it.

**Consent, always first.** Before you take a single note, say who you are, what the notes are for, and that you will not use their name. If they say no to notes, you can still talk; you write your log immediately afterward and mark it "from memory". Full names, phone numbers, and addresses never go into your public repository. Use a code name and a role: "Host, 6 rooms, Oni".

## Why it matters in practice

In 1974, two researchers, Elizabeth Loftus and John Palmer, showed people film clips of car accidents and then asked how fast the cars were going. The only difference between groups was one verb. Some were asked how fast the cars were going when they "hit" each other. Others heard "smashed".

The "smashed" group estimated noticeably higher speeds. A week later, the researchers asked everyone whether they had seen broken glass in the film. There was no broken glass. About a third of the "smashed" group said yes, roughly twice the rate of the "hit" group.

Two lessons. First, the wording of a question changes the answer, which is why your script matters. Second: memory is not a recording. It is rebuilt each time you recall it, filling in details that fit what you expected. An interviewer who writes up notes three days later remembers the host saying what the interviewer already believed. Nobody lied; that is how memory works.

The 24-hour and verbatim rules are your only protection against your own brain editing the evidence.

## Worked example, step by step

Here is one Sakhli interview, from arrival to committed log.

**Step 1: Before the interview (5 minutes).** Luka (asker) and Mariam (logger) reread the script and the prediction: "We are wrong if hosts do not raise the commission themselves before we mention it." Mariam copies the prediction into a fresh log file.

**Step 2: Opening and consent (1 minute).** Luka: "We're students at KIU learning how family guesthouses handle bookings. We're not selling anything. Is it okay if Mariam takes notes? We won't use your name." The host agrees to notes, not recording. Mariam writes "Consent: yes, notes only".

**Step 3: The core (15 to 20 minutes).** Luka asks the host to walk through the last booking. She talks about her son writing English replies. Luka asks "and then what?", and she explains that when her son is in Tbilisi, nobody answers. Luka waits three seconds. She adds: "In August I don't sleep. I check the phone at three in the morning." Mariam writes it word for word and stars it; it has nothing to do with the prediction.

**Step 4: The moment you want to pitch.** The host says, "Someone should make an app for this." Luka feels the pull to describe the idea. Instead: "What would it need to do for you?" Then, before she can design it, back to the past: "When did you last feel that?"

**Step 5: The close (2 minutes).** "Who else in the valley should we talk to?" She names two neighbors who also host. Mariam logs it under Commitment. Now, with the unprompted part safely over, Mariam asks her one question: "What does Booking.com cost you?" The host shrugs: "Everyone pays it. It is the price of guests." That line quietly dismantles the prediction.

**Step 6: The log, that evening.** Mariam fills in the template from her notes while the words are fresh: context, prediction, quotes in Georgian with English beside them, the workaround, the cost, the surprise, and next steps. Luka reads it, adds one quote Mariam missed, and they commit it. The finished log is `examples/sakhli-interview-log-01.md`.

**Step 7: Update the script.** The next interview gets one new question: "Tell me about the last time you worried about a double-booking." That is how discovery compounds.

## Common mistakes, and how to spot them

**Paraphrased quotes.** "She said bookings are stressful." Spot it by the missing quotation marks and the word "said". If you cannot put it in quotes, you did not capture it.

**One person doing both jobs.** The asker who takes notes loses eye contact and misses follow-ups; the notes come out thin. Spot it in the log: short quotes, no stars, no "next".

**Logging days later.** Spot it when every quote in the log conveniently supports the prediction. Real interviews are messier than that.

**Identifying details in the repo.** A real name, a phone number, the name of a small guesthouse that makes the host identifiable. Spot it by reading your log as a stranger: could you find this person from it? If yes, anonymize before committing.

**Counting practice as real.** The interview you did with a classmate in the lab is practice unless that classmate actually has the problem and is outside this course. Mark it "practice" in the log header and file it in `interview-logs/practice/`.

## Check yourself

1. Your team interviewed a host on Monday and wrote the log on Friday. Every quote supports your prediction. What does the Loftus and Palmer study suggest might have happened?
2. Mid-interview, the person says: "Honestly, I would pay for something that fixed this." What do you log, and what do you ask next?
3. The host agrees to talk but refuses notes. What do you do during and after the interview so the log is still useful?
