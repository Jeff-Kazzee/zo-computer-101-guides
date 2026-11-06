---
title: "Connect a plugin in 60 seconds (and the 1000-app catalog behind the curated list)"
id: connect-a-plugin
category: integrations
kind: how-to
date: 2026-06-18
updated: 2026-06-18
excerpt: Connecting an app to Zo is one click in chat, not an API-key scavenger hunt. Here's how it works, the curated-vs-catalog split, and why clicking Connect doesn't make Zo finish the task.
tags: [zo, integrations, plugins, beginner, setup]
related: [zo-plugins-integrations, secrets-and-keys, messaging-channels]
difficulty: beginner
reading_time: 6
---

Most tools make you hunt for an API key, paste it into a settings screen, pick scopes you don't understand, and pray the redirect URL matches. Zo skips all of that. You ask it to do something with an app it isn't connected to yet, and a Connect card appears right there in the chat. The whole flow is a single click and a standard OAuth window, the same login screen you'd see anywhere. The part that trips people up isn't the connecting. It's what happens after.

> Clicking Connect plugs in the app. It does not wake Zo up to finish what you asked. Zo stays idle until your next message.

## How a connect actually goes

Say you tell Zo "pull my three most recent Gmail threads and summarize them," and Gmail isn't connected. Here's the real sequence:

1. Zo notices the app is missing and surfaces a **Connect** card inline, in the conversation.
2. You click it. A normal OAuth window opens for that provider. You sign in and approve the scopes.
3. The window closes and the connection finalizes on its own. The card flips to connected.
4. You come back to the chat and say "go" (or just repeat the request).

Step four is the one nobody expects. Connecting the app does not hand control back to Zo. It was waiting on you, and authorizing in a separate browser window doesn't ping it. So the rhythm is: Zo offers the button, you connect, then you nudge it again. If you connect and then sit there expecting your inbox summary to roll in, you'll be waiting on a turn that never comes. One more message kicks it off.

You can also wire things up ahead of time from the **Integrations** page in Settings instead of waiting for a card to appear in chat. Same connections, same OAuth, just done proactively. Useful when you already know you'll want Calendar and Drive before you start asking for anything.

## Two tiers, and why the difference matters

Not every app Zo can reach is treated the same way, and you should know which lane you're in before you lean on something for real work.

The first tier is the curated set. These have dedicated handling built into Zo and behave the most reliably:

| App | What it covers |
| --- | --- |
| Gmail | Read, search, draft, send |
| Google Calendar | Events, scheduling |
| Google Drive | Files, including Docs/Sheets/Slides |
| Google Tasks, Sheets | Task lists, spreadsheets |
| Notion, Linear | Pages, issues, projects |
| Dropbox, Spotify, Airtable | Files, music, bases |
| Microsoft (Outlook, OneDrive) | Mail, calendar, files |
| X, GitHub, Stripe | Posts, repos, payments |

The second tier is the Pipedream catalog: more than 1000 apps you can connect through the same one-click flow. A CRM, an e-commerce backend, some niche dev tool. They connect identically. The difference is they haven't been individually tested by Zo, so the actions can be rougher and the edge cases less predictable. They work. They just don't get the polish the curated apps do.

The practical rule: if a curated app covers your need, use it. If you have to reach into the long tail, expect to verify the output more carefully and read the field where the action might be doing something slightly off. That's where the manual-evaluation guide earns its keep.

## The multi-account thing

If you have two of the same account connected, say a personal Gmail and a work Gmail, Zo can't read your mind about which one you mean. Tell it. "Send this from my work Gmail." "Check the personal calendar." It's one sentence, and it saves you from a draft landing in the wrong outbox. When only one account is connected, you can skip this entirely and Zo just uses it.

## Where keys still come in

OAuth handles the curated apps and the catalog. Some integrations, especially ones you build yourself or wire through a custom skill, still want a real API key. Those don't go through a Connect card. They live as secrets in Settings, where Zo can read them as environment variables without them sitting in plain text in a file. If you find yourself with a service that has no Connect option at all, that's your signal you're in key territory, and the secrets and keys guide covers how to store one safely.

## What to do when a connect stalls

A few honest failure modes worth knowing:

- **The card appears but nothing happens after you click.** The OAuth window may have been blocked by a popup blocker. Allow popups for the Zo tab and click again.
- **You connected but Zo isn't doing anything.** This is the idle-turn trap from up top. Send one more message.
- **You're connected and the action still fails.** For catalog apps, that's the untested-edge reality. For curated ones, it's usually a scope you didn't grant. Reconnect from the Integrations page and approve the full set.

The point is one click and about a minute, then you're back to work. Just remember Zo doesn't resume on its own, and you'll never lose a turn wondering why your inbox summary never showed up.

If this saved you a confused minute staring at a finished OAuth window, the rest of Zo Computer 101 runs the same way: one real workflow at a time, no hand-waving. The plugins and integrations guide goes deeper on what each connection can actually do, and the messaging channels guide covers reaching Zo from outside the web app. They all live at jeffkazzee.zo.space/writing.
