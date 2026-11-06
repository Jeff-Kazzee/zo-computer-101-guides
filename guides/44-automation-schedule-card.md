---
title: "Every automation schedule, with the rrule that actually fires it"
id: automation-schedule-card
category: automations
kind: reference
date: 2026-06-18
updated: 2026-06-18
excerpt: You describe an automation schedule in plain English and Zo turns it into an rrule. Here's the reference card of the common ones, including the cadences people get subtly wrong.
tags: [zo, automations, scheduling, rrule, reference]
related: [zo-automations-101, conditional-automations, debug-automation-run]
difficulty: beginner
reading_time: 5
---

The fastest way to break an automation is to be vague about when it runs. Say "every day" when you meant weekdays and your Monday briefing also wakes you on Saturday. The schedule is the part people hand-wave, and it's the part that costs them. This is the card you bookmark so you don't.

> You don't write the rrule. You write the sentence. The sentence is where every scheduling bug actually starts.

## How scheduling works in Zo

You describe the cadence in plain English, Zo parses it into a recurrence rule (the underlying format is an rrule, the same RFC standard calendar apps use), and it confirms before saving. You never touch the raw rule unless you want to. So the skill here isn't memorizing rrule syntax. It's saying the cadence precisely enough that the parse matches what's in your head.

Two ways to set the schedule: tell Zo in chat ("every weekday at 7:30am, email me a brief"), or use the Automations page to create or edit the schedule. To change a schedule later, edit it from the automation's row in that tab, or just ask Zo to change it.

## The reference card

Every one of these is a phrase Zo parses directly. The "watch for" column is where people get burned.

| You say | What it does | Watch for |
| --- | --- | --- |
| `once, tomorrow at 6pm` | Runs a single time, then never again | It will not repeat. If you wanted a daily thing, you said the wrong word |
| `every day at 8am` | Fires all seven days, including weekends | This is not "weekdays." Saturday and Sunday are in |
| `every weekday at 8am` | Monday through Friday only | The one you usually want for work briefings |
| `every Monday at 9am` | Once a week, that weekday | Good for weekly reports and reviews |
| `every hour` | Top of every hour, around the clock | 24 runs a day. Each one is a full session |
| `every 15 minutes` | Four times an hour, all day | ~96 runs a day. Read the cost note below before you commit |
| `the first Monday of every month at 9am` | One specific weekday each month | Cleaner than "the 1st," which can land on a weekend |
| `every Friday at 4pm` | Weekly, end of week | The classic slot for a wrap-up or revenue report |

If a phrase you try comes back parsed in a way you didn't mean, rephrase and let Zo re-confirm. The confirmation step exists so you catch the mismatch before it's live, not after it's pinged you at 3am.

## The four that beginners get wrong

**"Every day" is not "every weekday."** This is the single most common mix-up. "Every day" includes Saturday and Sunday. If the automation is about your work calendar or inbox, you almost certainly want "every weekday," or you'll get empty, pointless weekend runs that still cost credits.

**High-frequency polls add up fast.** Every run is a real automation execution that spends credits, so short intervals add up fast. "Every 5 minutes" is roughly 288 sessions a day. "Every 15 minutes" is roughly 96. That's fine for something genuinely time-sensitive, like watching a status page for an outage. It's a terrible default for a job that could run hourly. The fix is two-part: stretch the interval as far as the task allows, and pair it with a conditional notification so it only ever messages you when something is actually true. A page-watcher that runs every 15 minutes but only texts you when a service flips from green is cheap on your attention even if it isn't cheap on credits.

**Timezone matters, so state it.** "8am" is 8am in a timezone. Your Zo runs on UTC under the hood, and "8am" should resolve to your local morning, but the way to never wonder is to be explicit in the prompt: "every weekday at 8am Mountain time." When daylight saving shifts, a wall-clock time like "8am Mountain" follows your clock; a fixed UTC offset won't. If a run lands an hour off from what you expected, the timezone is the first thing to check.

**"Once" means once.** "Once, tomorrow at 6pm" runs a single time and retires itself. People use it for a one-shot reminder, then a week later go looking for why it didn't fire again. It did its one job. If you want it back, you want a recurring cadence instead.

## A couple of patterns worth copying

- One-shot reminder: `once, this Friday at 2pm, remind me to send the invoice`
- Workday briefing: `every weekday at 7:30am, summarize my calendar and unread VIP email`
- Cheap watcher: `every 30 minutes, check [the status page], and text me only if a service is down`
- Monthly report: `the first Monday of every month at 9am, generate last month's summary in reports/`

The rule of thumb for cost: if you'd write the same prompt in chat more than twice a month, it wants to be an automation. And if the interval is shorter than an hour, make sure the notification is conditional, or you're paying for output you'll never read.

If you set the cadence right and a run still misfires, that's a different problem with its own fix, and the debugging-automation-runs guide covers it. The rest of the basics, like what makes a good automation in the first place, lives in the automations guide. All of Zo Computer 101 is built the same way, specific and tested with no hand-waving, at jeffkazzee.zo.space/writing.
