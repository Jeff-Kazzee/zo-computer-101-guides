---
title: "The freelance photographer's Zo kit: 10 automations from inquiry to delivery"
id: recipes-industry-photographer
category: recipes
kind: recipe-pack
audience: industry
order: 4
date: 2026-06-18
updated: 2026-06-18
excerpt: Inquiry replies, booking prep, shot-list drafts, and the delivery follow-up you forget after the shoot. 10 photography-business automations, each copy-paste ready with the gotcha.
tags: [automations, recipes, photographer, freelance, email, calendar, scheduling, conditional-alerts]
related: [zo-automations-101, plugin-inside-automation, zo-plugins-integrations]
difficulty: beginner
reading_time: 9
---

A wedding inquiry comes in Tuesday at 11pm. You see it Thursday afternoon, after they already booked the photographer who answered in an hour. That gap is where freelance photographers bleed money, and it has nothing to do with your work. It's the admin layer: the reply you meant to send, the contract you forgot to chase, the gallery follow-up that never went out because you were already shooting the next thing. Most of that layer is "watch something on a schedule and only bother me when it matters," which is exactly what Zo is good at. Here are 10 you can paste in today.

Each one follows the same shape: what it does, what you need connected, the exact prompt, the tweak that keeps it quiet, and the failure to watch for. Connect your plugins first (the integrations guide walks through it), then talk to Zo in plain English. Every prompt is a starting point. Change the times, names, and thresholds so they fit how you actually work.

> The speed of your first reply decides more bookings than the quality of your portfolio. Automate the reply so the work can speak for itself.

## 1. The fast inquiry reply, drafted while you sleep

**What it does:** Turns a new inquiry into a ready-to-send reply draft so you answer in minutes, not days.
**You need:** Gmail connected.
**The prompt:**
```
Every 2 hours between 7am and 9pm Mountain, check Gmail for new messages
that look like a photography inquiry (asking about availability, pricing,
or booking a date). For each one, draft a warm reply in my voice that
thanks them, asks for their date, location, and shoot type, and points to
my booking page at [your booking URL]. Save it as a draft. Text me that
a draft is ready with the sender's name. Never send it.
```
**Make it quieter:** Add "only text me if you actually drafted something; stay silent otherwise."
**Watch out for:** Zo's read of "this is an inquiry" is a guess. A vendor pitch and a real lead can look identical in a subject line. Check the draft before you hit send, every time, especially the first two weeks.

## 2. Booking-prep brief the morning of a shoot

**What it does:** A short brief on each shoot before you load the car, pulled from the thread with that client.
**You need:** Google Calendar and Gmail connected.
**The prompt:**
```
Every day at 6:30am Mountain, look at my Google Calendar for shoots
scheduled today. For each one, find the most recent email thread with that
client and summarize the key details in four lines: location, start time,
shoot type, and anything they specifically asked for. Email me the set.
```
**Make it quieter:** Add "skip the email entirely on days with no shoot on the calendar."
**Watch out for:** It only sees what's in the connected inbox. If half your details live in DMs or a phone call, that context never shows up, so put the important stuff in writing.

## 3. Shot-list draft from the brief

**What it does:** Drafts a starting shot list from the shoot details so you walk in with a plan.
**You need:** Google Calendar and Gmail connected (plus Notion or a file if you want it saved).
**The prompt:**
```
Every day at 7:00am Mountain, for each shoot on today's calendar, read the
client thread and draft a shot list grouped into must-have, nice-to-have,
and detail shots. Base it on the shoot type and anything the client
requested. Save it to my [Notion shot-list page or file] and email me the
list. This is a draft for me to edit, not a final.
```
**Make it quieter:** Run it only on shoot days, same calendar gate as the brief above.
**Watch out for:** A generated shot list is a scaffold, not your eye. It will miss the one moment the client cares about most unless they spelled it out. Treat it as the boring 80 percent so you can focus on the rest.

## 4. The contract and deposit chaser

**What it does:** Flags booked clients who still haven't signed or paid, so the date doesn't sit unconfirmed.
**You need:** Gmail connected (and Stripe if you take deposits there).
**The prompt:**
```
Every Monday and Thursday at 9:00am Mountain, check for clients I've agreed
to shoot whose contract is unsigned or deposit is unpaid more than 3 days
after I sent it. Cross-reference my sent Gmail and, if connected, Stripe.
Email me the list with client, date, and what's missing. Draft a polite
nudge for each one and save it as a draft. Do not send anything.
```
**Make it quieter:** Add "only email me if at least one client is missing a contract or deposit."
**Watch out for:** Zo can't see a contract signed in a third-party tool it isn't connected to. If you use a separate signing service, it may flag someone who already signed. Confirm before you nudge a paying client.

## 5. The gallery-delivery follow-up

**What it does:** Catches shoots that wrapped but whose gallery never went out, the thing you forget the second the next booking lands.
**You need:** Google Calendar and Gmail connected.
**The prompt:**
```
Every weekday at 4:00pm Mountain, look at shoots on my calendar from the
last 14 days. For each one, check my sent Gmail for whether I've already
sent that client their gallery or a delivery update. Email me the shoots
that look undelivered, oldest first, with client name and shoot date.
```
**Make it quieter:** Add "only send the email if there's at least one undelivered shoot."
**Watch out for:** "Delivered" is detected from your sent mail. If you deliver through a gallery platform that emails the client directly, Zo won't see it and will flag a finished job. Tell it which platform you use, or forward yourself the delivery confirmation.

## 6. The review request, drafted after delivery

**What it does:** Drafts a review or testimonial ask a few days after you deliver, while the client still loves the photos.
**You need:** Gmail connected.
**The prompt:**
```
Every weekday at 10:00am Mountain, find clients I delivered a gallery to
3 to 5 days ago based on my sent Gmail. Draft a short, warm message asking
for a review at [your review link] and permission to share a few images.
Save each as a draft and text me the names. Never send them automatically.
```
**Make it quieter:** Add "only text me if you drafted at least one request."
**Watch out for:** Timing is the whole game here. Three days reads as enthusiasm, three weeks reads as an afterthought. And the draft is generic until you add the one specific thing you both loved about the shoot. Spend 20 seconds personalizing each one.

## 7. The weekly pipeline, bookings and leads in one view

**What it does:** Your whole funnel in a short Friday read: confirmed shoots, pending bookings, and leads that went cold.
**You need:** Google Calendar and Gmail connected.
**The prompt:**
```
Every Friday at 3:00pm Mountain, build me a pipeline summary: shoots
confirmed on my calendar for the next 30 days, inquiries from the last 2
weeks I haven't replied to, and leads I replied to but who went quiet for
more than 5 days. Email me three short lists under those headings.
```
**Make it quieter:** Keep this one weekly and unconditional. It's a planning read, so you want it even on a slow week.
**Watch out for:** "Went quiet" depends on Zo reading your sent mail accurately. Define your follow-up window in the prompt or it'll use its own judgment, and the cold-lead list is only as good as that threshold.

## 8. The seasonal promo idea generator

**What it does:** Feeds you a few promo angles ahead of each season so your slow months have a plan.
**You need:** Nothing connected; Zo reads public pages and works from the prompt.
**The prompt:**
```
On the 1st of each month at 9:00am Mountain, give me 3 promo ideas for the
season coming up in [your region], aimed at [your main client type, e.g.
families, couples, small businesses]. For each idea, suggest the offer, who
it targets, and one line of copy I could post. Keep it practical and local.
```
**Make it quieter:** Monthly is already light. Tighten it to "skip months I tell you are fully booked" once you know your calendar.
**Watch out for:** Ideas are cheap and these will sometimes be generic. Treat the list as a prompt for your own thinking, throw out two, and run the one that fits your actual market.

## 9. The gear rental return reminder

**What it does:** Reminds you to return rented gear before the late fee, because you've eaten one of those before.
**You need:** Google Calendar connected (or Google Tasks).
**The prompt:**
```
Every day at 8:00am Mountain, check my calendar and tasks for any gear
rental marked with a return date. If something is due to be returned today
or tomorrow, text me what it is and when it's due. Stay silent if nothing
is due.
```
**Make it quieter:** It's already conditional. Leave it alone.
**Watch out for:** This only works if you actually log the rental with a return date the day you pick it up. The automation can't remind you about a rental it never saw. Make logging it part of the pickup, not an afterthought.

## 10. The end-of-month income recap

**What it does:** A clean monthly number from your own records, so you stop guessing how the month went.
**You need:** A spreadsheet or file where you log payments (Google Sheets, or a file in your workspace). Stripe too, if you use it.
**The prompt:**
```
On the last day of each month at 6:00pm Mountain, read my income file at
[path to your income sheet] and total this month's payments by shoot type.
Compare to last month and email me a short recap: total, the busiest shoot
type, and the direction the number moved. If a row is missing an amount,
flag it instead of guessing.
```
**Make it quieter:** You want this every month, so keep it scheduled, not conditional.
**Watch out for:** The recap is only as honest as your file. If you forgot to log three cash sessions, the total is wrong and Zo has no way to know. And tell it to flag blank amounts rather than treat them as zero, or a missing number quietly drags your total down.

## Before you paste all 10

Two rules keep this from becoming noise you mute by next Friday. First, build them one at a time. Get the inquiry reply right, run it for a week, then add the next. Ten automations installed in one afternoon and never tuned is ten things you'll ignore. Second, every recipe here that drafts a message to a client is set to draft only on purpose, and that's worth enforcing at the persona level. Run the risky ones under a scoped persona that can read your inbox and draft replies but cannot send, post, or charge on its own. The plugin-in-automation guide shows exactly how to box that in, and for client-facing work it's not optional.

Start with the fast inquiry reply and the gallery-delivery follow-up. One wins you bookings by closing the response-time gap, the other saves the relationships you've already earned. Run those two for a week, then add the rest one at a time.

If you're starting from zero, read the automations explainer first, because the recipes that use Gmail, Stripe, or Notion need those connected first (the public-web ones don't). Then pick one, not ten. This is the kind of guide I write every week. They live at jeffkazzee.zo.space/writing.
