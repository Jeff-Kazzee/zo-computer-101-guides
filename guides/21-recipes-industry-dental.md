---
title: "11 automations for a dental or medical front office"
id: recipes-industry-dental
category: recipes
kind: recipe-pack
audience: industry
order: 3
date: 2026-06-18
updated: 2026-06-18
excerpt: Appointment reminders, recall lists, no-show follow-up, and the front-desk admin that piles up. 11 front-office automations, each with a draft-first human gate because this touches patients.
tags: [automations, recipes, dental, triage, email, calendar, scheduling, conditional-alerts]
related: [zo-automations-101, plugin-inside-automation, zo-plugins-integrations]
difficulty: beginner
reading_time: 9
---

The front desk runs on small things that fall through cracks. A patient who hasn't been in for 14 months and never got a recall call. A claim that's been sitting with the insurer for three weeks while nobody followed up. A 2pm opening that could have been filled if anyone noticed it by 9am. None of that is hard work. It's just constant, and it competes with the phone ringing and someone standing at the counter. That layer is what an automation handles well, because most of it is "look at the schedule or the inbox on a clock and tell me what needs a human." Here are 11 you can paste into Zo.

Every one of these drafts. None of them sends anything to a patient on its own. That's not a setting you can flip later as a convenience. It's the whole design, because the moment an automation can text a patient without a person reading it first, you've built a liability instead of a tool. Connect your plugins first (the integrations guide walks through it), keep patient names and any health detail out of the prompts, and let Zo prepare the work for a human to send.

> A reminder Zo drafts and a person sends is a helpful front desk. A reminder Zo sends on its own is a complaint waiting to happen. Always build the first one.

## 1. The morning schedule read

**What it does:** One message before the doors open, with today's appointment count, the gaps, and anything that looks off.
**You need:** Google Calendar connected (or whatever calendar your practice management software syncs to).
**The prompt:**
```
Every weekday at 7:00am Mountain, read my Google Calendar for today.
Email me a brief: how many appointments are booked, the open time blocks
longer than 30 minutes, and any double-booking or back-to-back with no
buffer. Keep it under 150 words. Do not include patient names, just times
and appointment types.
```
**Make it quieter:** Add "skip the email if the day is fully booked with no gaps and no conflicts."
**Watch out for:** Zo only sees what's actually on the connected calendar. If your operatory schedule lives only inside Dentrix or Eaglesoft and never syncs out, it can't read it. Confirm the sync before you trust this.

## 2. The recall list nobody pulled

**What it does:** Surfaces patients overdue for a cleaning or follow-up so someone can call them.
**You need:** Google Sheets connected (or a recall export file you keep).
**The prompt:**
```
Every Monday at 8:30am Mountain, read my recall tracking sheet. Pull the
rows where the next-due date has already passed and no future appointment
is booked. Email me the count and the list by initials and due date only,
sorted by most overdue first. Do not send anything to anyone.
```
**Make it quieter:** Add "only email me if there are 5 or more overdue."
**Watch out for:** This is a call list for your team, not an outreach tool. Keep full patient detail in your sheet and tell Zo to work off initials so the email itself carries less. The actual calling stays human.

## 3. No-show follow-up, drafted

**What it does:** Catches yesterday's missed appointments and drafts a follow-up your front desk can review and send.
**You need:** Google Calendar connected, plus a place to mark no-shows (a sheet or a calendar note).
**The prompt:**
```
Every weekday at 8:00am Mountain, look at yesterday's appointments flagged
as no-show in my [no-show sheet]. For each one, draft a short, warm
rebooking message I can send manually. Email me the drafts. Do not send
any of them. Use a placeholder where the patient name goes.
```
**Make it quieter:** Add "only email me if there was at least one no-show yesterday."
**Watch out for:** The draft is a starting point, and a person has to read every one before it goes out. Tone matters here, a missed appointment can be a sick kid or a bad week, so keep the human in front of send, always.

## 4. Tomorrow's reminder drafts (human sends them)

**What it does:** Prepares appointment reminders for the next day so the front desk sends them in one pass instead of one at a time.
**You need:** Google Calendar connected.
**The prompt:**
```
Every weekday at 4:00pm Mountain, read tomorrow's appointments from my
calendar. For each one, draft a reminder message with the date, time, and
appointment type, leaving a [patient name] placeholder. Email me the full
set as a numbered list. Do not send anything to patients.
```
**Make it quieter:** It's already daily prep. Add "skip if tomorrow has no appointments."
**Watch out for:** This is the recipe where people get tempted to wire up auto-send. Do not. Run it under a persona scoped to read and draft only, with no ability to send SMS or email to anyone but you. The plugin-in-automation guide shows how to box it in.

## 5. New-review watcher

**What it does:** Tells you when a new patient review lands so you can respond while it's fresh.
**You need:** Nothing connected; Zo reads public pages.
**The prompt:**
```
Every weekday at 9:00am Mountain, check my Google Business profile page
and my Yelp page for new reviews since yesterday. Email me only the new
ones with the rating and text. If nothing's new, send one line saying so.
Draft a reply suggestion for any review under 4 stars, but do not post it.
```
**Make it quieter:** Already change-gated. Leave it.
**Watch out for:** Review platforms sometimes block automated reads or hide the newest reviews behind a load-more button. If a source keeps failing, tell Zo to flag it rather than quietly returning nothing. And a reply to a review can imply someone is a patient, so keep replies generic and human-approved.

## 6. The gap alert for same-day openings

**What it does:** Flags open chair time early enough that someone can fill it from the recall or short-call list.
**You need:** Google Calendar connected.
**The prompt:**
```
Every weekday at 8:15am Mountain, look at today's schedule. If there's an
open block of 45 minutes or more between now and close, text me the times.
If the day is full, stay silent.
```
**Make it quieter:** This is already the conditional version. It only pings on a real gap.
**Watch out for:** It works off the calendar, so a slot that's booked in your PM software but not synced will show as open. Same sync caveat as recipe 1. Treat the alert as a prompt to check, not gospel.

## 7. Insurance claim follow-up list

**What it does:** Surfaces claims that have gone quiet so billing can chase them before they age out.
**You need:** Google Sheets connected (a claims tracking sheet).
**The prompt:**
```
Every Tuesday at 9:00am Mountain, read my claims sheet. Pull claims that
are submitted, unpaid, and more than 21 days old with no status update.
Email me the list by claim number, payer, amount, and days outstanding,
oldest first. Do not contact any payer.
```
**Make it quieter:** It's weekly and list-only. Leave it.
**Watch out for:** Twenty-one days is a placeholder. Some payers run 30 to 45 days clean, so set the threshold to your real aging window or you'll chase claims that aren't actually late.

## 8. Supply reorder reminder

**What it does:** Reminds you to reorder consumables before you run out mid-procedure.
**You need:** Google Sheets connected (a simple par-level sheet), or just your notes file.
**The prompt:**
```
Every Thursday at 2:00pm Mountain, read my supply par sheet. List any item
where the on-hand count I logged is at or below its reorder point. Email me
the reorder list with item, current count, and supplier. If everything's
above par, say so in one line.
```
**Make it quieter:** Add "only email me if at least one item is at or below reorder point."
**Watch out for:** This is only as good as the counts you log. If nobody updates on-hand numbers, it reminds you about nothing. Pair it with whoever does your end-of-week count, or it drifts useless.

## 9. End-of-day unconfirmed list

**What it does:** Catches tomorrow's appointments that haven't confirmed yet so the front desk can make calls before they leave.
**You need:** Google Calendar connected, plus wherever confirmation status lives (a sheet or calendar tag).
**The prompt:**
```
Every weekday at 3:30pm Mountain, look at tomorrow's appointments and check
which ones are still marked unconfirmed in my [confirmation tracker]. Email
me that list by time and appointment type, no patient names. Do not call or
message anyone.
```
**Make it quieter:** Add "only send if there's at least one unconfirmed appointment."
**Watch out for:** Confirmation status has to live somewhere Zo can read. If your team confirms by checking a box inside PM software that never syncs out, this can't see it. Decide where confirmation gets logged before you rely on the recipe.

## 10. New-patient inquiry ping

**What it does:** Real-time alert when a new-patient request comes in through email so it doesn't sit unanswered for hours.
**You need:** Gmail connected.
**The prompt:**
```
Every 30 minutes between 8am and 5pm Mountain on weekdays, check Gmail for
new email that looks like a new-patient inquiry or appointment request from
someone not already in a thread with us. Text me only if one arrived, with
the sender and subject. Draft a reply for me to review, but do not send it.
```
**Make it quieter:** This is the conditional. It stays silent unless a real inquiry comes in.
**Watch out for:** Every run spends credits, and 30 minutes across a workday is plenty. Don't set it to every 5 minutes around the clock. Also, "looks like a new-patient inquiry" is fuzzy, so expect a few misreads the first week and refine the wording.

## 11. The weekly front-office recap

**What it does:** A short Friday picture of the week, what got booked, what's still overdue, what's hanging.
**You need:** Google Calendar and Google Sheets connected.
**The prompt:**
```
Every Friday at 4:30pm Mountain, pull this week's numbers: appointments
seen, no-shows, recall patients still overdue, and claims still outstanding
past my aging window. Compare to last week where you can. Email me a short
recap with the direction each number moved. If a number isn't available,
say so instead of guessing. No patient names, just counts.
```
**Make it quieter:** You want this every week. Keep it scheduled, not conditional.
**Watch out for:** Define your week (Monday to Friday vs Sunday to Saturday) in the prompt so the comparison is honest. And don't trust a count you can't trace back to a source. If your sheets don't expose a clean "no-shows this week" number, the prompt tells Zo to flag it rather than make one up.

## Before you paste all eleven

Two rules keep this from turning into something your front desk mutes by Wednesday. First, build them one at a time. Get the morning schedule read working and trusted, then add the recall list, then the next. Eleven automations stood up in one afternoon and never tuned is eleven things you'll stop reading. Second, every recipe here that touches a patient or has any ability to send needs to run under a persona scoped to read and draft only, with no power to send SMS, send email to anyone but you, or post anywhere. This is the part you do not skip in a medical setting. The plugin-in-automation guide shows exactly how to lock a persona down so the automation can prepare work but never act on a patient by itself.

One honest line on the legal side. Zo is not a place for protected health information, and these recipes are built to keep it that way: no patient health detail in the prompts, initials or placeholders instead of names, drafts a human reviews instead of automated patient contact. If your practice has compliance requirements around where data lives and who can see it, those come first, and you fit the tooling to them, not the other way around.

Start with the morning schedule read and the new-patient inquiry ping. Those two earn the idea in a day, because one tells you what your day looks like before it starts and the other keeps a prospective patient from waiting four hours for a reply. Once your team feels that, the recall list and the unconfirmed list are the obvious next picks.

If you're starting from zero, read the automations explainer first, because the recipes that use Gmail, Stripe, or Notion need those connected first (the public-web ones don't). Then pick one, not eleven. This is the kind of guide I write every week. They live at jeffkazzee.zo.space/writing.
