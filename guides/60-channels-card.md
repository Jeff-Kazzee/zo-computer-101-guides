---
title: "Every messaging channel and how to wire it"
id: channels-card
category: reference
kind: reference
date: 2026-06-18
updated: 2026-06-18
excerpt: Zo can reach you on five channels, and each one wires up in its own way. This is the card: what each channel is good for, how it connects, and the DM-vs-group behavior that surprises people.
tags: [zo, messaging, telegram, discord, sms, email, slack, reference]
related: [messaging-channels, conditional-automations, zo-automations-101]
difficulty: beginner
reading_time: 4
---

Zo does not live in one browser tab. It can reach you on five channels, and each one connects in its own way and behaves differently once it's live. Get the wiring right and Zo becomes the thing that texts you when a deploy breaks at 2am, instead of a window you have to remember to open. This is the card for that: what each channel is for, how you turn it on, and the one behavior that trips up everybody the first time they add Zo to a group.

> The same Zo runs everywhere. Your files, your integrations, your full workspace, whether you're typing in the web app or replying to a text.

The thing to understand before any of the details: every channel is two-way. You message Zo, Zo can message you back, and conversations from any channel show up in your history in the web app. There is no read-only mode and no second-class channel. Email and SMS feel different from Telegram and Discord, but under the hood it's one assistant answering from one workspace.

## The card

| Channel | Connect via | Best for | Group behavior |
| --- | --- | --- | --- |
| Email | Works out of the box. Email `yourhandle@zo.computer` | Long prompts, attachments, anything you'd rather type at a keyboard | n/a, each email is its own conversation |
| SMS | Settings > Channels | Quick asks, nudges, replies on the go. Responses stay under 150 words | n/a |
| Telegram | Settings > Channels (native) | Daily back-and-forth, sending you images and files | @mention only, bot must be a group admin |
| Discord | Settings > Channels (native) | Servers, teams, threaded topics | @mention in a channel spins up a thread |
| Slack | Settings > Channels | Work context, the assistant pane sidebar | @mention in a channel or thread |

Telegram and Discord are worth a flag here. They are native channels you turn on in Settings > Channels, not catalog integrations you connect through the Pipedream app list. People go hunting for them in the wrong place. They're in Channels, next to SMS and Slack.

## The behavior that surprises people

In a DM, Zo answers everything you send. Simple. In a group or a channel, it goes quiet unless you actually call on it. You @mention Zo (or, on Telegram, reply directly to one of its messages) and only then does it respond. This is on purpose. Drop Zo into a busy Discord server with no filter and it would try to answer every message in the room. The @mention is the leash.

A few specifics that follow from that:

1. **Discord channel @mentions create a thread.** Tag Zo in a channel and the conversation moves into its own thread, so you're not burying the channel under a long answer. Each thread is its own conversation with its own history.
2. **Zo only answers you.** Even in a shared channel, Zo runs on *your* workspace with *your* integrations. Someone else in the room can @mention Zo too, but it runs on their Zo, not yours. Nobody is reading your files by tagging your bot.
3. **It labels itself in groups.** In any group context Zo prefixes its replies with `[yourhandle.zo.computer]` so it's clear whose assistant just spoke.

## Commands that work across channels

Discord, Slack, Telegram, and SMS all share a small command set. Worth memorizing the two you'll actually use:

- `/new` starts a fresh conversation. Reach for this when the current thread has wandered and you want a clean slate.
- `/conversations` lists recent conversations so you can jump back into one.

The rest fill in around those: `/status` (it's `/info` in Slack) shows what conversation you're in, `/model` shows or switches the active model, `/persona` does the same for personas, and `/help` lists everything. Your model and persona picks are saved per channel, so the model you set in Discord won't touch your SMS setup.

## Two quirks to know

SMS and email each handle conversation boundaries differently from the chat-style channels. Your SMS thread is one long ongoing conversation, and Zo periodically rolls it into a fresh one with a summary so it doesn't drag a year of texts into every reply. Email is the opposite: every message you send to `yourhandle@zo.computer` starts a brand new conversation. And email is a conversational front door, not an inbox. Zo doesn't store your mail there. If you want Zo reading your actual inbox or sending mail as you, that's a Gmail or Outlook integration, a different thing entirely.

## Where this pays off

The reason to wire up channels isn't novelty. It's that automations can deliver to any of them. An automation is just Zo running a prompt on a schedule, and you choose where the result lands: email, SMS, Telegram, Discord, or Slack. Set up a morning brief and have it text you. Watch a status page and have it ping Discord only when something flips to red.

That last part is the move most people miss. You can make delivery conditional, and the moment you do, the channel stops being another inbox and becomes a filter. "Text me only if the deploy failed." "Email the digest only when there's a VIP message waiting." The channel goes silent until the thing you care about is actually true. I dig into that pattern in the conditional automations guide, and the broader setup lives in the Zo automations guide.

If you want the full mechanics on any single channel, threads, attachments, character limits, the messaging channels how-to in the Zo docs goes deeper than this card does. The rest of Zo Computer 101 lives at jeffkazzee.zo.space/writing.
