# Sizing Sprint 1 to Real Hours

## The concept

A sprint plan that survives a part-time week starts with a number: the hours each teammate actually has free before the Week 7 lab, when, specifically, added up. Every story is then sized in hours by the person who will build it, and the sum of the stories must not exceed the total. The plan ends with a slip rule, written while everyone is rested: which story is most likely to overrun, what part of it moves to Sprint 2 if it does, and what part stays no matter what because the value does not land without it.

The number is a ceiling, not a target. Plans sized to wished-for hours are the main reason teams miss the gate.

## Why it matters

A team of three with jobs, other courses, and exams has twelve to thirty hours before the Week 7 lab, not forty. Every Spring team that missed the gate had planned as if the hours were there. The deadline arrived, the last story was half built, and the missing half was the one with the value in it, because teams build in journey order and the value is at the end.

The failure story is from Spring. A team of three planned seven stories for Sprint 1. Nobody counted hours. The plan assumed every evening. Two members had exams in another course in the sprint's second week. By the Week 7 lab, stories one to four were done and five to seven were not, and story six was the one where the user got the value. They deployed a product people could start and not finish, and the break data showed exactly that. A plan sized to their real fourteen hours would have held four thin stories and shipped a complete journey with less polish.

## Worked example, step by step

Sakhli, Lab 6, checkpoint 3.

Step one: count. NK works Tuesday to Saturday: two evenings and a Sunday morning, six hours. GT has no job this month: four evenings, each capped at two hours, because after two hours the code gets worse, eight. LK has exams in two other courses: a Saturday afternoon and one evening, five. Nineteen hours. The "when, specifically" column matters, because it turns a guess into a calendar.

Step two: one story per journey step, in value order. Five steps, five stories, with the deploy as a sixth that happens in the Week 7 lab. The north star step, the host confirms, is written first.

Step three: the owner sizes each story. GT: link page, four; request form, four. NK: host page and confirm, five, because of the date logic. LK: confirmation and calendar block, four. Deploy: two, in the lab, NK and LK. Nineteen. It fits with nothing to spare, which is normal.

Step four: when it does not fit, thin the stories, do not drop the last one. If the sum had been twenty-four, the move is not to cut S4. It is to make S1 thinner: no photo, a plain date input instead of a picker, two hours instead of four. The journey stays complete; the screens get uglier. Ugly and complete beats polished and half.

Step five: write the slip rule. S4 is the most likely to overrun, because email delivery has a third party in it. If S4 is not done by the Wednesday before the Week 7 lab, the email moves to Sprint 2 and the guest gets the confirmation on screen only. The calendar block stays, because without it the value does not land. The rule names the story, the date, the part that moves, and the part that stays.

Step six: put the board up and merge daily. Four columns, one card per story.

## Common mistakes and how to spot them

**Counting hours awake instead of hours free.** A total of forty-five for three people with jobs. Spot it: the "when, specifically" column. If a row cannot name the evenings, the number is a wish.

**Sizing by the person who will not build it.** The most confident teammate estimates everyone's work. Spot it: the owner's initials and the hours are written by the same person.

**Dropping the last story to fit.** The sum is too high, so the step where the value lands moves to Sprint 2. Spot it: the last story is the value; thin the first ones instead.

**No slip rule, or a slip rule written at midnight.** Spot it: the slip rule is in the committed plan on lab day. A rule written during the slip protects the thing that is easiest, not the thing that matters.

**The sprint planned to the deadline with nothing for the deploy.** Every hour assigned to building; deploy "will be quick." Spot it: the deploy is its own story with its own hours, and it happens in the Week 7 lab on the clock.

## Check yourself

1. What is your team's total, and can every row name the specific evenings behind its number?
2. If the sum of stories were four hours over, which story gets thinner, and what is the ugliest acceptable version of it?
3. Read your slip rule. Does it name the story, the date, the part that moves, and the part that stays?
