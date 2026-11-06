---
title: "The job hunt, automated: 9 ways Zo works your search for you"
id: recipes-everyone-job-hunt
category: recipes
kind: recipe-pack
audience: everyone
order: 2
date: 2026-06-18
updated: 2026-06-18
excerpt: New-posting alerts, tailored application drafts, follow-up reminders, and the company research you keep skipping. 9 job-search automations you can paste into Zo today, each with the failure to watch for.
tags: [automations, recipes, everyone, job-hunt, email, web-search, scheduling, conditional-alerts]
related: [zo-automations-101, plugin-inside-automation, zo-plugins-integrations]
difficulty: beginner
reading_time: 9
---

Job hunting is a part-time job you do on top of your real one, and most of it is checking. Did a new posting go up. Did that recruiter ever write back. Have I followed up on the role I applied to nine days ago, or did it quietly die. You refresh the same three job boards at 11pm, then forget which company you already applied to. The checking is the part Zo can take, because checking on a schedule and only flagging what changed is exactly what an automation is built for. Here are 9 you can paste in today.

Each one has the same shape: what it does, what you need connected, the exact prompt to give Zo, the tweak that keeps it quiet, and the failure to watch for. Connect your plugins first (the integrations guide walks through it), then talk to Zo in plain English. Every prompt is a starting point. Change the times, the search terms, and the names to fit your actual search.

> The job hunt punishes the people who go quiet. Set up the follow-up nudges before the polished resume, because the candidate who emails back on day three beats the better candidate who forgot.

## 1. New-posting watcher for your saved search

**What it does:** Checks the boards for roles matching your search and pings you only when something new shows up.
**You need:** Nothing connected; Zo reads public pages.
**The prompt:**
```
Every weekday at 8:00am Mountain, check [job board URL], [job board URL],
and [company careers page URL] for postings matching "[your role keywords]"
in [your city] or remote. Compare to what you saw yesterday and email me
only the new ones, with title, company, and link. If nothing is new, send
one line saying so.
```
**Make it quieter:** Add "skip the email entirely on days with no new postings."
**Watch out for:** Some boards block automated reads or hide jobs behind a login. If one keeps failing, tell Zo to note that board by name instead of silently dropping it, so you know to check it by hand.

## 2. Tailored application draft from a posting

**What it does:** Turns a job description into a first-pass cover letter and a tightened resume summary, drafted for you to edit.
**You need:** Gmail connected if you want it emailed, plus your resume saved as a file Zo can read.
**The prompt:**
```
When I send you a job posting URL, read it and my resume at [resume file path].
Draft a one-page cover letter that maps my actual experience to the three
things this posting cares about most, and a four-line resume summary tuned to
this role. Keep my real history honest. Flag anything the posting wants that
I don't have. Save both as drafts and email me a note that they're ready to review. Do not send anything.
```
**Make it quieter:** This one runs on demand, not on a schedule, so it only fires when you hand it a posting.
**Watch out for:** It drafts from what's in your resume. If you ask it to claim a skill you don't have, it will, and a recruiter will catch it in the first call. Read every draft before it leaves your outbox.

## 3. Company research brief before an interview

**What it does:** A short, honest brief on the company and the role so you walk in knowing more than the careers page.
**You need:** Google Calendar connected helps; otherwise run it on demand.
**The prompt:**
```
The morning of any interview on my calendar, build me a one-page brief on
[the company]: what they do in plain terms, recent news from the last 90 days,
their main competitors, and three smart questions I could ask the interviewer.
Note anything that looks like a red flag. Email it to me by 7:30am Mountain.
```
**Make it quieter:** Add "only run this on days I actually have an interview scheduled."
**Watch out for:** Recent news can be thin or wrong for small companies. Treat the brief as a head start, then verify the one or two facts you plan to mention out loud.

## 4. Follow-up reminder after you apply or interview

**What it does:** Catches the moment a follow-up is overdue and reminds you to send one.
**You need:** Notion or Google Sheets connected to track applications, or a simple file Zo can read.
**The prompt:**
```
Every weekday at 9:00am Mountain, look at my applications tracker at
[tracker location]. For any application where I applied 7+ days ago with no
reply, or any interview from 2+ days ago where I haven't sent a thank-you,
email me the list with company, role, and what's owed. One line each.
```
**Make it quieter:** Add "only email me if at least one follow-up is actually due."
**Watch out for:** This only works if you log applications somewhere Zo can see. If your tracker is a pile of browser tabs, build the habit of dropping each application into one file first, or this stays empty.

## 5. The daily "which applications need a nudge" list

**What it does:** A short morning list of the threads that have gone quiet and are worth a poke.
**You need:** Gmail connected.
**The prompt:**
```
Every weekday at 8:30am Mountain, scan my Gmail for application and recruiter
threads where the last message was mine and they haven't replied in 5 or more
days. Email me a short list with company, the person, and the date I last
wrote. Skip automated "we received your application" mail.
```
**Make it quieter:** Add "only send if there's at least one stalled thread."
**Watch out for:** Some "no reply" threads are dead, not stalled. After the first week you'll learn which companies ghost, and you can tell Zo to skip those domains so the list stays worth reading.

## 6. Salary and comp research for a role

**What it does:** A grounded pay range for a specific title and location before you name a number.
**You need:** Nothing connected; Zo reads public pages.
**The prompt:**
```
Research the typical total compensation for a "[role title]" in [your city]
or remote at a company around [company size, e.g. 50 to 200 people]. Pull
from public salary sources and recent job postings that list a range. Email
me a low, middle, and high number, each with where it came from, plus the
range you'd anchor to in a negotiation.
```
**Make it quieter:** Run it on demand per role, not on a schedule. Comp data doesn't move week to week.
**Watch out for:** Salary aggregators are noisy and often inflated or stale. Make Zo cite the source for each number so you can throw out the ones built on three self-reported data points.

## 7. LinkedIn and portfolio refresh nudge

**What it does:** Reminds you to keep your public profiles current while you're actively searching.
**You need:** Nothing connected; this is a reminder plus a read of your own public pages.
**The prompt:**
```
Every other Monday at 10:00am Mountain, look at my public profile at
[LinkedIn URL] and [portfolio URL]. Email me a short checklist: anything that
still says my old role, any project missing from the portfolio, and one
specific line I could sharpen. Keep it to five items or fewer.
```
**Make it quieter:** Every other week is already light. If it nags, move it to monthly.
**Watch out for:** LinkedIn often blocks automated reads. If Zo can't load the page, have it fall back to reminding you which sections to review yourself rather than pretending it saw the live profile.

## 8. Networking follow-up draft for a contact

**What it does:** Drafts a warm, specific follow-up to someone you met, so the connection doesn't go cold.
**You need:** Gmail connected, plus whatever notes you keep on the person.
**The prompt:**
```
When I give you a name and where I met them, draft a short follow-up email
to [contact name]. Reference [what we talked about], keep it to four
sentences, and end with one concrete ask or next step. Pull any past thread
with them from my Gmail for context. Save it as a draft for me to review.
```
**Make it quieter:** On-demand by design. It fires when you feed it a name.
**Watch out for:** Generic networking emails get ignored. If your note about the person is vague, the draft will be too, so give Zo one real detail from the conversation to hang it on.

## 9. Weekly job-hunt recap of what moved

**What it does:** A Friday summary of where every thread stands, so Monday doesn't start from zero.
**You need:** Gmail connected, and your applications tracker if you keep one.
**The prompt:**
```
Every Friday at 4:00pm Mountain, summarize my week's job hunt: new
applications I sent, replies I got, interviews scheduled, and threads that
went quiet. Pull from my Gmail and my tracker at [tracker location]. Email
me a clear status list grouped by company, and flag the two things that most
need my attention next week.
```
**Make it quieter:** Keep this one weekly. It's the recap that resets your head, and you want it every Friday.
**Watch out for:** It can only summarize what it can see. If half your search lives in a board's internal messaging or on the phone, tell Zo that up front so the recap doesn't read as complete when it isn't.

## Before you paste all nine

Two rules keep this from turning into nine notifications you mute by next Tuesday. First, build them one at a time. Get the new-posting watcher behaving the way you want, run it for a few days, then add the follow-up nudge. Nine automations stood up in one night and never tuned is nine things you'll ignore. Second, the ones that touch your inbox or draft on your behalf are worth running under a scoped persona that can read and draft but cannot send, post, or charge on its own. Job hunting is exactly when you don't want a stray auto-send going to a recruiter. The plugin-in-automation guide covers how to box them in.

Start with the new-posting watcher and the follow-up reminder. Those two are the difference between a search that drifts and one that actually moves, and once you feel them working you'll know which of the other seven you need.

If you're starting from zero, read the automations explainer first, because the recipes that use Gmail, Stripe, or Notion need those connected first (the public-web ones don't). Then pick one, not nine. This is the kind of guide I write every week. They live at jeffkazzee.zo.space/writing.
