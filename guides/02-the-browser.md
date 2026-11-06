---
title: Zo has hands: how the built-in browser acts as you on any site
id: zo-browser-explained
series: Zo Computer 101
category: browser
kind: explainer
order: 1
date: 2026-06-18
updated: 2026-06-18
excerpt: Zo runs a real Chromium browser on your server. You sign in once, and it can act as you on any site. How it works, when it fires, and the safety line you should not cross.
tags: [browser, web-search, integrations, beginners]
related: [zo-plugins-integrations, how-zo-memory-works]
difficulty: beginner
reading_time: 7
---
Most of what people imagine when they hear "AI agent that browses the web" is wrong, and the wrong version is more impressive than the real one. The real one is better because it is honest about what it does. Zo runs an actual Chromium browser on your personal server. You sign into sites in that browser once. After that, Zo can do anything on those sites that you could do with the same login. Read your feed. Pull a number out of a dashboard. Post a draft. Place an order.

That last sentence should make you slightly nervous, and it should. We will get to the safety line. First, the mechanic, because once you understand when the browser fires versus when Zo uses something lighter, you stop being confused about why some requests are instant and some take twenty seconds.

> If you could share a URL with someone logged out and they'd see the same thing, Zo won't use the browser. The browser is for everything behind your sign-in.

## How to turn it on

Go to Settings, Integrations, and click Open Zo's browser. A real browser pops up in its own tab. Navigate to a site, sign in like you normally would, and close it. The session sticks, the same way it sticks in your own browser. You do this once per site.

Sites you have signed into show up in Settings as authenticated sites. That list is doing double duty: it is your session store, and it is also how Zo knows which sites it is allowed to act on as you. When you say "check my Substack stats," Zo checks that list, sees it has a session, and goes.

## The hierarchy: why the browser is the last resort

This is the part that clears up the confusion. Zo has several ways to reach the web, and the browser is the heaviest one. It loads a real page, runs the JavaScript, and uses your live session. That is expensive compared to the alternatives, so Zo only reaches for it when nothing lighter will do.

Roughly the order it picks from:

| Zo reaches for | When |
| --- | --- |
| An integration | The service has one (Gmail, Linear, Notion, Stripe, and the rest) |
| A skill | The work is a packaged, known workflow |
| A CLI or API | The service ships a tool Zo can run or an endpoint it can call |
| A web tool | The page is publicly readable (read a webpage, web search) |
| The browser | None of the above exist for the site you're using |

The practical version: if Gmail is connected, Zo uses the Gmail integration, not the browser, to read your mail. Faster, cleaner, no session risk. The browser is the universal fallback for the long tail. Niche SaaS, internal tools, a vendor admin panel, a customer portal, anything too small or too private to have its own integration. That long tail is the entire reason the browser exists.

## When it fires on its own

You do not have to say the word "browser." Zo picks the browser tool by itself when a request points at a site it is signed into. Ask it to pull last month's numbers from a dashboard it has a session for, and it just opens the browser. If you want to be explicit you can say "in the browser" or "open Substack and," but you rarely need to.

## When Zo gets stuck, and what unblocks it

Live sites are hostile to automation. They change layout, throw popups, and log you out at the worst time. A few things that reliably unblock Zo:

| Symptom | What to do |
| --- | --- |
| Familiar page, Zo can't find the button | Ask it to screenshot and describe what it sees, then point it at the right spot |
| Logged out mid-task | Open the browser, sign back in, tell Zo to retry |
| 2FA prompt appears | Complete it in the browser, tell Zo to keep going, it picks up where it left off |
| Site looks different than yours | Zo's browser is a separate session from a different IP, so some sites serve a different layout. Have Zo describe what it sees before you debug |

The screenshot move is the one to remember. When the browser is misbehaving, "take a screenshot and tell me what you see" turns a black box into something you can actually direct.

## The safety line you should not cross casually

Here is the warning, stated plainly because it matters more than any tip above. The browser keeps live cookies for every site you sign into. Anything Zo can do as you in a chat, it can also do as you on those sites. Read your messages. Send messages. Buy things. Change settings. Delete things.

So the rule is simple: only sign into accounts you are comfortable having Zo act on. Your bank, in a browser an agent drives, is a decision, not a default. Think about it before you do it.

If you want Zo to read a site but never take actions on it, the clean answer is a persona with a limited tool set. Give a "research" persona browse-and-read access and nothing that can post or send, and now it can pull data out of a dashboard but cannot fat-finger a tweet from your account. That is the right tool for "look but don't touch," and it is worth setting up before you hand over anything sensitive.

## The one thing to internalize

The browser is not Zo being clever on the open web. It is Zo using your logins, on your server, to do the tab-fiddling you would otherwise do yourself. That framing tells you both when it is the right tool (the long tail behind a sign-in) and when to be careful (it has your cookies). Reach for an integration when one exists. Reach for the browser when you would have just opened the tab yourself.

Zo Computer 101 is a growing library of beginner guides I write as someone who runs this thing daily. If the browser is Zo's hands, its memory is what tells those hands what to do, so the memory guide pairs well with this one. Plugins are the next thing to read: they're the faster, safer way to reach the apps that have one. The whole library lives at jeffkazzee.zo.space/writing.