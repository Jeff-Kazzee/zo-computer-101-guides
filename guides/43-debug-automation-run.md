---
title: "Your automation went quiet. Here's how to read its run history and fix it"
id: debug-automation-run
category: automations
kind: troubleshooting
date: 2026-06-18
updated: 2026-06-18
excerpt: A scheduled automation that stops working fails silently, because quiet is what you asked for. Here's how to open its run history, read what actually happened, and fix the cause.
tags: [zo, automations, troubleshooting, debugging, beginner]
related: [zo-automations-101, conditional-automations, plugin-inside-automation]
difficulty: beginner
reading_time: 6
---

Your morning brief landed every day for three weeks, and then it didn't. No error, no bounce, no angry red banner. The automation just went quiet, and you only noticed because the thing you relied on wasn't in your inbox. That silence is the problem with automations: you built them to run without bothering you, so when they break, they break the same way they succeed, by saying nothing.

The good news is that nothing is actually hidden. Every automation run is a real Zo conversation, saved to your history with the exact prompt it executed, the tools it tried to use, and whatever it produced. You don't have to guess what happened. You have to go read it.

> A silent automation is a stack of transcripts you haven't opened yet, not a black box you have to guess at.

## Open the run, read the transcript

Start in the **Automations** tab. Click the task that went quiet, and you'll see its list of past runs. Open the run from the day it stopped working, or the most recent one if it's a daily job. Inside is a full conversation: the prompt Zo ran, every tool call it made, and the output.

Read it like a detective. You are hunting the first place reality diverged from what you expected. You're not looking for whether the result is good. You're looking for the first place reality diverged from what you expected. Two things tell you most of the story:

1. **Did the tools fire?** If your brief pulls Gmail and the run has no Gmail call in it, the problem is upstream of the writing. If the call is there but came back empty or errored, the problem is the connection or the data.
2. **What did the prompt actually say?** The plain-English schedule you gave Zo got turned into a real prompt. Sometimes that prompt is more literal, or more vague, than you remember asking for.

## The four ways automations go quiet

Broken automations almost always fall into one of four buckets. Match the symptom to the cause before you change anything. Match the symptom to the cause before you change anything.

| Symptom in the run | Likely cause |
| --- | --- |
| App call present but returns an auth error or empty result | A plugin's access lapsed |
| No notification ever, run output says "nothing matched" | A conditional that's never true |
| Runs at the wrong hour, or skips a day near a date boundary | Wrong timezone |
| Output is plausible but wrong, or off-topic | An ambiguous prompt |

The first one is the sneakiest. A connected app's access can lapse without telling anyone: a token expires, you change a password, you revoke a session somewhere else and forget. The schedule keeps firing on time, Zo keeps trying to call Gmail or Calendar, and the call quietly fails while the rest of the run plows ahead. To you it looks like the automation stopped. To the automation, it ran fine. The transcript is where those two stories reconcile.

The second one isn't a bug at all. If you wrote "email me only if there are unread VIP messages" and there haven't been any, the automation is doing exactly what you asked. Silence is the correct output. Open a run, confirm it says it checked and found nothing, and you've saved yourself from fixing something that isn't broken. The conditional automations guide goes deep on this if you want the patterns.

Timezone bugs hide near boundaries. An automation set for "every weekday at 8am" against the wrong zone can run at 1am your time, or skip a Monday that the server still thinks is Sunday. If the run timestamps look shifted by a consistent number of hours, that's your tell. The fix: tell Zo the zone explicitly when you set the schedule, or say "change this to 8am Mountain" and let it rewrite the timing.

## Let Zo read its own transcript

You don't have to diagnose this by hand. Zo can open its own run history and explain itself. The phrasing that works:

> "Open last night's run of my morning brief and tell me why the calendar section was empty."

It will read the transcript, find the tool call that failed or the step that came back empty, and tell you what went wrong. Better, you can hand it the fix in the same breath: "the Calendar connection looks expired, and once I reconnect it, change the schedule to 7am." It edits the prompt or the schedule directly. You're having a conversation about a conversation, which is a strange thing to get used to, and then it's the fastest debugging loop you've got.

## Build the alarm you wish you'd had

The real fix is making the next failure loud instead of silent. Add one line to the automation's prompt that turns a broken connection into a text message:

> "If you can't reach Gmail, text me instead of finishing."

Now a lapsed token pings your phone the morning it lapses, not three weeks later when you happen to notice the gap. That single instruction catches the most common silent-connection failures into something you find out about immediately. I add a version of it to every automation that depends on a connected app, because the cost of one extra sentence is nothing against the cost of trusting a job that quietly died.

While you're in there, tighten the prompt that caused the trouble. Vague instructions produce vague output that looks fine until you check it. "Summarize my email" invites Zo to guess what matters. "List unread email from the last 18 hours from anyone in my contacts, subject and one-line summary each" leaves far less room to drift.

## The habit that keeps them honest

Once a month, open one run of each automation you depend on and read it end to end. Confirm the tools still fire and the output still matches what you'd write yourself. Connections drift, inboxes change shape, the thing you set up in January isn't running against the same world in June. A five-minute audit catches the quiet failure before it costs you a missed brief or a deadline you trusted a robot to remember.

If you're still building these, the automations basics guide covers setup and scheduling, and the plugins-in-automations guide covers wiring a connected app into a scheduled job without it breaking the first time a token expires. The rest of Zo Computer 101 is built the same way, specific and tested with no hand-waving, at jeffkazzee.zo.space/writing.
