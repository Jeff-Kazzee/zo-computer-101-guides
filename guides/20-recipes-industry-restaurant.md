---
title: "The restaurant owner's Zo playbook: 10 automations that save a shift"
id: recipes-industry-restaurant
category: recipes
kind: recipe-pack
audience: industry
order: 2
date: 2026-06-18
updated: 2026-06-18
excerpt: Reservations, reviews, inventory nudges, and staffing reminders. 10 restaurant automations that handle the admin so you can run the floor, each copy-paste ready.
tags: [automations, recipes, restaurant, reporting, email, scheduling, conditional-alerts]
related: [zo-automations-101, plugin-inside-automation, zo-plugins-integrations]
difficulty: beginner
reading_time: 9
---

You found out about the one-star review four days late, from a regular who mentioned it at the bar. By then it was the top result for your name. That is the restaurant admin problem in one sentence: the stuff that actually moves the needle happens while you are on the line at 7pm with a sauté pan in each hand, and nobody is watching the back office because the back office is you. Reservations, reviews, the POS numbers you keep meaning to read, the linen order you forgot until you ran out. All of it is "check something on a schedule and only interrupt me when it matters," which is the exact job an automation does without complaining.

Each recipe below uses the same shape: what it does, what you connect, the prompt to paste into Zo, the tweak that keeps it quiet, and the failure to watch for. Connect your plugins first (the integrations guide walks through it), then talk to Zo in plain English. Change every time, name, and threshold to match your room. These are starting points, not gospel.

> A reminder that fires every single day gets muted by next Tuesday. A reminder that fires only when the walk-in is low or a review went sideways gets trusted all year. Build the second kind.

## 1. The reservations summary before the doors open

**What it does:** One message each afternoon with tonight's covers, big parties, and anything flagged.
**You need:** Google Calendar connected (or your reservation file).
**The prompt:**
```
Every day at 2:00pm Mountain, read my Google Calendar for tonight's
reservations. Email me a summary: total covers, the times they land,
any party of 6 or more, and any note like allergy, birthday, or VIP.
Keep it under 150 words.
```
**Make it quieter:** Add "if there are no parties of 6 or more and no flagged notes, just give me the cover count in one line."
**Watch out for:** Zo only sees the reservations that live in the connected calendar or file. Walk-ins and phone bookings written on a paper sheet will not show up unless they make it into the system.

## 2. New-review watcher that catches the one-star fast

**What it does:** Checks your public review pages and pings you when a new one lands, loud if it is negative.
**You need:** Nothing connected; Zo reads public pages.
**The prompt:**
```
Every day at 11:00am Mountain, check [your Google Maps reviews URL] and
[your Yelp page URL] for reviews posted since yesterday. Text me any new
ones with the star rating and a one-line quote. If a review is 3 stars
or lower, put ALERT at the front so I see it first.
```
**Make it quieter:** Add "if there are no new reviews, send nothing."
**Watch out for:** Yelp in particular throttles automated reads, so some days it may come back empty when there is actually something there. Tell Zo to note when a page failed to load instead of pretending zero, and spot-check the pages yourself once a week.

## 3. Daily sales recap from your POS export

**What it does:** Reads last night's numbers from a file so you stop squinting at the register report on your phone.
**You need:** A POS export file Zo can read (CSV or your sales sheet).
**The prompt:**
```
Every day at 9:00am Mountain, read my POS export at [file path or sheet].
Email me yesterday's totals: net sales, cover count, average check, and
top 3 selling items. Compare net sales to the same weekday last week and
tell me up or down by how much.
```
**Make it quieter:** This one you want daily. Keep it on a schedule.
**Watch out for:** The recap is only as fresh as the export. If you forget to drop last night's file, Zo reads stale data and reports it confidently. Build the export into your closing checklist so the file is always there by morning.

## 4. Low-inventory reminder from your prep sheet

**What it does:** Watches a tracked inventory sheet and nudges you before you 86 something mid-service.
**You need:** Google Sheets connected (or your inventory file).
**The prompt:**
```
Every day at 10:00am Mountain, read my inventory sheet at [sheet name].
Text me any item where the on-hand count is at or below its par level,
with the item name and how far under par it is. List nothing if everything
is above par.
```
**Make it quieter:** It is already gated to only fire when something is low. Leave it.
**Watch out for:** Garbage in, garbage out. If the line never updates the count column after a busy Friday, the sheet says you are fully stocked while the walk-in is empty. The automation cannot fix a counting habit that does not exist.

## 5. Staff schedule gap alert

**What it does:** Looks at tomorrow's shifts and flags holes before you are standing in an understaffed dining room.
**You need:** Google Sheets or Google Calendar connected (wherever your schedule lives).
**The prompt:**
```
Every day at 4:00pm Mountain, read tomorrow's staff schedule at [schedule
location]. Email me each shift with who is on it, and call out any shift
that has nobody assigned or fewer people than the minimum I set: [e.g. 2
servers, 1 line cook, 1 dish]. If every shift is covered, say "all covered"
in one line.
```
**Make it quieter:** Add "only email me if a shift is short or unassigned."
**Watch out for:** Zo reads the schedule as written, so a last-minute call-out at 5pm is invisible until someone edits the sheet. This catches planning gaps, not same-day emergencies.

## 6. Supplier order reminder on your real cadence

**What it does:** Reminds you to place standing orders before the cutoff, so you are not begging your produce rep at 6am.
**You need:** Nothing connected; this is a timed nudge (add a file if you want order notes).
**The prompt:**
```
Every Sunday and Wednesday at 7:00am Mountain, remind me to place my
produce and dry-goods orders before the [supplier name] cutoff at 10am.
Include my standing order notes from [file] if I have them, otherwise just
send the reminder.
```
**Make it quieter:** Tie it to your actual delivery days. Two reminders a week beats a daily one you tune out.
**Watch out for:** A reminder is not an order. Zo is poking you, not calling the supplier, unless you have explicitly set up an integration that places orders and you have decided you trust it to.

## 7. Weekly sales versus last week

**What it does:** Your real week in four lines every Monday, no spreadsheet diving.
**You need:** Your POS export file or sales sheet.
**The prompt:**
```
Every Monday at 9:00am Mountain, read my sales data at [file or sheet].
Compare last week (Monday through Sunday) to the week before. Email me
net sales, total covers, average check, and best day, with the direction
each number moved. If a field is missing from the file, say so instead
of guessing.
```
**Make it quieter:** You want this every Monday. Keep it scheduled.
**Watch out for:** Define your week the same way every time, because a Sunday-to-Saturday file compared against a Monday-to-Sunday one will lie to you. And if the export does not cleanly separate dine-in from delivery, tell Zo to flag that rather than blend the two into a number you cannot trust.

## 8. Social mention monitor

**What it does:** Tells you when someone tags or talks about the restaurant publicly, so you can repost the good and answer the bad.
**You need:** Nothing connected; Zo reads public pages and search.
**The prompt:**
```
Every day at 1:00pm Mountain, search for public mentions of [restaurant
name] and [your handle] from the last 24 hours on the open web and social.
Email me anything you find with a link and a one-line summary. Skip my own
posts. If there is nothing new, send nothing.
```
**Make it quieter:** Already silent by default. Tighten the search terms if a common phrase keeps pulling false hits.
**Watch out for:** Public search misses a lot. Private accounts, app-only posts, and platforms that block reads will not surface here, so treat this as a partial net, not full coverage.

## 9. Slow-day promo idea generator

**What it does:** On your quiet days, hands you three specific promo ideas built from your own slow numbers.
**You need:** Your POS export file or sales sheet.
**The prompt:**
```
Every Tuesday at 10:00am Mountain, look at my sales data at [file] and
find my two slowest dayparts this past week. Email me three concrete promo
ideas aimed at filling those exact slots, each with a suggested offer and
a one-line reason it fits my numbers. Keep it practical for a [your concept,
e.g. neighborhood Italian spot].
```
**Make it quieter:** Move it to every other week if weekly ideas start repeating.
**Watch out for:** Zo will cheerfully suggest a 30 percent discount that wrecks your margin. It does not know your food cost unless you tell it, so add your target margin to the prompt or read every idea with your calculator handy.

## 10. End-of-week owner brief

**What it does:** One Sunday-night read that ties the week together: sales, reviews, staffing, and what needs your attention Monday.
**You need:** Your POS file, plus Google Calendar or Sheets for the rest.
**The prompt:**
```
Every Sunday at 6:00pm Mountain, build me a one-page owner brief for the
week: net sales versus the prior week from [file], any new reviews from
[review URLs] and their average rating, any inventory items still under
par, and any uncovered shifts in next week's schedule. End with the three
things you think need my attention first.
```
**Make it quieter:** Keep this one whole and weekly. It is your sit-down with a coffee, not an alert.
**Watch out for:** This pulls from several sources at once, so if one is stale or failed to load, the brief inherits that gap quietly. Tell Zo to flag any section it could not fill rather than skipping it, so a missing review check does not read as "no bad reviews this week."

## Before you paste all ten

Two rules keep this from turning into ten notifications you swipe away. First, build them one at a time. Get the reservations summary and the review watcher working and trusted, then add the next. Ten automations stood up in one slow afternoon and never tuned is ten things you will mute by the weekend rush. Second, the ones touching anything sensitive (your sales file, your ability to send or post) are worth running under a scoped persona that can read and draft but cannot send, post, or charge on its own. The plugin-in-automation guide shows exactly how to box one in, and for a restaurant that boundary matters, because the difference between "draft a reply to this review" and "post a reply to this review" is your public voice.

Start with the review watcher and the reservations summary. The first one means you never hear about a one-star from a regular again. The second one means you walk in already knowing the room. Feel those two work, and the other eight stop looking like chores and start looking obvious.

If you are starting from zero, read the automations explainer first, because the recipes that use Gmail, Stripe, or Notion need those connected first (the public-web ones don't). Then pick one, not ten. This is the kind of guide I write every week. They live at jeffkazzee.zo.space/writing.
