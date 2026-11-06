---
title: "12 automations that quietly run your life"
id: recipes-everyone-daily-life
category: recipes
kind: recipe-pack
audience: everyone
order: 2
date: 2026-06-18
updated: 2026-06-18
excerpt: You don't run a company. You run a life, and it has just as much admin. Here are 12 automations that handle the forgettable stuff, each copy-paste ready with what to connect and the failure to watch for.
tags: [automations, recipes, everyone, calendar, email, reminders, scheduling, conditional-alerts, weather, journaling]
related: [zo-automations-101, plugin-inside-automation, zo-plugins-integrations]
difficulty: beginner
reading_time: 9
---

Founders get all the automation guides, which is backwards. The person who needs this most is whoever is holding a job, a household, and a brain that keeps dropping the same five things: the bill that sneaks up, the prescription refill, the friend you meant to text back. A life has admin too, and most of it is "remind me about a thing at the right moment, and only then." Here are 12 automations you can paste into Zo today, none of which require you to run a business.

Each one follows the same shape: what it does, what you need connected, the exact prompt to give Zo, the tweak that keeps it quiet, and the failure to watch for. Connect the plugins first (the integrations guide covers that), then talk to Zo in plain English. Change the times, names, and thresholds to fit your actual life.

> The best automation isn't the clever one. It's the boring one that means you never again think "I forgot to do that thing" at 11pm.

## 1. The morning you, briefed

**What it does:** One message when you wake up: today's calendar, the weather, and anything you flagged.
**You need:** Google Calendar connected.
**The prompt:**
```
Every day at 7:00am Mountain, read my Google Calendar for today and check
today's weather for [your city]. Text me a short brief: what's on my
calendar with times, and whether I need a jacket or an umbrella.
```
**Make it quieter:** Add "skip days where I have nothing scheduled."
**Watch out for:** It reads the calendar it's connected to. If your life is split across two calendars, connect both or it misses half.

## 2. Bills before they're late

**What it does:** Warns you a few days before a recurring bill is due, so nothing hits a late fee.
**You need:** Nothing connected; you give Zo the dates once.
**The prompt:**
```
I have these recurring bills: rent on the 1st, phone on the 12th, car
insurance on the 20th. Every day at 8:00am Mountain, text me only if a bill
is due in exactly 3 days, naming it and the amount.
```
**Make it quieter:** It's already conditional. It stays silent except on the 3-day mark.
**Watch out for:** Zo doesn't see your bank. This is a reminder from the list you gave it, not a balance check. Update the list when a bill changes.

## 3. The prescription / refill nudge

**What it does:** Reminds you to refill before you run out, on your real cycle.
**You need:** Nothing connected.
**The prompt:**
```
My prescription needs refilling every 30 days; the last refill was June 10.
Text me 4 days before I'd run out so I have time to call it in. Just that
reminder, nothing else.
```
**Make it quieter:** Already a single conditional ping. Leave it.
**Watch out for:** This is a clock, not a pharmacy. It can't see your actual supply, so keep the refill date honest when it changes.

## 4. "Text them back" before you forget

**What it does:** Surfaces the messages you meant to answer and let slip.
**You need:** Gmail connected (works for email; texts it can't see).
**The prompt:**
```
Every day at 6:00pm Mountain, find personal emails from the last 3 days that
look like they're waiting on a reply from me and that I haven't answered.
Text me a short list of who and about what. Skip newsletters and receipts.
```
**Make it quieter:** Add "only send if there's at least one."
**Watch out for:** It only sees email. The friend who texted you is invisible to it; this catches the inbox, not your phone.

## 5. The weekly meal plan and grocery list

**What it does:** Plans the week's dinners and hands you a shopping list.
**You need:** Nothing connected (or Notion if you want it saved there).
**The prompt:**
```
Every Saturday at 10:00am Mountain, plan 5 dinners for the week using simple
ingredients, no repeats from last week. Email me the plan plus a grocery
list grouped by section of the store.
```
**Make it quieter:** Keep it weekly; it's a plan, not an alert.
**Watch out for:** Tell it your constraints up front (no shellfish, cooking for two, under 30 minutes) or you'll get generic meals.

## 6. Rain check, literally

**What it does:** Texts you only when rain or snow is coming, so you can plan around it.
**You need:** Nothing connected.
**The prompt:**
```
Every day at 6:30am Mountain, check today's forecast for [your city].
Text me only if there's rain, snow, or a high above 90 or below 25.
Otherwise stay quiet.
```
**Make it quieter:** This is the quiet version. It only speaks on notable weather.
**Watch out for:** Forecasts move. Treat it as a heads-up, not a guarantee.

## 7. The package-arrival digest

**What it does:** Collects shipping and delivery emails into one "here's what's coming" note.
**You need:** Gmail connected.
**The prompt:**
```
Every day at 9:00am Mountain, scan my Gmail for shipping and delivery
updates. Email me a short list of what's arriving today and what's still
in transit. Skip anything already delivered.
```
**Make it quieter:** Add "only send if something is arriving today."
**Watch out for:** It reads the emails retailers send. If a store doesn't email tracking, that package won't show up.

## 8. A reading list that builds itself

**What it does:** Turns the links you save into a tidy weekly list instead of a graveyard of tabs.
**You need:** A file or note where you drop links.
**The prompt:**
```
I save links to a file called reading-list. Every Sunday at 7:00pm Mountain,
read the new ones added this week, give each a one-line summary, and email me
the organized list. Then mark them as processed.
```
**Make it quieter:** Keep it weekly.
**Watch out for:** It can summarize public pages. Anything behind a paywall or login it can't fully read, so it'll note that instead.

## 9. The habit nudge that doesn't nag

**What it does:** A single, well-timed push for the habit you're building, worded like a person.
**You need:** Nothing connected.
**The prompt:**
```
I'm trying to walk my dog every evening. Every day at 5:00pm Mountain, send
me one short, friendly nudge to get out the door. Vary the wording so it
never feels like the same robot message twice.
```
**Make it quieter:** One ping a day is the floor. Drop it to 3 days a week if daily feels naggy.
**Watch out for:** A nudge is not accountability. If you want it to notice when you skip, you'd have to tell it whether you went, which is more than most people keep up.

## 10. The "good news only" digest

**What it does:** A short, curated read on a topic you actually enjoy, instead of doomscrolling.
**You need:** Nothing connected; Zo searches the web.
**The prompt:**
```
Every morning at 8:00am Mountain, find 3 genuinely positive or interesting
stories from the last day about space, science, or dogs. Email me the
headlines with a one-line summary and the link.
```
**Make it quieter:** Already low-volume. Tune the topics to what you'd actually open.
**Watch out for:** "Positive" is interpreted loosely. Refine the topics over a week until the picks feel right.

## 11. Trip-price watch

**What it does:** Watches a route or trip and tells you when it's worth booking.
**You need:** Nothing connected; Zo checks public pages.
**The prompt:**
```
Every day at noon Mountain, check flight prices from [your airport] to [destination] for
the weekend of [date]. Text me only if a round trip drops below $200.
```
**Make it quieter:** This is the conditional version; it stays silent above your threshold.
**Watch out for:** Some travel sites block automated checks or show different prices. If it keeps failing, have it tell you instead of failing in silence.

## 12. Journal by text

**What it does:** Lets you capture a thought by texting it, filed and dated for you.
**You need:** SMS set up with Zo.
**The prompt:**
```
When I text you a message that starts with "j:", strip the prefix and append
it to my journal file for today with a timestamp. Reply with one word so I
know it landed. Don't analyze it, just file it.
```
**Make it quieter:** This one only acts when you text it. It's silent otherwise by design.
**Watch out for:** It's a capture tool, not a therapist. Keep the prompt to filing, and review the journal yourself.

## Before you paste all twelve

Two rules so this stays useful instead of becoming background noise. Build them one at a time, get each one feeling right, then add the next. A dozen reminders installed in one sitting and never tuned is a dozen things you'll mute by next week. And for the ones that read your email or your journal, run them under a scoped persona that can read and draft but cannot send or post on its own. The plugin-in-automation guide shows exactly how to box them in.

Start with the morning brief and the bills reminder. Those two alone replace a low hum of background worry, and once you feel that, the rest are easy. If your plugins aren't connected yet, read the automations explainer first. This is the kind of guide I write every week. They live at jeffkazzee.zo.space/writing.
