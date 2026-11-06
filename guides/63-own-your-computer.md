---
title: "The case for a computer you actually own"
id: own-your-computer
category: opinion
kind: opinion
date: 2026-06-18
updated: 2026-06-18
excerpt: Most of your digital life is rented. Your files, your tools, your AI, all sitting in someone else's app, gone the day they change the terms. Here's the case for owning the computer instead.
tags: [zo, ownership, opinion, files, custody]
related: [files-on-your-server, what-zo-actually-is, get-your-work-out-of-zo]
difficulty: beginner
reading_time: 7
---

Count how much of your digital life you actually own. The docs are in someone's cloud, the automations live in a SaaS you pay monthly, the AI you lean on runs behind an API you don't control and can't see. You're renting all of it, and a rented thing can change its terms, triple its price, or disappear on a Tuesday with a polite email. You found out the rules the day they changed on you.

That's the default now, and most people never chose it. It accreted. One signup at a time, until your work lived in forty places and you held the keys to none of them.

> Renting feels cheaper until the day you need to leave and find out the door only opens from their side.

## What renting actually costs

The monthly fee is the part you can see. The real cost shows up at the exits.

A SaaS tool gets acquired, the new owner sunsets the feature you depended on, and your workflow is gone with thirty days notice. A model provider deprecates the version you tuned all your prompts against, and now everything reads slightly wrong. A platform decides your use case violates a policy it wrote last week, and your account is locked while a support queue decides your fate. None of these are hypotheticals. They are the normal weather of building on land you don't own.

The pattern underneath: when the thing you depend on lives in someone else's account, their incentives quietly become yours. They optimize for retention, for lock-in, for the export that's technically possible and practically miserable. You optimize for getting your work done. Those two goals diverge the moment you try to leave.

## Owning the computer flips the default

A personal server changes the question from "can I get my stuff out" to "where do I want to put it next." Here's the difference in concrete terms.

| The rented default | Owning the computer |
| --- | --- |
| Files in a proprietary format inside an app | Files in open formats (markdown, CSV, plain text) on a machine you control |
| AI behind one vendor's API, take it or leave it | Bring your own model key, swap providers when one gets worse |
| Work trapped in the platform | Sync to your laptop, push to GitHub, publish or export any time |
| Their terms, their pricing, their roadmap | Root access, your files, install anything Linux runs |

This is what Zo is built around, and it's the reason I use it instead of stitching together six subscriptions. The files sit in a real workspace I can sync to my laptop through the desktop app, so the same markdown lives in two places I control. The AI isn't locked to one company. Under Settings, AI, Providers, you open Bring Your Own Key and drop in your own OpenAI, Anthropic, or Groq key, then pick the model under Settings, AI, Models, so when a provider ships a worse version you point at a different one and keep moving. When I want something gone, I publish a folder to `zo.pub`, push code to GitHub, or just copy the directory. No export ticket. No begging.

## The principle, said plainly

Own the computer, don't rent the app. 

A computer you own treats your work as yours by default. Open formats mean any other program can read your files in ten years, after whatever I'm using today is dead. A swappable model means no one AI company gets to be a single point of failure for how you think and write. Portable work means the platform has to earn your loyalty every month instead of trapping it, and that's a healthier relationship to be in with anything you depend on.

There's an anti-authoritarian read on this that I won't pretend isn't part of why I care. The more of your life runs through systems you can't inspect and can't leave, the more power those systems have over you for free. Custody is leverage. Owning your tools is a small, boring, daily way of keeping it.

## The honest tradeoff

Owning more means carrying more. I'm not going to sell you a free lunch.

1. **Backups are on you.** A platform that holds your stuff also, usually, keeps copies of it. When you take custody, you take the responsibility to not lose it. Sync to a second machine. Push the important work somewhere off the server. Don't keep one copy of anything you'd cry over.
2. **More rope, more ways to trip.** Root access and a real Linux box mean you can break things a locked-down app would never let you touch. That freedom is the point, and it's also a sharp edge.
3. **It is not magic.** A personal server doesn't make the AI smarter or the work write itself. It changes who's in charge of the work, not how hard the work is.

I think that trade is worth it, and it isn't close. The cost of ownership is a little more attention. The cost of renting is finding out, at the worst possible moment, that you were a guest the whole time.

If this argument landed, the rest of Zo Computer 101 makes the practical case: the guide on keeping your files on your own server walks through where everything actually lives, the what-Zo-actually-is guide lays out the whole machine, and the guide on getting your work out of Zo proves the door opens from your side. They all live at jeffkazzee.zo.space/writing.
