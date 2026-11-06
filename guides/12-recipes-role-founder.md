---
title: "12 automations every solo founder should steal"
id: recipes-role-founder
category: recipes
kind: recipe-pack
audience: role
order: 1
date: 2026-06-18
updated: 2026-06-18
excerpt: You're the founder, the ops team, and the assistant. Here are 12 automations that hand the assistant job to Zo, each one copy-paste ready with the plugins it needs and the failure to watch for.
tags: [automations, recipes, founder, reporting, triage, calendar, email, stripe, scheduling, conditional-alerts]
related: [zo-automations-101, plugin-inside-automation, zo-plugins-integrations]
difficulty: beginner
reading_time: 9
---

If you run a company alone, the time sink is admin: inbox triage, calendar wrangling, the "did that customer ever pay" check, the weekly numbers you keep meaning to look at. That layer is exactly what an automation is good at, because most of it is "look at something on a schedule and only bother me if it matters." Here are 12 you can paste into Zo today.

Each one follows the same shape: what it does, what you need connected, the exact prompt to give Zo, the tweak that keeps it quiet, and the failure to watch for. Connect the plugins first (the integrations guide covers that), then talk to Zo in plain English. Every prompt here is a starting point, not scripture. Change the times, names, and thresholds to fit you.

> An automation that pings you every day gets muted in a week. An automation that pings you only when something's wrong gets trusted for years. Build the second kind.

## 1. The morning brief that replaces six tabs

**What it does:** One message before you open your laptop, with today's calendar, overnight VIP email, and anything urgent.
**You need:** Google Calendar and Gmail connected.
**The prompt:**
```
Every weekday at 7:00am Mountain, read my Google Calendar for today and
my Gmail from the last 16 hours. Email me a brief: my meetings with times,
any email from a customer or investor, and anything that looks time-sensitive.
Keep it under 200 words.
```
**Make it quieter:** Add "skip the email entirely if there are no meetings and no urgent messages."
**Watch out for:** "Urgent" is your judgment, not Zo's. Name your real VIPs in the prompt or it guesses.

## 2. Invoice-paid watcher

**What it does:** Tells you when money lands, so you stop refreshing Stripe.
**You need:** Stripe connected.
**The prompt:**
```
Every weekday at 6:00pm Mountain, check Stripe for payments received today.
Text me the count and total. If a payment over $500 came in, name the customer.
```
**Make it quieter:** Change to "text me only on days a payment actually came in."
**Watch out for:** Stripe test mode and live mode are separate. Tell Zo which one you mean.

## 3. The unpaid-invoice nag (for you, not them)

**What it does:** Surfaces invoices that have gone quiet so you can follow up.
**You need:** Stripe connected.
**The prompt:**
```
Every Monday at 9:00am Mountain, check Stripe for invoices that are unpaid
and more than 7 days past their due date. Email me the list with customer,
amount, and days overdue. If there are none, say so in one line.
```
**Make it quieter:** It's already weekly and conditional-friendly. Leave it.
**Watch out for:** This drafts your follow-up list. It does not send anything to customers unless you explicitly tell it to, and you should keep it that way.

## 4. Meeting prep, automatically

**What it does:** Before each meeting, a short brief on who you're meeting and what's open with them.
**You need:** Google Calendar and Gmail connected.
**The prompt:**
```
Every weekday at 8:00am Mountain, look at my calendar for today's external
meetings. For each one, search my Gmail for the most recent thread with that
person and summarize where we left off in two lines. Email me the set.
```
**Make it quieter:** Add "only include meetings with someone outside my company."
**Watch out for:** It can only see what's in your connected inbox. Context from elsewhere won't show up.

## 5. End-of-day "what did I not answer"

**What it does:** Catches the email you meant to reply to and forgot.
**You need:** Gmail connected.
**The prompt:**
```
Every weekday at 5:30pm Mountain, find emails I received today that look like
they need a reply and that I haven't responded to. Email me the short list
with sender and subject. Skip newsletters and automated mail.
```
**Make it quieter:** Add "only send if there are 1 or more unanswered."
**Watch out for:** "Looks like it needs a reply" is fuzzy. Expect a few false positives the first week, and refine the prompt.

## 6. The weekly numbers, written for you

**What it does:** Your real metrics in three lines every Friday, no dashboard.
**You need:** Stripe connected (and any data file you keep).
**The prompt:**
```
Every Friday at 4:00pm Mountain, pull this week's Stripe payments, refunds,
and whatever customer metric my connected Stripe view actually exposes.
Compare to last week. Email me a three-line summary with the direction each
number moved. If a field isn't available, say so instead of guessing.
```
**Make it quieter:** This one you want every week. Keep it on a schedule, not conditional.
**Watch out for:** Define your week (Mon-Sun vs Sun-Sat) in the prompt so the comparison is honest. And don't trust a number you can't trace. If Stripe doesn't expose a clean "new customers" count for your setup, the prompt above tells Zo to flag it rather than invent one.

## 7. Competitor / market watch

**What it does:** Checks a few pages weekly and tells you only what changed.
**You need:** Nothing connected; Zo reads public pages.
**The prompt:**
```
Every Monday at 10:00am Mountain, check [competitor pricing page URL] and
[competitor blog URL]. Compare to what you saw last week and email me only
the things that changed. If nothing changed, email me one line saying so.
```
**Make it quieter:** Already change-gated. Add more URLs as you find them.
**Watch out for:** Some sites block automated reads. If one keeps failing, tell Zo to note it instead of failing silently.

## 8. Content calendar that drafts ahead

**What it does:** Keeps your marketing from going dark by drafting the week.
**You need:** Notion connected (or just your files).
**The prompt:**
```
Every Sunday at 6:00pm Mountain, look at my content plan in Notion. For any
slot in the next 7 days that's still empty, draft a first version and add it
as a draft. Email me what you drafted so I can review before anything ships.
```
**Make it quieter:** Add "only email me if you drafted something."
**Watch out for:** This drafts; it never publishes. Keep the human gate before anything goes public.

## 9. The "someone important emailed" instant ping

**What it does:** Real-time alert for the handful of senders you can't miss.
**You need:** Gmail connected.
**The prompt:**
```
Every 30 minutes between 8am and 7pm Mountain on weekdays, check Gmail for
new email from [name], [name], or anyone at [keydomain.com]. Text me only
if one arrived, with sender and subject.
```
**Make it quieter:** This is the conditional. It stays silent unless a named person writes.
**Watch out for:** Every run spends credits. Thirty minutes is fine for a short window; don't set it to every 5 minutes around the clock.

## 10. Receipts and expenses into one place

**What it does:** Pulls receipt emails into a running list so tax time isn't archaeology.
**You need:** Gmail connected, plus a spreadsheet or file to write to.
**The prompt:**
```
Every Friday at 5:00pm Mountain, find receipt and invoice emails I received
this week. Pull out vendor, amount, and date, and append them to my
expenses file. Email me the week's total.
```
**Make it quieter:** Add "only email me the total if it's above $0."
**Watch out for:** It reads what it can parse. Odd receipt formats may need a nudge; check the file the first few weeks.

## 11. The standing-meeting agenda builder

**What it does:** Builds the agenda for a recurring meeting from the week's activity.
**You need:** Gmail and your task or project tool connected.
**The prompt:**
```
Every Thursday at 3:00pm Mountain, build a short agenda for my Friday team
sync: open items from this week's email, anything blocked, and decisions I
flagged. Email it to me as a bulleted draft.
```
**Make it quieter:** Keep it weekly. It's prep, not an alert.
**Watch out for:** It only knows what's in the tools it can see. Tell it where the real work lives.

## 12. The "did I forget to follow up" safety net

**What it does:** Catches threads where you said you'd do something and went quiet.
**You need:** Gmail connected.
**The prompt:**
```
Every Wednesday at 9:00am Mountain, scan my sent Gmail from the last two
weeks for emails where I promised to follow up or send something, then check
whether I did. Email me the ones that look unresolved.
```
**Make it quieter:** Add "only send if you find at least one open loop."
**Watch out for:** This reads your sent mail, which is more sensitive. If that's not okay, skip this one.

## Before you paste all twelve

Two rules that keep this from turning into noise you mute. First, build them one at a time, get each one right, then add the next. Twelve automations installed in one afternoon and never tuned is twelve things you'll ignore by Friday. Second, the ones with real access (your sent mail, your Stripe, your ability to send) are worth running under a scoped persona that can read and draft but cannot send, post, or charge on its own. The plugin-in-automation guide covers exactly how to box them in.

Pick the morning brief and the VIP ping first. Those two earn the whole idea in a day, and once you feel it, the rest are obvious.

Most of these want a plugin connected first, so if you haven't wired up Gmail and your calendar yet, the integrations guide is the place to start. A few need nothing but a URL, because Zo can read a public page on its own. Either way, build one, run it for a week, then add the next. The full Zo Computer 101 library is at jeffkazzee.zo.space/writing.
