---
title: Set Zo to work while you sleep: automations without the cron-job headache
id: zo-automations-101
series: Zo Computer 101
category: automations
kind: explainer
order: 1
date: 2026-06-18
updated: 2026-06-18
excerpt: An automation is one thing: Zo running a prompt on a schedule. How to make one in plain English, the conditional trick that turns it into a filter, and the cost mistake that quietly drains your credits.
tags: [automations, scheduling, conditional-alerts, beginners]
related: [plugin-inside-automation, zo-plugins-integrations]
difficulty: beginner
reading_time: 8
---

An automation sounds like a feature you need to learn. It is not. It is one sentence: Zo running a prompt on a schedule. Same Zo, same files, same tools, same integrations, just firing on its own when you are not in the chat. If you can ask Zo to do something now, you can ask it to do that thing every morning. That is the entire concept, and once it lands you start seeing automations everywhere in your week.

The reason this matters more than it sounds: the best automations are not "do a task." They are "watch for a thing and only bother me when it happens." A good automation is a filter that buys back your attention, not another notification firing into the void.

> If you'd write the same prompt in chat more than twice a month, it probably wants to be an automation.

## Making one: just say it

You do not open a form and configure a cron job. You tell Zo, in plain English: "every weekday at 8am, summarize my calendar and email it to me." Zo reads that as a schedule, writes the prompt, and confirms before saving. You can also open the Automations tab and hit plus to build one by hand, but the chat way is faster and you will use it more.

Schedules are described the same way, in English, and Zo parses the cadence:

- "once, tomorrow at 6pm"
- "every weekday at 8am"
- "every hour"
- "the first Monday of every month at 9am"
- "every 15 minutes" for short polls

You can change the schedule later by editing the automation's row or just asking Zo to change it.

## The patterns that actually earn their keep

Not everything should be an automation. The ones that work share two traits: they want fresh context every time they run, and they save you from having to remember to ask. A few shapes that reliably pay off:

- **Morning briefing.** One message before you open your laptop: today's calendar, unread VIP email, overnight messages, a custom news pull. The thing that replaces opening six tabs.
- **Inbox-to-action triage.** Read incoming messages on a schedule, ping you only for the ones that need you, with a draft reply attached.
- **Page watcher.** Check a URL on a schedule, message you only when something changed. A status page, a price, a stock level, a release.
- **Routine report.** Query a data file, format it, post it where it belongs. Friday revenue from a Stripe export into a three-line summary.
- **Habit nudge.** Text yourself the prompt for the habit you're building, conditionally, so it doesn't feel like a robot nagging you.

## The conditional trick that changes everything

This is the move that separates a useful automation from spam you mute in a week. Ask Zo to ping you only when something is true. The automation still runs every time, but it only reaches you when it matters:

- "Text me only if the deploy failed."
- "Email me the digest only if there are unread VIP messages."
- "DM me only when the price drops below 400."

Now the automation is a filter, not another inbox. It runs in the background, stays quiet on the boring days, and surfaces only the signal. That conditional clause is the difference between an automation you keep and one you delete.

## Delivery: how, and whether, it reaches you

By default an automation runs quietly and writes its result to your chat history. You choose whether it actively pings you. Email, SMS, Telegram, Discord, or Slack for things you actually want to see. No notification for jobs that just maintain state in the background: refresh a data export, save a daily snapshot, index a folder. Plenty of good automations should never message you at all. They just keep something current so it is ready when you need it.

## The cost mistake nobody warns you about

Here is the part that bites beginners. Automations spend AI credits the same way a chat does. Every run is a full Zo session. A five-minute schedule is not "a tiny background task," it is 288 full sessions a day, and that adds up fast whether or not you ever read the output.

Two habits keep this sane. Use the longest interval that still does the job: most "every 15 minutes" automations are fine at every hour, and most hourly ones are fine once or twice a day. And lean on conditional notifications so you are not generating expensive output you will never read. The goal is fresh context when it matters, not a model running laps for no reason.

## A scope note worth knowing early

Automations run with the same access as your chats. Every file, every message, every connected integration. If you want to box in what an automation can touch, run it under a persona with a narrow tool set. A "reporting" persona that can read files and send email but cannot delete anything or post to your socials is a safer thing to leave running unattended. More on personas later in this series, but file that away now: an unattended automation with full access is a lot of trust to hand a background job.

## Reviewing what ran

Every automation run is a real conversation saved to your history. Open the Automations tab, click any task, and you see each past run, the prompt it executed, the tools it used, and the output. When one misfires, you do not guess. You tell Zo "open last night's run of my morning brief and tell me why the calendar section was empty," and it reads its own run and fixes the prompt or the schedule.

## The one to build first

Build the morning briefing. It is the automation that justifies the whole concept in a week, because you feel the difference every single day. Tell Zo what you want in your first message of the day, when you want it, and where to send it. Then add the conditional ones as you notice yourself checking the same thing on a loop. Start with one that runs once a day, get it right, and expand from there.

Zo Computer 101 is a growing library of beginner guides for people who'd rather build than read docs. The automation you just learned gets dramatically more useful the moment you give it a connected app to work with, which is the plugin-inside-an-automation guide, the highest-leverage move in the platform. Read the plugins guide first if you haven't connected anything yet. Both are in the library at jeffkazzee.zo.space/writing.
