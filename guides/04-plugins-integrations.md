---
title: Plugins, in plain English: handing Zo a key to the apps you already use
id: zo-plugins-integrations
series: Zo Computer 101
category: integrations
kind: explainer
order: 1
date: 2026-06-18
updated: 2026-06-18
excerpt: A plugin is just Zo holding a key to one of your accounts. How connecting works, the curated apps versus the 1000-app catalog, and why a plugin beats the browser every time one exists.
tags: [integrations, plugins, catalog, secrets, gmail, beginners]
related: [zo-browser-explained, plugin-inside-automation]
difficulty: beginner
reading_time: 7
---

A plugin is the least mysterious thing in Zo once you see what it actually is. It is Zo holding a key to one of your accounts. You authorize it once, and from then on Zo can read and write in that app the proper way, through the app's own door, instead of pretending to be you in a browser. Connect Gmail and Zo can read and send your mail directly.

Zo uses a few names for the same family here: plugins, integrations, connected apps. Same idea, an account you let Zo into. This guide is what they are, how to connect one, and the rule for when Zo uses a plugin instead of the browser, because that rule is what makes the whole thing feel fast instead of flaky.

> A plugin is the front door. The browser is climbing through the window. If the front door exists, Zo takes it, and so should you.

## How connecting actually works

You do not paste API keys for the common apps. You click a button. Ask Zo to do something with an app that is not connected yet, and it surfaces a Connect card right in the chat. You click it, a standard authorization window opens, you say yes, and the connection finalizes on its own. Next message, Zo can use it.

Clicking Connect does not wake Zo back up to finish the task. The connection completes, but Zo stays idle until your next message. So the rhythm is: Zo offers the button, you connect, then you come back and say "okay, go." Tell it to proceed and it picks up the thread.

You can also manage everything from the Integrations page in Settings, but the inline button is one click versus several, so let Zo surface it when it can.

## The curated apps versus the big catalog

There are two tiers, and knowing which one you are in saves confusion.

The **curated set** is the apps Zo supports directly and has tested: Gmail, Google Calendar, Notion, Linear, Stripe, X, GitHub, and a couple dozen more. These are the ones with dedicated handling, so they're the reliable everyday workhorses.

Behind that sits the **Pipedream catalog**, over a thousand more apps. CRMs, e-commerce platforms, dev tools, the long tail. If the app you want is not in the curated list, Zo can search the catalog for it, connect it the same way, and run its actions. The tradeoff: catalog apps are not individually tested by Zo, so reliability varies. When a curated app covers your need, prefer it. When it does not, the catalog is there.

You do not have to know which tier an app is in. Ask for what you want, and Zo finds the app, checks if it needs connecting, and tells you.

## The rule: plugin beats browser, every time one exists

This is the single most useful thing to internalize about plugins, and it ties straight back to the browser guide. When a plugin exists for a service, Zo uses the plugin, not the browser. It is faster, it does not depend on a live login session that can expire, and it speaks the app's real data format instead of scraping a page.

So if Gmail is connected, "check my email" goes through the Gmail plugin, clean and fast. The browser is the fallback for the apps that have no plugin: your niche vendor portal, an internal tool, some small SaaS with no catalog entry. Plugin first, browser only when there is no plugin. That order is why some requests are instant and some are slow, and now you know which is which.

## What it looks like in use

Once an app is connected you mostly forget it is a plugin at all. You just talk about the app:

- "Add a task to my Today list in Google Tasks."
- "Draft a reply to the last email from Sarah, don't send it."
- "Pull this week's paid orders from Stripe into a table."
- "Create a Notion page from these meeting notes."

Zo translates that into the app's actual operations. For reading, searching, and organizing, it just does it. For anything that sends, posts, or charges money, the safe default is that Zo drafts and waits for your go, especially with email and social. If you ever want it to send without asking, you tell it so explicitly.

## Multiple accounts, one app

If you have two Gmail accounts connected, you are not stuck. Tell Zo which one: "send this from my work Gmail." It picks the right connection. Same for any app where you have more than one account hooked up.

## The trust line, stated plainly

A plugin is real access to a real account. Connecting Gmail means Zo can send mail as you. Connecting Stripe means it can see your revenue. This is the same trust conversation as the browser, and the same answer applies: only connect what you are comfortable having Zo act on, and lean on the draft-first default for anything destructive or public.

If you want a connected app available but locked down, scope it through a persona. A "reading" persona that can pull from your calendar and inbox but cannot send anything is a safer thing to leave running in an automation than full access. More on personas later in this series.

## The one to connect first

Connect your calendar and your email. Those two unlock the highest-value beginner automation in the whole platform, the morning briefing, and they turn Zo from "a chat" into a thing that knows your day. Connect them, ask Zo to build the briefing, and you'll feel the difference by tomorrow morning.

Zo Computer 101 is a growing library of beginner guides written by a heavy independent user, not a manual. The browser guide is the companion to this one: plugins are the front door, the browser is the window for apps that have no plugin. And once a plugin is connected, the real payoff is putting it inside an automation. Both live in the library at jeffkazzee.zo.space/writing.
