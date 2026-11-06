---
title: "The conditional clause that turns an automation from spam into signal"
id: conditional-automations
category: automations
kind: how-to
date: 2026-06-18
updated: 2026-06-18
excerpt: An automation that pings you every run gets muted in a week. Add one conditional clause and it goes quiet until something actually matters. That clause is what makes the automation worth keeping.
tags: [zo, automations, conditional-alerts, beginner, scheduling]
related: [zo-automations-101, plugin-inside-automation, debug-automation-run]
difficulty: beginner
reading_time: 6
---

You set up an automation to watch something for you, and for the first two days the alerts feel great. By the end of the week you're swiping them away without reading, and a month later you've muted the whole channel and the automation might as well not exist. The fix is one clause in the prompt. You tell Zo to reach you only when a specific thing is true, and the same automation that was noise becomes the one alert you actually trust.

> An alert you ignore is worse than no alert, because you paid for it and it trained you to stop looking.

## What an automation actually is

An automation is Zo running a prompt on a schedule. Same files, same tools, same connected integrations, just firing on its own when you're not in the chat. By default it runs quietly and writes the result to your chat history. Nothing pings you. You decide whether it reaches you, and how: email, SMS, Telegram, Discord, or Slack.

Most people set delivery to "every run" and stop there. That's the mistake. A prompt like "every morning at 8, check [the deploy status] and text me the result" texts you a green checkmark almost every day. A pile of texts to catch the one problem. Your brain learns the pattern fast, and the pattern is "this is safe to ignore."

## The clause that flips it

The move is to push the decision about whether to notify you into the prompt itself. The automation still runs every time. It still reads the data, every interval, on schedule. It just stays silent unless the condition you named is met. That turns the thing from a feed into a filter.

Watch what one phrase does:

| Spam version | Signal version |
| --- | --- |
| Every 30 min, check [status.example.com] and text me the status | Every 30 min, check [status.example.com]. Text me **only if** something goes from green to down, with the service name and the time it started |
| Every morning, email me a summary of [my inbox] | Email me a digest **only if** there are unread messages from [my VIP list], otherwise stay quiet |
| Hourly, check the price of [the item] and DM me | DM me **only when** the price drops below [400], and include the current price and the link |

The schedule and the data read stay identical. The difference is that the right column reaches you maybe twice a month, and when it does, you read it, because the automation has never once wasted your attention.

## Three more that earn their keep

A few patterns where the conditional clause does the heavy lifting:

1. **Page watcher.** "Every 15 minutes, check [the release notes page]. Message me only when the version number changes, and paste the new entry." You get one ping the day they ship, not 96 pings a day saying nothing moved.
2. **Inbox triage.** "Every weekday at 7am, scan [email] since 5pm yesterday. Only ping me for anything that looks like it needs a reply today, and attach a draft." The automation reads everything. It interrupts you for the two that matter.
3. **Threshold report.** "Every Friday at 4pm, query [the revenue export]. Email me the full report always, but also text me **only if** the week is down more than [15%] versus last week." This one splits delivery: the routine report goes to email where you read it on your schedule, the bad-news case jumps to SMS where you'll see it now.

That last pattern is worth stealing. You can route the calm output to a slow channel and the alarming output to a fast one, all from the same run.

## The cost angle nobody mentions

A conditional clause controls whether Zo *messages* you. It does not control whether the automation *runs*. Every scheduled run spends AI credits the same way a chat does, condition met or not. A prompt set to "every 5 minutes" fires 288 times a day and bills for all 288, even if it only texts you once a month.

So two levers, not one:

- **Interval:** use the longest one that still catches the thing in time. A price you'd act on within the hour does not need a 5-minute poll. Most "every 15 minutes" automations are fine at 30 or 60.
- **Delivery:** make it conditional so you're not generating and reading expensive output you'll never act on.

Stretch the interval and tighten the condition, and you get an automation that's cheap to run and impossible to ignore. Get both wrong and you've built a machine that charges you to spam yourself.

## Two practical notes

Conditions can be fuzzy, and that's allowed. "Only ping me if anything looks urgent" leans on Zo's judgment instead of a hard number, which is fine for triage where you can't write the rule as a clean threshold. For money and status checks, prefer a concrete trigger ("below [400]", "goes from green to down") so there's no ambiguity about when it should fire.

And if the multi-step part of the automation is something you'd want to run by hand too, lift those steps into a skill and have the automation call it. The skill-inside-an-automation guide covers that pattern. When an alert misfires or goes silent when it shouldn't have, every run is saved as a real conversation you can open and inspect, which is the whole subject of the guide on debugging a run. Start with the automations basics guide if you haven't built one yet.

The clause is one line, and it flips the whole behavior. An automation without it is another inbox you'll learn to skip. An automation with it sits quiet for weeks and then tells you the one thing you needed to know, which is the only reason to build one at all.

If this kept you from muting another alert, the rest of Zo Computer 101 is written to the same standard: specific, tested, no filler. It lives at jeffkazzee.zo.space/writing.
