---
title: "The contractor's Zo crew: 10 automations for bids, scheduling, and invoices"
id: recipes-industry-contractor
category: recipes
kind: recipe-pack
audience: industry
order: 6
date: 2026-06-18
updated: 2026-06-18
excerpt: Bid follow-up, job scheduling, material reminders, and the invoices you keep meaning to send. 10 contractor automations you can paste into Zo today, each with the gotcha.
tags: [automations, recipes, contractor, lead-gen, email, calendar, scheduling, conditional-alerts]
related: [zo-automations-101, plugin-inside-automation, zo-plugins-integrations]
difficulty: beginner
reading_time: 9
---
```

The money in a contracting business leaks through the gaps between jobs. A bid request comes in Tuesday while you're on a roof, you mean to answer it that night, and by Thursday the homeowner already hired the guy who called back first. A quote sits in someone's inbox for two weeks and you never nudge it. A job wraps on Friday and the invoice doesn't go out until you finally sit down three weekends later, if you remember. None of that is a skills problem. It's the admin layer, the part that happens at a laptop after a ten-hour day when you have nothing left, and it's exactly the layer a scheduled automation handles well. Most of it is "watch something and only bug me when it matters."

Each recipe below is the same shape: what it does, what you need connected, the exact prompt to give Zo, the tweak that keeps it from becoming noise, and the failure to watch for. Connect your plugins first, the integrations guide walks through that, then talk to Zo in plain English. Change the times, names, and thresholds to match your own setup. None of these send anything to a client on their own. They draft and they remind. You stay the one who hits send.

> A bid you answer in two hours wins jobs. A bid you answer in two days loses to whoever called back first. Most of this list exists to close that gap.

## 1. New bid request, on your phone in minutes

**What it does:** Texts you the second a lead or estimate request hits your inbox, so you can call back before the competition.
**You need:** Gmail connected.
**The prompt:**
```
Every 30 minutes between 7am and 8pm Mountain, every day, check my Gmail for
new messages that read like a job or estimate request: words like quote, bid,
estimate, project, remodel, or a contact-form submission from my website.
Text me only when one arrives, with the sender, their phone number if it's in
the message, and a one-line summary of the job. Skip supplier emails and
newsletters.
```
**Make it quieter:** Add "ignore anything from my suppliers at [supplier domain] and [supplier domain]." Those clog the filter fast.
**Watch out for:** It can only flag what lands in the connected inbox. Calls, texts, and Facebook messages never reach it. If half your leads come by phone, this catches the other half, not all of it.

## 2. The bid that went quiet

**What it does:** Surfaces quotes you sent that nobody has answered, so a $14,000 job doesn't die from silence.
**You need:** Gmail connected.
**The prompt:**
```
Every Monday and Thursday at 7:30am Mountain, scan my sent Gmail from the last
21 days for emails where I sent a quote, estimate, or bid. For each one, check
whether the client replied. Email me the list of quotes that got no response,
oldest first, with the client, the job, and how many days it's been quiet.
```
**Make it quieter:** Add "only send the email if there's at least one unanswered quote."
**Watch out for:** A client who replied on the phone instead of by email still shows up as "quiet." Treat the list as a call list to scan, not gospel. Knock the closed ones off in your head.

## 3. Today's run, before you're in the truck

**What it does:** One message at breakfast with every job, address, and time on the calendar for the day.
**You need:** Google Calendar connected.
**The prompt:**
```
Every day at 5:45am Mountain, read my Google Calendar for today. Text me each
job in order with the start time, the address or site name, and any note I put
in the event. End with the total number of stops. Keep it short enough to read
at a stoplight.
```
**Make it quieter:** It's a daily brief you actually want, so keep it on a schedule. If you'd rather skip empty days, add "don't text me if the calendar has nothing on it."
**Watch out for:** It reads what's actually in the event. If you keep addresses in your head or a paper notebook, the brief is blank where it counts. Put the address in the calendar entry and this earns its keep.

## 4. Materials, the night before

**What it does:** Reminds you what to pick up or order before a job, while the supply house is still open.
**You need:** Google Calendar connected.
**The prompt:**
```
Every day at 4:00pm Mountain, look at my Google Calendar for tomorrow's jobs.
For any event where I wrote a materials note (for example "MATERIALS: 20 sheets
drywall, 6 boxes screws"), text me that list so I can order or grab it today.
If there are no materials notes for tomorrow, say nothing.
```
**Make it quieter:** It's already silent on days with no materials note. Leave it.
**Watch out for:** This only works if you write the note. Pick one format, like starting the line with "MATERIALS:", and use it every time, or Zo has nothing to read. The habit is the hard part, not the prompt.

## 5. The invoice you keep forgetting to send

**What it does:** Nudges you to bill the day a job finishes, so the gap between finishing and getting paid stops being three weeks.
**You need:** Google Calendar connected. A Google Sheet or file where you track jobs helps but isn't required.
**The prompt:**
```
Every weekday at 6:30pm Mountain, check my Google Calendar for jobs marked done
or completed today. Email me a reminder for each one: the client, the job, and
"invoice this." Draft a plain invoice email I can edit and send myself for each.
Do not send anything to the client.
```
**Make it quieter:** Add "only email me if at least one job finished today."
**Watch out for:** It drafts the invoice email for you, it never sends it. Keep it that way. An auto-sent invoice with the wrong final number is a worse phone call than a late one. You read it, fix the total, then send.

## 6. Who hasn't paid

**What it does:** A short list of overdue invoices every week so you can chase the money on purpose instead of when you happen to remember.
**You need:** Stripe connected if you invoice through Stripe. Otherwise a Google Sheet where you log invoices and due dates.
**The prompt:**
```
Every Monday at 8:00am Mountain, check Stripe for invoices that are unpaid and
more than 10 days past the due date. Email me the list with client, amount, and
days overdue, largest amount first. If everyone's current, say so in one line.
```
**Make it quieter:** Already weekly and conditional. Bump the threshold to 14 days if 10 feels too twitchy for your trade.
**Watch out for:** This builds your follow-up list. It does not message a single client unless you explicitly tell it to later, and on overdue money you want to make those calls yourself anyway. Read the room before you dun a repeat customer.

## 7. Weather watch for the outdoor jobs

**What it does:** Checks the forecast for your job sites and warns you the day before if the weather is going to kill a pour, a roof, or a paint day.
**You need:** Nothing connected; Zo reads public pages. Google Calendar helps if your jobs have locations.
**The prompt:**
```
Every day at 3:30pm Mountain, look at tomorrow's outdoor jobs on my calendar
(concrete, roofing, painting, excavation). Check the public forecast for
[your city] for tomorrow. Text me only if rain is over 40 percent, the high is
below 40F, or sustained wind is over 20 mph, with the specific number and which
job it affects. If the forecast is fine, stay silent.
```
**Make it quieter:** Already change-gated to bad weather only. Tune the thresholds to your work. Concrete cares about cold; roofing cares about wind.
**Watch out for:** A public forecast is a forecast. It's wrong sometimes, especially in mountain country where the valley and the ridge get different weather. Use it as a heads-up to make the call, not as the decision.

## 8. The client update you should be sending

**What it does:** Drafts a short progress update to a client mid-project so they stop wondering whether you vanished.
**You need:** Gmail connected.
**The prompt:**
```
Every Friday at 2:00pm Mountain, for my active job at [client name], draft a
short, plain progress-update email: what got done this week, what's next week,
and anything I'm waiting on them for. Pull what you can from this week's emails
about the job. Email the draft to me. Do not send it to the client.
```
**Make it quieter:** Run it only on the weeks a project is actually open. Pause the automation between jobs instead of letting it draft about nothing.
**Watch out for:** Zo only knows what's in your inbox about the job. It can't see the framing you finished on Wednesday unless something in your email mentions it. Treat the draft as a starting skeleton, add the real site detail, then send.

## 9. Permits and inspections that can't slip

**What it does:** Tracks permit expirations and inspection deadlines and warns you before one lapses and stops the job cold.
**You need:** A Google Sheet or file listing permits and inspections with dates. Google Calendar works too if you put the dates there.
**The prompt:**
```
Every Monday at 7:00am Mountain, read my permits-and-inspections sheet. Email me
anything where a permit expires, an inspection is due, or a deadline lands in the
next 14 days, sorted by date, with the job, the item, and the exact date. If
nothing's due in that window, say so in one line.
```
**Make it quieter:** Already weekly and conditional. Tighten the window to 7 days if 14 buries you in too-early warnings.
**Watch out for:** It reads the dates you logged. A permit you never entered is a permit it can't warn you about. The automation is only as honest as the sheet, so the five minutes of data entry per job is the actual work here.

## 10. The Friday recap, jobs and money in one place

**What it does:** A short end-of-week picture: what got done, what's still open, and what came in, without opening a single dashboard.
**You need:** Google Calendar connected. Stripe connected if you want the money line.
**The prompt:**
```
Every Friday at 5:00pm Mountain, summarize my week in three short sections.
Jobs: what the calendar shows completed this week and what's still scheduled
into next week. Money: payments received this week from Stripe and the total.
Open loops: any unanswered quotes or unsent invoices you can see. Email it to me.
If Stripe doesn't expose a number cleanly, flag it instead of guessing.
```
**Make it quieter:** Keep this one weekly. It's the Friday gut-check, not an alert, and you want it whether the week was good or bad.
**Watch out for:** Define your week in the prompt if Monday-to-Sunday matters to you, otherwise the totals can straddle two weeks and lie to you. And a number you can't trace back to a real payment isn't a number, it's a guess. The prompt tells Zo to flag the gap rather than fill it.

## Before you paste all ten

Two rules keep this from turning into ten things you mute by next Friday.

First, build them one at a time. Get the bid-request ping working and trust it for a week before you add the quote-follow-up, then the schedule brief, and so on. Ten automations installed in one rainy afternoon and never tuned is ten alerts you'll swipe away without reading. One that works earns the next one.

Second, the recipes that touch real access, your sent mail, your Stripe, your ability to email a client, are worth running under a scoped persona that can read and draft but cannot send, post, or charge on its own. That's how you get the convenience of the invoice draft and the client update without the nightmare of a wrong number going out under your name while you're up a ladder. The plugin-in-automation guide shows exactly how to box a persona in like that.

Start with the new-bid ping and the gone-quiet quote list. Those two are where the money actually leaks, and once you feel a $9,000 bid come back from the dead because Zo reminded you to call, the rest of the list sells itself.

If you're starting from zero, read the automations explainer first, because the recipes that use Gmail, Stripe, or Notion need those connected first (the public-web ones don't). Then pick one. Not ten. This is the kind of guide I write every week. They live at jeffkazzee.zo.space/writing.
