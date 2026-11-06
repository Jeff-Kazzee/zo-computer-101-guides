---
title: "Hosting decision card: Space vs Site vs Service vs zo.pub in one table"
id: hosting-decision-card
category: reference
kind: reference
date: 2026-06-18
updated: 2026-06-18
excerpt: Four ways to put something online from your Zo, and the names don't tell you which is which. This is the one-screen card: what each is for, the URL it gives you, and the pick rule.
tags: [zo, hosting, space, sites, services, zo-pub, reference]
related: [zo-hosting-explained, first-zo-site, zo-pub-sharing]
difficulty: beginner
reading_time: 4
---

Your Zo is a personal server, so there are four different ways to put something online from it, and the names give you almost no help deciding which one you want. Space, Sites, Services, zo.pub. Pick wrong and you either over-build a tip calculator into a full project or try to run a database on a thing that was meant to host a folder of PDFs. This is the card I keep open so I stop guessing.

> The question is never "how do I host this." It's "which of the four am I actually describing," because the right answer is usually obvious once you name the thing.

## The master table

| Option | What it's for | URL pattern | Default visibility | Pick it when |
| --- | --- | --- | --- | --- |
| **Space** | One page, one API, or one small widget, with zero project setup | `yourhandle.zo.space` | Pages private, you can flip them public. APIs always public. Assets always public | You have one small thing in mind and don't want to think about folders or deploys |
| **Sites** | A full website project that lives as a folder you own | `sitename-yourhandle.zocomputer.io` | Private until you click Publish | You'll keep building on it, or it needs your files, a database, or your AI |
| **Services** | Any long-running program: server, database, bot, worker | `*.zocomputer.io` public, `*.zo.computer` private | Depends on mode (see below) | You care about the runtime itself, not only the code |
| **zo.pub** | Share a folder of files behind a link | `zo.pub/<your-handle>/...` | Fully public, no private mode at all | Someone just needs to download files |

That table answers most of it. The detail that trips people up lives in two places: what Sites and Services actually share, and the three Service modes.

## Sites and Services are the same family

A Site is a full project you own, with a private dev preview while you build it. It's a real project built on Hono and Bun, it lives in a folder on your Zo, and it can read and write files in your workspace. Ask for a database and it uses SQLite by default, sitting right next to your other files. While you're building, only you can open the URL. The moment you hit **Publish**, the Site becomes a public Service at `sitename-yourhandle.zocomputer.io`.

So the real fork is whether you want the scaffolding. Want a website project that integrates with your workspace and you keep evolving? That's a Site. Want raw control over a process that may not even be a website? That's a Service.

## The three Service modes

This is the part the word "service" hides, and getting it wrong is how you accidentally expose a database to the open internet.

| Mode | Public? | URL | Use it for |
| --- | --- | --- | --- |
| **`http`** | Public by default, can be set private | `*.zocomputer.io`, or `*.zo.computer` when private | Any HTTP server, API, or website |
| **`tcp`** | Always public, no auth in front of it | Direct Tunnel host and port | Non-HTTP protocols: game server, MQTT broker, custom socket |
| **`process`** | No public endpoint at all | None | Workers, schedulers, bots, sync loops, an internal Postgres bound to `127.0.0.1` |

Two things worth memorizing. TCP is always public with nothing in front of it, so whatever you run there handles its own auth or it doesn't get exposed. And `process` mode doesn't count toward your hosted-service limit, so reach for it any time a public endpoint isn't needed. A database your other services talk to should be a `process` on localhost, never a TCP service.

Why register a service at all instead of starting it in a terminal? A registered Service is supervised, so it comes back after a crash or a reboot. A process you start by hand does not. A process you launched by hand won't come back. A registered service does, with the same config, every time.

## The fast decision rule

Read these in order and stop at the first yes.

1. **Is it a folder of files someone just needs to download?** zo.pub. No account needed on their end, browsable listing, downloadable as a zip or tar. Photos, data exports, a portfolio PDF, a static report.
2. **Is it one page, one API, or one small widget, and you don't want a project?** Space. Ask Zo to make it and it's live at `yourhandle.zo.space`.
3. **Is it a website project you'll keep building, or one that needs your files, a database, or your AI?** Sites.
4. **Is it a long-running custom process, a database, a bot, or anything the above don't cover?** Services, then choose the mode from the table.

## The traps

A few wrong turns I've watched happen, including to me:

- **Trying to run an app on zo.pub.** zo.pub shares files, full stop. No code, no logins, no per-user logic. If you need any of that, it's Sites or Services.
- **Exposing a database over TCP.** Don't. Bind it to localhost in `process` mode and let your HTTP service connect to it internally.
- **Building a Site when you wanted a Space.** If the whole thing is a single calculator or a webhook URL, the project folder is overhead you'll never touch again.
- **Forgetting Space pages are private by default.** You build a landing page, send the link, and the other person sees nothing because they aren't you. Flip it public first.

If you want a branded URL on top of any public Site or Service, attach a custom domain. That's a separate move and it's covered in its own guide, the custom domains card.

Still not sure which of the four you're describing? Describe the thing to Zo in plain language and it'll tell you. For the long version of this with the reasoning behind each pick, read the Zo hosting explainer, and the rest of Zo Computer 101 lives at jeffkazzee.zo.space/writing.
