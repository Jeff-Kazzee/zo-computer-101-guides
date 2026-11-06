---
title: "Customer support on autopilot: 10 Zo automations that don't feel robotic"
id: recipes-role-support
category: recipes
kind: recipe-pack
audience: role
order: 3
date: 2026-06-18
updated: 2026-06-18
excerpt: Triage, draft replies, escalation alerts, and the knowledge-base upkeep nobody has time for. 10 support automations that keep the human in the loop, each copy-paste ready.
tags: [automations, recipes, support, triage, email, conditional-alerts, scheduling, notion]
related: [zo-automations-101, plugin-inside-automation, zo-plugins-integrations]
difficulty: beginner
reading_time: 9
---

Support work is mostly sorting. Forty messages land overnight and thirty-eight of them are the same three questions you've answered a hundred times, but the two that matter are buried somewhere in the middle, and you find out which two they were only after a customer has spent a morning getting angrier. The sorting is the job nobody trained you for and the part that eats your day. It's also the part a scheduled automation handles well, because almost all of it is "read what came in, rank it, and only put a human on the messages that need a human." Here are 10 you can paste into Zo today.

Every recipe below follows the same shape: what it does, what you need connected, the exact prompt to give Zo, the tweak that keeps it quiet, and the failure to watch for. One rule runs under all of them and I'm putting it up top because support touches customers directly: Zo drafts, you send. Nothing in this pack fires a reply to a real person on its own, and you should keep it that way even when you're tempted. Connect your plugins first (the integrations guide walks through it), then talk to Zo in plain English. Change the times, names, and thresholds to fit your queue.

> A customer can forgive a slow answer. They do not forgive a robot answering the wrong question fast. Keep the human on the send button and let the machine do the sorting.

## 1. Morning triage by urgency

**What it does:** Ranks everything that came into the support inbox overnight so you open the worst fire first.
**You need:** Gmail connected.
**The prompt:**
```
Every weekday at 7:30am Mountain, read my support inbox in Gmail from the
last 16 hours. Sort the messages into three buckets: urgent (angry tone,
service down, payment problem, legal words), normal questions, and noise
(newsletters, automated mail). Email me the urgent and normal lists with
sender, subject, and a one-line reason it landed in that bucket. Skip the
noise bucket entirely.
```
**Make it quieter:** Add "if the urgent bucket is empty, just send the normal list and say 'no fires this morning' at the top."
**Watch out for:** Tone detection is a guess. A customer typing in all caps because that's how they always type will look urgent. Read the one-line reason before you panic, and refine the urgent keywords after the first week.

## 2. Draft replies for the questions you answer every day

**What it does:** Pre-writes responses to your top repeat questions so you edit instead of starting from a blank box.
**You need:** Gmail connected, plus your help docs in Notion or a file.
**The prompt:**
```
Every weekday at 8:00am Mountain, find support emails from the last 16 hours
that ask one of my common questions: how to reset a password, where to find
an invoice, how to cancel, shipping status. For each, draft a reply in my
help-doc voice and save it as a Gmail draft addressed to that customer. Email
me the list of drafts you created so I can review and send each one myself.
```
**Make it quieter:** Add "only draft for questions you're confident match one of my known answers; flag the rest for me to handle from scratch."
**Watch out for:** This creates drafts. It does not send. If you ever see "and send it" creep into this prompt, delete those words. A confidently wrong auto-sent answer is worse than a slow one, because now you're apologizing for two things.

## 3. Escalation alert for angry or VIP customers

**What it does:** Texts you the moment a message comes in from a named account or reads as genuinely furious, instead of you finding it three hours into the queue.
**You need:** Gmail connected.
**The prompt:**
```
Every 30 minutes between 8am and 6pm Mountain on weekdays, check my support
inbox for new email from anyone at [vip-client-domain.com], from [key account
contact], or any message that reads as seriously upset (refund demand,
threatening to leave, "this is unacceptable", mentions a chargeback or a
lawyer). Text me only if one arrived, with the sender and the first line.
```
**Make it quieter:** This is the conditional one. It stays silent unless a VIP writes or someone's genuinely hot. That silence is the feature.
**Watch out for:** Every run spends credits. A 30-minute check across a 10-hour window is fine. Don't drop it to every 5 minutes around the clock or you're paying to scan an empty inbox 288 times a day.

## 4. Daily ticket-volume summary

**What it does:** One line at end of day telling you how heavy the queue actually was, so you can feel the trend instead of guessing.
**You need:** Gmail connected (or your ticketing tool, if Zo can reach it).
**The prompt:**
```
Every weekday at 6:00pm Mountain, count the support emails that came in today,
group them by rough topic (billing, technical, how-to, complaint), and email
me a four-line summary: total count, the busiest topic, anything unusual about
today's volume, and how it compares to yesterday.
```
**Make it quieter:** This one you want daily. Keep it scheduled, not conditional. The point is the trend line, which only works if it shows up every day.
**Watch out for:** Topic grouping is approximate and the counts depend on what Zo can see in the inbox. If a chunk of your volume lives in a separate ticketing tool Zo can't read, the number is partial, so tell it to say "inbox only" in the summary rather than implying it counted everything.

## 5. SLA-breach warning before you miss it

**What it does:** Flags tickets approaching your response deadline while there's still time to answer, not after you've blown it.
**You need:** Gmail connected.
**The prompt:**
```
Every weekday at 9am, 12pm, and 3pm Mountain, find support emails I received
more than 18 hours ago that I haven't replied to yet. If my SLA is a 24-hour
first response, these are the ones about to breach. Text me the short list
with sender, subject, and how many hours are left. If there are none, stay
silent.
```
**Make it quieter:** Already silent when the list is empty. Tune the 18-hour threshold to fire a few hours before your real deadline, not at it.
**Watch out for:** Zo knows you replied only if the reply went out from the connected inbox. If you answered a customer by phone or in a separate tool, it'll still flag that ticket as open. Note resolved-elsewhere tickets somewhere Zo can see, or expect a few false alarms.

## 6. Recurring-issue detector across the week

**What it does:** Spots the same problem showing up over and over, so you fix the cause instead of answering the symptom forty times.
**You need:** Gmail connected.
**The prompt:**
```
Every Friday at 2:00pm Mountain, look at this week's support emails and find
problems that came up three or more times: the same bug, the same confusing
step, the same broken link. Email me the top recurring issues ranked by how
often they appeared, with two example subject lines each, so I can see what's
actually generating tickets.
```
**Make it quieter:** Weekly is right. Raise the threshold from three to five if your volume is high and the list gets noisy.
**Watch out for:** A cluster of similar tickets sometimes means one real outage, not a recurring design flaw. Read the examples before you file a bug report, because "47 people emailed about logins" on Tuesday might just be Tuesday's incident.

## 7. Knowledge-base gap finder

**What it does:** Catches the questions customers ask that your help docs don't answer, which is the list that actually grows your knowledge base.
**You need:** Gmail connected, plus your help docs in Notion or a file Zo can read.
**The prompt:**
```
Every Monday at 10:00am Mountain, compare last week's support questions against
my help docs in [Notion KB link or file path]. Find questions customers asked
that my docs don't clearly answer. Email me a list of the missing topics,
ranked by how often each was asked, with a suggested article title for each.
Don't write the articles, just find the gaps.
```
**Make it quieter:** Add "only send if you found at least two real gaps." A week with full coverage doesn't need an email.
**Watch out for:** It compares against the docs it can actually read. If half your knowledge base lives in a PDF or a tool Zo can't open, it'll report gaps that are already covered somewhere it can't see. Point it at the real, complete source.

## 8. After-hours acknowledgement draft

**What it does:** Drafts a warm "we got your message, here's when you'll hear back" for things that land after you've logged off, so customers aren't staring at silence till morning.
**You need:** Gmail connected.
**The prompt:**
```
Every weekday at 7:00pm Mountain, find support emails that came in after 6pm
today and haven't been answered. For each, draft a short acknowledgement in my
voice: we received it, we'll reply by [next business morning], and a link to
my help docs in case it's something they can self-serve. Save them as Gmail
drafts and email me the list. Do not send.
```
**Make it quieter:** Add "skip anyone who already got an acknowledgement from me today."
**Watch out for:** An auto-acknowledgement that promises a time you can't hit is worse than no acknowledgement. These are drafts on purpose so you can glance at the queue and decide whether "by morning" is honest before any of them go out. Resist wiring this to auto-send, even though it's the most tempting one in the pack.

## 9. Weekly support recap for the team

**What it does:** Turns the week's queue into a short readable summary your team or your boss actually opens, instead of a dashboard nobody checks.
**You need:** Gmail connected (and Notion or a file if you want it logged).
**The prompt:**
```
Every Friday at 4:00pm Mountain, write a support recap for the week: total
tickets handled, the three most common issues, anything that escalated, the
biggest KB gap we found, and one thing that got better or worse versus last
week. Keep it under 250 words in plain language. Email it to me as a draft I
can forward to the team.
```
**Make it quieter:** Keep it weekly. It's a recap, not an alert, so a regular rhythm is the whole value.
**Watch out for:** Define your week (Mon to Fri vs. a rolling 7 days) in the prompt so the comparison to last week is honest. And it summarizes what it can see. If you want it to forward straight to the team later, get a few weeks of accurate drafts under your belt first and keep yourself on the send button until you trust the numbers.

## 10. Sentiment flag on incoming mail

**What it does:** Quietly marks the messages where a customer sounds like they're on the edge of churning, before the word "cancel" ever shows up.
**You need:** Gmail connected.
**The prompt:**
```
Every weekday at 11:00am and 4:00pm Mountain, scan the support emails that came
in since the last check and flag any that carry frustrated or disappointed
sentiment even if they're polite: phrases like "still not working", "third time
I've asked", "starting to regret". Email me only the flagged ones with sender,
subject, and the line that tripped the flag. If none, stay silent.
```
**Make it quieter:** Already conditional. The flagged line it quotes is what keeps this useful, so don't drop that part.
**Watch out for:** Sentiment reading is the fuzziest thing in this whole pack and it will miss sarcasm and over-read a blunt customer. Treat it as a nudge to look, not a verdict. The person who writes "third time I've asked" might be calm and the person who writes "thanks so much!" might be quietly done. Use it to catch the ones you'd otherwise skim past.

## Before you paste all ten

Two rules keep this from becoming ten things you mute by Friday. First, build them one at a time. Get the morning triage working and tuned, live with it for a few days, then add the escalation alert, then the next. Ten automations installed in one afternoon and never adjusted is ten low-quality guesses firing at you on a schedule. Tune as you go.

Second, and this matters more here than in any other pack because every recipe touches a real customer: run the ones with send access under a scoped persona that can read your inbox and write drafts but cannot send email, post anything, or charge a card on its own. That single boundary is what makes "Zo drafts, you send" a rule the system enforces instead of a promise you have to remember at 7pm on a Friday. The plugin-in-automation guide shows exactly how to box a persona in.

Start with morning triage and the escalation alert. Triage hands you a sorted queue before you've finished your coffee, and the escalation alert means a furious VIP can't sit unseen for three hours. Those two earn the whole idea in a day. Once you feel them working, the rest are obvious.

If you're starting from zero, read the automations explainer first, because the recipes that use Gmail, Stripe, or Notion need those connected first (the public-web ones don't). Then pick one, not ten. This is the kind of guide I write every week. They live at jeffkazzee.zo.space/writing.
