---
title: "Wire Zo to your phone: Telegram, Discord, SMS, and email"
id: messaging-channels
category: integrations
kind: how-to
date: 2026-06-18
updated: 2026-06-18
excerpt: Zo doesn't have to live in a browser tab. Connect a channel and you can text it, DM it, or email it, and it can ping you back. Here's each channel and what it's good for.
tags: [zo, messaging, telegram, discord, sms, email, beginner]
related: [connect-a-plugin, zo-automations-101, conditional-automations]
difficulty: beginner
reading_time: 6
---

The version of Zo that lives in a browser tab is the version you forget to open. The useful version is the one that texts you at 7:30am with your day already sorted, or the one you fire a half-formed idea at from a trailhead before you lose it. Connecting a channel takes about two minutes and it changes what Zo is for. It stops being a website you visit and becomes a thing you talk to.

> A tool you have to remember to open is a tool you'll stop using. A tool that texts you doesn't have that problem.

Zo talks over five channels: Telegram, Discord, SMS, email, and Slack. It's the same Zo on every one of them, with your full workspace, your connected integrations, web search, and image generation all available no matter which one you message from. Conversations you have over text or Telegram also show up in your chat history in the web app, so nothing is stranded on your phone.

## Connect one, not all five

You set channels up in **Settings > Channels** on zo.computer. Telegram and Discord are native here, so don't go hunting for them in the integrations catalog. They aren't catalog apps. They're built in.

One trap worth naming before you start: AI model providers (OpenAI keys, Anthropic keys, that sort of thing) live under **Settings > AI**, not Channels. Channels are how you reach Zo. Providers are which brain answers. Different settings, easy to confuse on day one.

Email needs zero setup. You already have an address. It's `yourhandle@zo.computer`, and emailing it starts a conversation. Worth saying plainly: that address is a chat interface, not an inbox. Mail you send there isn't stored or searchable later. If you want Zo to read your actual inbox or send mail as you, that's a Gmail or Outlook integration, which is a different thing entirely.

## What each channel is actually good for

They are not interchangeable. Each one has a shape.

| Channel | Two-way? | Best for |
| --- | --- | --- |
| SMS | Yes | Capture from anywhere, no app, no signal-hungry data |
| Telegram | Yes | Daily driver, sends images and files back |
| Discord | Yes | If you already live in a server, threads keep things tidy |
| Email | Yes | Longer prompts, attachments, anything you'd rather type |
| Slack | Yes | Work context, dedicated assistant pane |

A few quirks that bite people:

- **SMS keeps it short.** Zo holds replies under 150 words over text, and it can send MMS media. Your text thread is one long running conversation. Zo will periodically start a fresh one with a summary of where you left off, so don't be surprised when the thread resets.
- **Discord splits long messages.** Discord caps messages at 2000 characters, so a long answer arrives in pieces. @mention Zo in a channel and it spins up a thread for that conversation automatically.
- **Telegram in a group needs admin.** To @mention Zo in a group chat, the bot has to be a group admin. In a one-on-one DM it just works.

## DMs versus groups, because this surprises people

In a DM, Zo answers every message you send. In any shared space (a Discord channel, a Slack channel, a Telegram group) it goes quiet unless you @mention it, or on Telegram reply directly to it. That's deliberate. Nobody wants a bot barging into every line of a group chat.

Two more things about groups. Zo runs on *your* workspace and *your* integrations even inside a shared channel, so when it answers, it's reaching into your files, not the group's. And it prefixes its messages with `[yourhandle.zo.computer]` so everyone can see which workspace is talking. Someone else in that same channel can @mention Zo too, and it runs against their workspace instead.

Handy commands that work across Telegram, Discord, Slack, and SMS:

| Command | Does |
| --- | --- |
| `/new` | Start a clean conversation |
| `/conversations` | List and switch between recent ones |
| `/model [name]` | Show or switch the active model |
| `/persona [name]` | Show or switch the active persona |

Your model and persona picks are saved per app. The model you set in Telegram won't touch your Slack model. Pair this with the personas guide and you can run a tight, locked-down persona over SMS and a different one in the web app.

## The actual payoff: delivery

Talking to Zo is half of it. The half that earns the setup is the reverse direction. Any automation can deliver its result to any of these channels. So the morning brief stops being a thing you go read and becomes a thing that arrives.

A concrete one I'd set up first: a weekday automation that pulls your calendar and a couple of news threads and sends a one-page brief to Telegram at 7:30am. You read it before you open the laptop. See the automations guide for the schedule wiring.

The sharper move is conditional delivery. Tell the automation to only ping you when something is true:

- Text me only if a deploy failed.
- Email the digest only if there's an unread VIP message.
- DM me only when the price drops below a number I set.

Now the channel is a filter instead of another feed. That distinction is the whole reason to bother, and there's a dedicated conditional automations guide that goes deep on it.

And it runs the other way for capture. Text Zo a stray thought with a prefix and a rule files it into the right note before it evaporates. The phone in your pocket becomes the front door to your workspace, which is the thing a browser tab can never be.

If wiring a channel made Zo feel less like a website and more like a thing you actually use, the rest of Zo Computer 101 is built the same way: specific, tested, no hand-waving. It lives at jeffkazzee.zo.space/writing.
