---
title: The move most people miss: a plugin inside an automation runs your week for you
id: plugin-inside-automation
series: Zo Computer 101
category: automations
kind: how-to
order: 2
date: 2026-06-18
updated: 2026-06-18
excerpt: A plugin connects Zo to your apps. An automation runs on a schedule. Combine them and your apps start working without you. How to wire it, the scope trap to avoid, and the failure mode nobody warns you about.
tags: [automations, plugins, integrations, conditional-alerts, calendar, email, beginners]
related: [zo-automations-101, zo-plugins-integrations]
difficulty: beginner
reading_time: 8
---

Two guides back you connected a plugin. One guide back you built an automation. Here is the part the docs tend to gloss and most people figure out by accident: those two things combine, and that combination is when Zo starts running your week. A plugin gives Zo a key to your apps. An automation gives it a schedule. Put a plugin inside an automation and your apps start doing things without you in the room.

This is the highest-leverage move in the whole platform for a beginner, and it's also where the most preventable mistakes happen. So this guide is both: how to wire it, and the two traps that bite people who wire it wrong.

> A plugin without a conditional is a robot reading you your own inbox out loud.

## The mechanic: nothing new to learn

Nothing new to learn here. The scheduled Zo is the full Zo, plugins and all. An automation is just Zo running a prompt on a schedule, and that scheduled Zo has the same access your chat Zo does by default, including every connected plugin. So if you can say "summarize my calendar" in chat because Google Calendar is connected, you can put that same instruction on a schedule and it just works.

You write it the way you'd write any automation, in plain English, and you name the app:

- "Every weekday at 7am, read my Google Calendar and email me the day's schedule."
- "Every hour, check Gmail for anything from my top clients and text me only if there is one."
- "Every Friday at 5pm, pull this week's paid Stripe orders and post the total to my Notion."

The plugin is already connected, so Zo reaches for it on schedule the same way it would in a live chat. That's the whole trick. The power isn't in a new feature; it's in realizing the scheduled Zo is the full Zo.

## The patterns that actually pay

The combinations worth building share a shape: read from one app, decide, act in another app or message you. A few that earn their keep:

- **Calendar to inbox.** Read your calendar each morning, email you the briefing. The classic.
- **Inbox to alert.** Scan Gmail on a schedule, text you only for VIP senders, with a draft reply attached.
- **Data to report.** Pull numbers from Stripe or a Sheet, format them, write them to Notion or Linear on a cadence.
- **Watch to ping.** Check a source through a plugin and message you on a channel only when something changed.
- **App to app.** Read new rows from Airtable, create matching tasks in Google Tasks. No human in the loop at all.

That last category, app-to-app with no message, is the one people underestimate. Plenty of good automations never ping you. They just keep two of your apps in sync in the background.

## Trap 1: the notification you'll mute in a week

If your plugin-powered automation messages you every single run, you will mute it fast, and then it's worse than useless because it's spending credits to be ignored. The fix is the conditional clause from the automations guide, and it matters even more here because plugins make it easy to generate a lot of output:

- Not "email me my inbox summary." Instead: "email me **only if** there's an unread message from a client."
- Not "text me the order count." Instead: "text me **only if** today's orders are below target."

The automation still runs and still reads the app every time. It just stays quiet unless the thing it found is worth your attention. A plugin plus a conditional is a filter that buys back your focus. A plugin without one is a robot reading you your own inbox out loud.

## Trap 2: the scope problem nobody warns you about

Here's the one that actually matters for safety. An automation runs unattended with the same access as your chats, which means every connected plugin. A scheduled job that can send email, post to your socials, and charge cards is a lot of authority to leave running while you sleep, especially if the prompt is even slightly ambiguous.

The clean fix is to run the automation under a **persona with a narrow tool set.** Give a "morning reporter" persona read access to your calendar and inbox and the ability to email you, and nothing else: no posting to X, no deleting files. Now the automation can do its job and physically cannot do damage if the prompt goes sideways. This is the right default for any unattended automation that touches a plugin which can send or post on your behalf.

Personas get their own guide later in this series. For now, the rule: the more an automation can do without you watching, the more you want it boxed in.

## The failure mode to expect

Plugin-powered automations break in a specific, predictable way: the plugin's access lapses. You change a Google password, the token goes stale, and the next run throws an `invalid_grant` on the Calendar call. The automation keeps firing on schedule but the app calls fail, and you won't notice, because silence is the whole point of a quiet automation.

Two habits cover this. When you set up anything important, add "if you can't reach the app, text me" so a broken connection surfaces instead of failing in the dark. And when an automation goes quiet for too long, check its run history: open the Automations tab and click the task to see the run that failed and why. Reconnect the plugin and move on.

## Build this one first

The morning briefing, with your calendar plugin, conditionally delivered, under a read-only persona. It uses every idea in this guide at once: a connected plugin, a schedule, a conditional so it's signal not noise, and a scoped persona so it's safe to leave running. Get that one working and you understand the most useful pattern Zo has. Everything else is a variation on it.

Zo Computer 101 is a growing library of beginner guides written by a heavy independent user. This guide sits on top of two others: the automations guide for the schedule, and the plugins guide for the connected app. If either felt thin, read those, then come back. The whole library lives at jeffkazzee.zo.space/writing.
