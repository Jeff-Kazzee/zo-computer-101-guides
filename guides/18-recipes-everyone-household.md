---
title: "10 ways Zo handles the household admin you keep forgetting"
id: recipes-everyone-household
category: recipes
kind: recipe-pack
audience: everyone
order: 3
date: 2026-06-18
updated: 2026-06-18
excerpt: Bills, renewals, appointments, school dates, and the slow creep of subscriptions. 10 household automations that catch the admin before it bites, each copy-paste ready.
tags: [automations, recipes, everyone, household, calendar, email, scheduling, conditional-alerts]
related: [zo-automations-101, plugin-inside-automation, zo-plugins-integrations]
difficulty: beginner
reading_time: 9
---

The expensive household mistakes are almost never dramatic. A free trial you meant to cancel renews at $14.99 and you don't notice for four months. The dentist appointment you booked in February is tomorrow at 2pm and nobody told the calendar. The return window on the thing that broke closed three days ago. None of it is hard to track. It's just one more thing, and one more thing is exactly the thing a brain running a household drops on the floor.

That floor is where automations earn their keep. Most of this admin is "watch a date or an inbox and only speak up when it matters," which is the one job a scheduled prompt does without getting tired or distracted. Here are 10 you can paste into Zo today. Each one follows the same shape: what it does, what you need connected, the exact prompt, the tweak that keeps it quiet, and the failure to watch for. Connect the plugins first (the integrations guide walks through that), then talk to Zo in plain English. Change the times, names, and amounts to fit your house. None of these are scripture.

> A reminder that fires every single day gets swiped away on autopilot by Thursday. A reminder that only fires when a charge is about to hit, or a window is about to close, is the one you actually read. Build the second kind.

## 1. The bill due before it's late

**What it does:** Flags a bill that's coming due so the late fee never happens.
**You need:** Google Calendar and Gmail connected.
**The prompt:**
```
Every weekday at 8:00am Mountain, check my Google Calendar and my Gmail
for any bill, payment, or due date landing in the next 3 days. Text me a
short list with what it is, the amount if you can find it, and the date.
If nothing's due, stay quiet.
```
**Make it quieter:** The "stay quiet" line already does it. Widen the window to 5 days only if you pay things by mail.
**Watch out for:** It can only catch bills that show up as a calendar event or an email. Autopay charges with no notice won't appear, so the subscription watcher below covers that gap.

## 2. The free-trial assassin

**What it does:** Warns you before a free trial or an annual renewal quietly charges your card.
**You need:** Gmail connected.
**The prompt:**
```
Every Monday at 9:00am Mountain, search my Gmail for trial confirmations,
renewal notices, and "your subscription renews" emails. Tell me about any
trial ending or annual renewal charging in the next 10 days, with the
service name, the amount, and the date it hits. If there are none, one line
saying so.
```
**Make it quieter:** Bump the schedule to twice a week (Monday and Thursday) only if you sign up for a lot of trials. Most people don't need it daily.
**Watch out for:** Plenty of services hide the renewal date in the original signup email from months ago, not a fresh reminder. Tell Zo the service names you actually worry about so it knows to dig for those.

## 3. The week's appointments, in one digest

**What it does:** One Sunday-night rundown of every appointment so nothing ambushes you Tuesday.
**You need:** Google Calendar connected.
**The prompt:**
```
Every Sunday at 6:00pm Mountain, read my Google Calendar for the next 7
days and email me every appointment that isn't a recurring work meeting:
doctor, dentist, vet, haircut, car, anything personal. Include the time,
the place, and a note if I need to bring or prep anything.
```
**Make it quieter:** Add "skip the email if there are no personal appointments this week." Some weeks are empty and that's fine.
**Watch out for:** The "bring or prep" note is only as good as what you typed into the event. If you wrote "dentist" with no other detail, Zo has nothing to remind you about.

## 4. The family calendar weekly digest

**What it does:** Pulls school dates, kid stuff, and family events into one shared brief everyone can see coming.
**You need:** Google Calendar connected (the shared family calendar specifically).
**The prompt:**
```
Every Sunday at 7:00pm Mountain, read my [family/school] Google Calendar
for the coming week and email me a digest: early dismissals, days off,
practices, recitals, permission-slip or signup deadlines, and anything
needing a parent there. Group it by day. Flag anything that needs an RSVP.
```
**Make it quieter:** Keep this one weekly and unconditional. The whole value is the predictable Sunday-night picture, so don't gate it.
**Watch out for:** School portals love to bury dates in PDFs and newsletters that never reach a calendar. If your district does that, this digest only sees what someone actually added as an event.

## 5. The package tracker that watches for you

**What it does:** Tells you what's arriving and what got stuck, without you logging into four carrier sites.
**You need:** Gmail connected.
**The prompt:**
```
Every weekday at 5:00pm Mountain, scan my Gmail for shipping and delivery
emails from the last 24 hours. Text me what's out for delivery or arriving
today, and flag anything marked delayed, exception, or returned to sender.
Skip stuff already delivered.
```
**Make it quieter:** Add "only text me if something is arriving today or has a delivery problem." A list of packages three days out is noise.
**Watch out for:** Some retailers send tracking from a no-reply address that buries the real status. If a package never shows up in the digest, search your inbox for it once and Zo learns the sender pattern.

## 6. The return window that closes on you

**What it does:** Catches the return or warranty deadline before it expires and the thing you hate becomes yours forever.
**You need:** Gmail connected, plus a notes file or spreadsheet for the running list.
**The prompt:**
```
Every Monday at 10:00am Mountain, find order confirmation and delivery
emails from the last 45 days. For each purchase, estimate the return
window (assume 30 days unless the email says otherwise) and add it to my
[returns file]. Email me anything whose return window closes in the next
7 days so I can decide to keep or send it back.
```
**Make it quieter:** The 7-day warning is the conditional part. To cut noise further, tell it to only track purchases over $40, since you're not driving to the store to return a $6 cable.
**Watch out for:** Thirty days is a guess, not the truth. Store policies run anywhere from 14 days to a year, and "estimate" is doing real work in that prompt. Treat the warning as a prompt to check the actual policy, not gospel.

## 7. The chore rotation that names a name

**What it does:** Rotates a recurring household chore through the people who do it, so it's never a vague "someone should."
**You need:** Nothing required if you list the names in the prompt; connect Google Tasks or Notion if you want it written somewhere.
**The prompt:**
```
Every Sunday at 5:00pm Mountain, it's time to rotate the trash-and-recycling
duty. The rotation is [name A], then [name B], then [name C], repeating.
Text me whose turn it is this week and remind them what day pickup is.
Keep track so it advances by one person each week.
```
**Make it quieter:** This one you want every week by design. Don't gate it. If anything, add a second chore on a different day rather than skipping runs.
**Watch out for:** Zo keeps the rotation position between runs, but if you ever pause or delete the automation and rebuild it, the count restarts. Note the last person in the prompt when you set it up so it picks up in the right spot.

## 8. The price watch on the thing you want

**What it does:** Watches a wishlist item's price and only pings you when it actually drops.
**You need:** Nothing connected; Zo reads public pages.
**The prompt:**
```
Every day at 11:00am Mountain, check the price on [product page URL].
Compare it to the last price you saw. Text me only if it dropped, with the
new price and how much it fell. If it didn't drop, stay silent. Note the
price each day so you have something to compare against.
```
**Make it quieter:** It's already drop-gated, so it's silent most days. Set a floor instead: "only text me if it falls below $[target]."
**Watch out for:** Big retailers throw up bot blocks and the page can fail to load. Tell Zo to flag a read failure instead of going quiet, otherwise a broken check looks identical to "no price drop."

## 9. The car registration and oil-change nag

**What it does:** Reminds you about registration renewal, inspection, and the next service before any of them lapse.
**You need:** Google Calendar connected; a notes file if you want to log mileage.
**The prompt:**
```
Every Monday at 9:00am Mountain, check for car deadlines coming up in the
next 30 days: registration renewal on [month], inspection, and the next oil
change (roughly every [6 months / 5,000 miles] from the last one on [date]).
Email me anything due soon. If nothing's within 30 days, skip the email.
```
**Make it quieter:** The 30-day window plus "skip if nothing's due" keeps it silent for most of the year. Leave it.
**Watch out for:** Mileage-based service is the weak spot, because Zo can't read your odometer. It can only count from a date you give it. If you drive a lot more or less than average, treat the oil-change ping as a "go check the sticker" nudge.

## 10. The Sunday "what's coming up" household brief

**What it does:** One calm message that lays out the whole week before it starts: appointments, bills, deliveries, family stuff.
**You need:** Google Calendar and Gmail connected.
**The prompt:**
```
Every Sunday at 4:00pm Mountain, give me a single household brief for the
week ahead. Read my calendar and recent Gmail and cover: personal
appointments, bills or payments due, packages expected, renewals about to
charge, and any family or school dates. Group it by day, keep it under 250
words, and end with the two things I most need to not forget.
```
**Make it quieter:** This is the one weekly message you want even on a slow week, so don't make it conditional. If it ever runs long, tighten the word limit instead.
**Watch out for:** This brief overlaps with the narrower recipes above on purpose. Run this one alone first, and only add the specific watchers (free trials, returns, price drops) for the things this weekly summary catches too late.

## Before you paste all 10

Two rules keep this from becoming background noise you eventually mute. First, build them one at a time. Get the bill reminder right, live with it for a week, then add the next. Ten automations stood up in one Saturday and never tuned is ten things you'll be ignoring by next Saturday. Second, the ones that touch real money or read your full inbox deserve a leash. Run them under a scoped persona that can read your email and draft a reminder but cannot send anything, charge anything, or post anywhere on its own. The plugin-in-automation guide shows exactly how to box a persona in like that.

Start with the free-trial assassin and the bill reminder. Those two pay for the whole idea inside a month, usually the first time one of them catches a $120 annual renewal you forgot you signed up for. Once you feel that, the rest are obvious.

If you're starting from zero, read the automations explainer first, because the recipes that use Gmail, Stripe, or Notion need those connected first (the public-web ones don't). Then pick one, not ten. This is the kind of guide I write every week. They live at jeffkazzee.zo.space/writing.
