---
title: "10 automations for the salesperson who hates CRMs"
id: recipes-role-sales
category: recipes
kind: recipe-pack
audience: role
order: 4
date: 2026-06-18
updated: 2026-06-18
excerpt: Follow-up reminders, lead research, pipeline nudges, and the data entry you keep avoiding. 10 sales automations that work your pipeline without a CRM tax, each with the prompt and the gotcha.
tags: [automations, recipes, sales, lead-gen, triage, email, calendar, conditional-alerts, scheduling]
related: [zo-automations-101, plugin-inside-automation, zo-plugins-integrations]
difficulty: beginner
reading_time: 9
---

The deal you lost last quarter probably didn't die because the prospect went with someone else. It died because you said "I'll circle back next week," then a louder fire ate the week, and by the time you remembered, the thread was three weeks cold and you felt weird reopening it. That is the whole job of a CRM, in theory. In practice you spend twenty minutes a day feeding fields to a tool that gives you a worse memory than a sticky note, and the follow-up still slips. The thing you actually need is a memory that watches your inbox and your calendar and pokes you when a thread goes quiet. You don't need a CRM for that. You need a handful of automations and the plugins you already have.

Each recipe below follows the same shape: what it does, what you connect, the exact prompt for Zo, the tweak that keeps it from becoming noise, and the failure mode nobody warns you about. Connect the plugins first (the integrations guide covers that), then say this stuff to Zo in plain English. Change the times, names, and thresholds. None of it is sacred.

> A CRM remembers everything and reminds you of nothing. Build automations that do the opposite, because the only field that matters is "who am I about to lose by going silent."

## 1. The gone-quiet thread catcher

**What it does:** Finds prospect threads where you sent the last message and nobody replied, so the deal doesn't rot in silence.
**You need:** Gmail connected.
**The prompt:**
```
Every weekday at 8:30am Mountain, scan my Gmail for threads with a prospect
where my message was the last one and there's been no reply for 4 or more
days. Email me the list with the person, the company if you can tell, and
how many days it's been quiet. Skip newsletters, receipts, and automated mail.
```
**Make it quieter:** Add "only send the email if there's at least one quiet thread."
**Watch out for:** It can't tell a "waiting on them" silence from a "deal is dead" silence. It surfaces; you decide. Expect a couple of false alarms the first week and tighten the 4-day window if your cycle runs faster.

## 2. Pre-meeting lead research, on your calendar's clock

**What it does:** Before a sales call, a short brief on who you're meeting and where the thread left off, so you stop skimming email in the parking lot.
**You need:** Google Calendar and Gmail connected.
**The prompt:**
```
Every weekday at 7:30am Mountain, look at today's calendar for meetings with
someone outside [your company domain]. For each one, find the most recent
email thread with that person, summarize where we left off in two lines, and
pull anything they asked for that I haven't sent. Email me the set, soonest
meeting first.
```
**Make it quieter:** Add "skip the email if I have no external meetings today."
**Watch out for:** It only sees what's in your connected inbox. If half your context lives in text messages or a notes app it can't read, the brief will look thinner than reality. Tell it where the real history lives or paste it in.

## 3. Who do I owe a reply

**What it does:** A daily short list of the prospect emails that landed and need a human answer from you.
**You need:** Gmail connected.
**The prompt:**
```
Every weekday at 4:30pm Mountain, find emails I got today from prospects or
customers that look like they're waiting on a reply from me and that I
haven't answered. Email me the list with sender, company, and a one-line gist
of what they want. Skip anything automated or internal.
```
**Make it quieter:** Add "only send if there are 1 or more open replies."
**Watch out for:** "Looks like it needs a reply" is a judgment call, and Zo will occasionally flag a thank-you note or miss a buried ask. Read the list, don't trust it blindly, and refine the wording after a few days.

## 4. New inbound, before it goes cold

**What it does:** A fast ping when a fresh lead hits your inbox, because the first vendor to reply wins more than people admit.
**You need:** Gmail connected.
**The prompt:**
```
Every 30 minutes between 8am and 6pm Mountain on weekdays, check Gmail for
new email that looks like an inbound sales lead: someone asking about pricing,
a demo, availability, or a quote, from a sender I haven't talked to before.
Text me only if one arrived, with the sender, company, and what they asked.
```
**Make it quieter:** This is already the quiet kind. It stays silent until a real inbound shows up. Narrow the window if your leads only come in during business hours.
**Watch out for:** Every run costs credits even when nothing arrives. A 30-minute cadence across a 10-hour window is reasonable. Every 5 minutes around the clock is how you light money on fire for no extra speed.

## 5. The pipeline review with no pipeline software

**What it does:** A weekly read of your deals straight from the notes file you actually keep, ranked by what needs attention.
**You need:** Nothing extra if your deals live in a workspace file; connect Notion if that's where you track them.
**The prompt:**
```
Every Friday at 3:00pm Mountain, read my deals file at [path or Notion page].
Email me a pipeline review: deals likely to close in the next 14 days, deals
that haven't moved in 2 weeks, and any deal missing a clear next step. Flag
the ones where I'm the bottleneck.
```
**Make it quieter:** Keep this one on a schedule every week. It's a review, not an alert, so you want it whether or not something changed.
**Watch out for:** The output is only as honest as the file. If you've been lazy about logging next steps, the review will tell you so, which is uncomfortable and also exactly the point. Garbage notes, garbage review.

## 6. The post-meeting follow-up draft

**What it does:** Drafts the recap email after a call so the follow-up goes out same-day instead of "tomorrow," which means never.
**You need:** Google Calendar and Gmail connected.
**The prompt:**
```
Every weekday at 5:00pm Mountain, look at today's calendar for sales meetings
that already happened. For each one, draft a short follow-up email to that
person: thank them, recap what we agreed, and state the next step with a date.
Save them as Gmail drafts and email me the list so I can edit and send.
```
**Make it quieter:** Add "only draft for external meetings, and skip days with none."
**Watch out for:** It drafts, it never sends. Keep it that way. It also can't know what was actually said on the call, so it writes a sensible default recap that you correct, not a transcript. Treat the draft as a head start, not a finished email.

## 7. The stale-deal nudge

**What it does:** Surfaces deals that have stalled past the point where silence usually means trouble.
**You need:** Gmail connected, plus your deals file if you keep one.
**The prompt:**
```
Every Monday at 9:00am Mountain, find prospects I was actively talking to who
have gone quiet for 10 or more days, cross-checking my recent email and my
deals file at [path]. Email me each one with the last thing that happened and
a suggested re-open angle. If there are none, say so in one line.
```
**Make it quieter:** It's weekly and already gated on the 10-day gap. Tune the threshold to your sales cycle and leave it.
**Watch out for:** The "re-open angle" is a suggestion, not a script. A generic "just checking in" is worse than nothing. Use Zo's draft as raw material and rewrite it so it sounds like you actually remember the person.

## 8. Contact enrichment from the open web

**What it does:** Fills in the blanks on a lead from public pages, so you walk into the call knowing the role and the company instead of staring at a bare email address.
**You need:** Nothing connected; Zo reads public pages.
**The prompt:**
```
When I give you a name and company, search public pages and tell me: their
likely role, the company's size and what they sell, recent news about the
company, and anything that gives me a real reason to reach out. Pull only
from public sources and tell me which fact came from where.
```
**Make it quieter:** Run this on demand instead of on a schedule. You want it the moment a lead comes in, not on a timer.
**Watch out for:** Public data goes stale and people share names. Zo can grab the wrong [client name] or an old title. Make it cite sources so you can sanity-check before you use a "I saw you just raised a round" opener on someone who didn't.

## 9. The end-of-week activity recap

**What it does:** A Friday summary of what you actually did this week, sent, met, and moved, so your Monday self isn't starting cold.
**You need:** Gmail and Google Calendar connected.
**The prompt:**
```
Every Friday at 4:30pm Mountain, summarize my sales week: how many prospect
emails I sent, how many meetings I had and with whom, and which deals moved
forward based on my email. Email me a short recap and three things that need
attention Monday.
```
**Make it quieter:** Keep it weekly. This is your own status report, so you want it every Friday regardless.
**Watch out for:** "Deals moved forward" is inferred from your inbox, so it'll miss progress that happened on a phone call or in person. Read the "needs attention Monday" list as the useful part and the counts as rough, not gospel.

## 10. The no-show follow-up draft

**What it does:** Catches the meetings where the prospect ghosted and drafts the graceful reschedule before you take it personally.
**You need:** Google Calendar and Gmail connected.
**The prompt:**
```
Every weekday at 5:30pm Mountain, look at today's calendar for external
meetings where I see no sign in my email that the person showed or rescheduled.
For each, draft a short, no-guilt reschedule email offering two new times.
Save as Gmail drafts and email me the list.
```
**Make it quieter:** Add "skip days with no missed external meetings."
**Watch out for:** Zo is guessing at the no-show from calendar and inbox signals, so it'll sometimes flag a meeting that actually happened. Glance at the draft list before you trust it, and never let it auto-send a "you missed our call" email to someone who didn't.

## Before you paste all ten

Two rules keep this from becoming ten notifications you mute by Wednesday. First, build them one at a time. Get the gone-quiet catcher working and tuned, live with it for a few days, then add the next. Ten automations installed in one sitting and never adjusted is ten things you'll ignore. Second, the recipes that touch your inbox and write drafts deserve a scoped persona that can read and draft but cannot send, post, or charge on its own. Sales tools that auto-send are how a half-baked "just checking in" goes out to your biggest account at 5:01pm with a typo in their name. The plugin-in-automation guide shows exactly how to box that in.

Start with the gone-quiet catcher and the post-meeting follow-up draft. The first one stops deals from dying of neglect. The second one makes you the rep who always follows up same-day, which closes more than any clever pitch. Once those two are earning their keep, the rest are easy to add.

If you're starting from zero, read the automations explainer first, because the recipes that use Gmail, Stripe, or Notion need those connected first (the public-web ones don't). Then pick one. Not ten. This is the kind of guide I write every week. They live at jeffkazzee.zo.space/writing.
