---
title: "12 automations a realtor can run in Zo this week"
id: recipes-industry-realtor
category: recipes
kind: recipe-pack
audience: industry
order: 1
date: 2026-06-18
updated: 2026-06-18
excerpt: New-listing alerts, lead follow-up, showing prep, and the paperwork chase between. 12 real-estate automations you can paste into Zo today, each with the plugins it needs and the gotcha.
tags: [automations, recipes, realtor, lead-gen, email, calendar, scheduling, conditional-alerts]
related: [zo-automations-101, plugin-inside-automation, zo-plugins-integrations]
difficulty: beginner
reading_time: 9
---

The deal dies in the gaps. A lead fills out a form at 9:40pm and hears back two days later, by which point they booked a showing with someone faster. A buyer mentions they loved a house, you mean to follow up Thursday, Thursday turns into next week. An inspection contingency expires while the file sits in a tab you forgot was open. None of that is a skill problem. It is a "you are one person doing the work of an office" problem, and it is exactly the layer a scheduled automation handles without complaint. Here are 12 you can paste into Zo this week.

Each one uses the same shape: what it does, what you need connected, the exact prompt, the tweak that keeps it from becoming noise, and the failure to watch for. Connect your plugins first (the integrations guide walks through it), then talk to Zo in plain English. Treat every prompt as a starting point. Swap in your real times, names, zip codes, and thresholds.

> A drafted follow-up that you approve in ten seconds beats a perfect one you never sent. Build the automation that hands you the draft, then keep your thumb on the send button.

## 1. New-listing alert for your saved area

**What it does:** Tells you when the public listing page for a market you watch shows something new, so you're not the last to know.
**You need:** Nothing connected; Zo reads public pages.
**The prompt:**
```
Every weekday at 7:30am Mountain, check [public listing search URL for your
area and price band]. Compare to what you saw yesterday and email me only
the new listings, with address, price, beds/baths, and the link. If nothing
new posted, email me one line saying so.
```
**Make it quieter:** Already change-gated. Narrow the URL to one zip and one price band so it surfaces homes you'd actually show.
**Watch out for:** Some MLS-backed portals block automated reads or hide new listings behind login. If a page keeps failing, tell Zo to flag it instead of going silent, and point it at a public-facing search you know loads.

## 2. The gone-quiet lead reminder

**What it does:** Surfaces prospects you stopped talking to so a warm lead doesn't go cold from neglect.
**You need:** Gmail connected.
**The prompt:**
```
Every Monday at 8:30am Mountain, scan my Gmail for buyer or seller leads I
exchanged email with in the last 60 days but haven't replied to or heard
from in 14 or more days. Email me the list with name, last contact date,
and a one-line note on where we left off. Skip anything that already closed.
```
**Make it quieter:** Add "only send if there are 1 or more gone-quiet leads."
**Watch out for:** Zo can only see leads who live in your connected inbox. A lead who only ever texted you won't show up here, so this is a backstop for email, not your whole pipeline.

## 3. Showing-prep brief

**What it does:** A short brief before each showing covering the property and what you already know about the client.
**You need:** Google Calendar and Gmail connected.
**The prompt:**
```
Every weekday at 7:00am Mountain, look at my calendar for today's showings.
For each one, pull the property address from the event, and search my Gmail
for the most recent thread with that client to summarize what they're looking
for and any budget or must-haves they mentioned. Email me the set, one block
per showing.
```
**Make it quieter:** Add "skip the email entirely if I have no showings today."
**Watch out for:** It writes the property line from whatever is in the calendar event. If your events just say "Showing 2pm" with no address, the brief is thin. Put the address in the event title or location field.

## 4. Post-showing follow-up draft

**What it does:** Drafts the "great seeing you today" message while the showing is still fresh, ready for you to edit and send.
**You need:** Google Calendar and Gmail connected.
**The prompt:**
```
Every weekday at 6:00pm Mountain, look at the showings on my calendar from
today. For each client, draft a short, warm follow-up email referencing the
specific property we saw and asking one real question about their reaction.
Save them as Gmail drafts and email me a heads-up listing what you drafted.
Do not send anything.
```
**Make it quieter:** Add "only ping me if you drafted at least one."
**Watch out for:** This drafts, it never sends. Keep it that way. A follow-up that goes out before you've read it is how you email the wrong client's name to the right person.

## 5. The weekly pipeline review

**What it does:** Your active deals and their stage in one read every Sunday night, no CRM spelunking.
**You need:** Notion or Google Sheets connected (wherever you track deals).
**The prompt:**
```
Every Sunday at 6:30pm Mountain, read my deal tracker in [Notion / Google
Sheets]. Group everything by stage: new lead, showing, offer out, under
contract, closing this month. Email me the count in each stage and flag any
deal that hasn't moved in 10 or more days. If a deal is missing a next step,
say so.
```
**Make it quieter:** Keep it weekly. This is your Monday-morning map, not an alert.
**Watch out for:** The review is only as honest as your tracker. If you forget to log a stage change, Zo reports the stale version. Define your stages in the prompt so it doesn't invent its own.

## 6. Open-house follow-up drafts

**What it does:** Turns a sign-in sheet into a stack of personalized follow-up drafts the morning after.
**You need:** Gmail connected, plus a sheet or file with your open-house sign-ins.
**The prompt:**
```
Every Monday at 9:00am Mountain, read [open-house sign-in file]. For each
attendee with an email, draft a short follow-up: thank them for coming to
[property address], mention I'm happy to send comparable listings, and ask
if they're working with an agent yet. Save as Gmail drafts and email me the
list. Send nothing.
```
**Make it quieter:** Add "skip anyone already marked as a client in the file."
**Watch out for:** Garbage in, garbage out. If sign-in handwriting got typed into the sheet wrong, the draft greets "Jhon" by name. Skim the drafts before you send, every time.

## 7. Price-change watch on your watched listings

**What it does:** Alerts you when a home your buyer is circling drops or jumps in price.
**You need:** Nothing connected; Zo reads public pages.
**The prompt:**
```
Every weekday at 8:00am Mountain, check these listing URLs: [URL], [URL],
[URL]. Compare each price to what you saw yesterday. Email me only the ones
that changed, with old price, new price, and the link. If nothing moved,
send one line saying so.
```
**Make it quieter:** Already change-gated. Add and remove URLs as buyers move on.
**Watch out for:** A listing that goes pending or off-market may stop loading. Tell Zo to note "page no longer available" rather than treat a vanished listing as no change, because that disappearance is often the news.

## 8. Contract deadline tracker

**What it does:** Watches the dates that kill deals, inspection, appraisal, financing, closing, and warns you before they pass.
**You need:** Google Sheets or Notion connected (a file with your contract dates).
**The prompt:**
```
Every weekday at 7:00am Mountain, read [contract deadlines file]. For every
active deal, check the inspection, appraisal, financing, and closing dates.
Email me anything due in the next 3 days or already past due, with the deal,
the deadline type, and the date. If nothing is due, say so in one line.
```
**Make it quieter:** It is already date-gated. Leave the 3-day window unless you want more runway, then widen it to 5.
**Watch out for:** This is a reminder, not a calendar of record. It reads the dates you logged. A contingency you never entered is a contingency it can't warn you about, so the file has to be current or the safety net has holes.

## 9. Birthday and closing-anniversary nudge

**What it does:** Reminds you to reach out to past clients on the days that keep referrals coming.
**You need:** Google Sheets or Notion connected (a client list with dates).
**The prompt:**
```
Every weekday at 7:30am Mountain, read my [client list file]. Check for any
client with a birthday today or a home-purchase anniversary today. Email me
who it is, which occasion, and the year they closed. Suggest one short, non-
salesy message I could send.
```
**Make it quieter:** Add "only email me on days someone actually has an occasion."
**Watch out for:** Zo suggests the message, you send it. A past client who gets an obviously automated "Happy anniversary!!" can smell it. Rewrite the suggestion in your own voice before it goes out.

## 10. Weekly market-stats digest for your zip

**What it does:** The numbers you quote to sellers, median price, days on market, inventory, pulled fresh every Friday.
**You need:** Nothing connected; Zo reads public pages.
**The prompt:**
```
Every Friday at 4:00pm Mountain, check [public market-stats page or
portal URL for your zip]. Pull median list price, average days on market,
and active inventory count. Compare to last week and email me a short summary
with the direction each number moved. If a figure isn't published, say so
instead of guessing.
```
**Make it quieter:** Keep it weekly. You want this whether or not it changed, because the trend is the point.
**Watch out for:** Public stat pages lag and they update on their own schedule, often monthly. Don't present a week-old "median" as this week's. Have Zo note the as-of date the source shows.

## 11. New-inbound-lead instant ping

**What it does:** A near-real-time text the moment a lead form or portal inquiry hits your inbox, so you call while they're still on the site.
**You need:** Gmail connected.
**The prompt:**
```
Every 20 minutes between 7am and 9pm Mountain, check Gmail for new lead
emails from [Zillow / your IDX form / your lead source domain]. Text me only
if one arrived, with the lead's name, the property they asked about, and
their contact info if it's in the email.
```
**Make it quieter:** This is the conditional. It stays silent unless a real inquiry lands. Tighten the sender filter to your actual lead sources so it doesn't ping on every newsletter.
**Watch out for:** Every run spends credits. A 14-hour window every 20 minutes is reasonable; don't set it to every 5 minutes around the clock or you're paying to check an empty inbox at 3am.

## 12. End-of-week activity recap

**What it does:** A Friday summary of what you actually did this week, the showings, the new leads, the deals that moved, so Monday-you isn't guessing.
**You need:** Google Calendar and Gmail connected (plus your deal tracker if you keep one).
**The prompt:**
```
Every Friday at 5:00pm Mountain, summarize my week: count the showings on my
calendar, the new leads that came into Gmail, and any deal that changed stage
in [tracker file]. Email me a six-line recap with the numbers and one note on
what's still open heading into next week.
```
**Make it quieter:** Keep it weekly. It's a mirror, not an alarm.
**Watch out for:** It counts what it can see. A showing you never put on the calendar and a lead who only texted won't make the tally, so read the recap as "what my tools caught," not gospel.

## Before you paste all twelve

Two rules keep this from turning into a wall of email you mute by Friday. First, build them one at a time. Get the new-listing alert clean, run it for three days, tune the URL and the wording, then add the next. Twelve automations stood up in one afternoon and never tuned is twelve things you'll ignore. Second, the ones that can act on your behalf, anything touching Gmail drafts or your client list, are worth running under a scoped persona that can read and draft but cannot send, post, or charge on its own. The plugin-in-automation guide shows exactly how to box them in, and in this business the difference between a drafted follow-up and an auto-sent one is the difference between looking sharp and looking like a bot to a client deciding whether to trust you with the biggest purchase of their life.

Start with the new-inbound-lead ping and the gone-quiet reminder. One catches the leads coming in, the other catches the ones slipping out, and together they pay for the whole idea in a week. Once you feel a deal get saved by a text you'd otherwise have sent two days late, the rest are easy.

If you're starting from zero, read the automations explainer first, because the recipes that use Gmail, Stripe, or Notion need those connected first (the public-web ones don't). Then pick one, not twelve. This is the kind of guide I write every week. They live at jeffkazzee.zo.space/writing.
