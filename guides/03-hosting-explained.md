---
title: Four ways to put something online from your Zo, and how to pick in ten seconds
id: zo-hosting-explained
series: Zo Computer 101
category: hosting
kind: explainer
order: 1
date: 2026-06-18
updated: 2026-06-18
excerpt: Space, Sites, Services, zo.pub. The names don't tell you which is which. Here's the decision rule, the URL each one gives you, and the mistake that wastes an afternoon.
tags: [hosting, space, sites, services, zo-pub, custom-domain, beginners]
related: [move-an-app-into-zo, get-your-work-out-of-zo]
difficulty: beginner
reading_time: 8
---

Your Zo is a personal server, which means putting something online from it is not one button. It is four different things called Space, Sites, Services, and zo.pub, and the names do a bad job of telling you which is which. New users pick the wrong one, build halfway in, and then have to redo it. This guide is the decision rule so you pick right the first time.

The whole thing fits in one table, and then the rest is knowing why.

| You want to | Use | URL you get |
|---|---|---|
| A page, an API, or a small widget at a stable address | Space | `yourhandle.zo.space` |
| A full website project that lives in a folder | Sites | `sitename-yourhandle.zocomputer.io` |
| A long-running program: server, database, bot, worker | Services | `*.zocomputer.io` public, `*.zo.computer` private |
| Share a folder of files with a link | zo.pub | `zo.pub/yourhandle/...` |

> The fastest way to waste an afternoon on Zo is to start building a multi-page project as Space routes. Space is for one small thing. The moment it's a project, it wants to be a Site.

## Space: one small thing, no setup

Every Zo user gets one domain at `yourhandle.zo.space`, free, already live. Space is for focused, single creations. A landing page. A tip calculator. A webhook endpoint that catches data from somewhere else. A little React widget. There is no project to set up, no folder, no framework choice. You ask Zo to "make my zo.space home page a personal landing page" and it exists.

Two facts about Space that trip people up. Pages are private by default, meaning only you see them when signed in, but you can flip a page public. APIs are always public at the network level, so if you put a secret in an API route, protect it with a token. And uploaded assets, images and files, are always public.

Reach for Space when you have exactly one small thing in mind and you do not want to think about folders or deploys. The instant something is going to grow into a real project with its own dependencies, stop, and use a Site instead.

## Sites: a real project in a folder you own

A Site is a full website project that lives as a folder on your Zo. It runs on Hono and Bun, and if you ask for a database it uses SQLite by default. The thing that makes Sites different from Space is ownership and reach: the source files are yours, in your workspace, and because the site lives on your server it can read and write your files, save form responses to a database sitting next to your other data, and pull in any folder you point it at.

Sites are private by default. You, signed into your Zo, are the only one who can open the dev URL. When you hit Publish, the site becomes a public service at `sitename-yourhandle.zocomputer.io`. That two-step is on purpose: you develop in private, then publish when it is ready, and the published version keeps running even when you are not actively developing.

Reach for Sites when you want a project you will keep evolving, when you want to own the source files directly, or when the thing needs your files, your AI, or a database behind it.

## Services: anything that runs

A Service is the most general option: any long-running program on your Zo. A custom server. A database engine. A Discord bot. A worker that syncs something every few minutes. If it listens on a port or runs in the background, it is a Service. You give it a port, an entrypoint, and a working directory, and it runs.

Services have three modes, and knowing them saves confusion:

- **http** is a web service. Public by default at `*.zocomputer.io` with no auth, or private at `*.zo.computer` requiring your sign-in.
- **tcp** is a non-HTTP service at a host and port. Always public. This is your "I need a raw port" option, like a database you connect to from elsewhere.
- **process** is a supervised background program with no public endpoint at all. Workers, schedulers, bots, or an internal service bound to localhost like a Postgres on `127.0.0.1`. Process services do not count against your hosted-service limit, which is a nice detail when you are running a few background helpers.

Reach for Services when you care about the runtime, not just the code. A custom server, a real database engine, a long-running worker, anything Sites does not cover.

## zo.pub: a folder, shared, done

`zo.pub/yourhandle` is your public namespace for sharing files. Ask Zo to publish a folder and you get a link anyone can open with no Zo account. They land on a clean listing, browse the folder, click any file to view or download, and can grab the whole thing as a zip.

The line to remember: zo.pub is for sharing, not for running. There is no private mode and no password. Everything you publish there is fully public. Photos, data exports, a portfolio PDF, a static report, anything you would otherwise email as a download link. If it needs code, auth, or per-user logic, that is a Site or a Service, not zo.pub.

## The decision rule, compressed

- One page, one API, one small widget: Space.
- A website project you'll keep building: Sites.
- A custom process, a database, anything that just runs: Services.
- A folder of files for someone to download: zo.pub.

Want a branded URL on top of a public site or service? Attach a custom domain to it. That works on any public Site or Service.

## The mistake to avoid

The single most common wrong turn is building a real multi-page project as a pile of Space routes because Space was the first thing you found. Space routes are great for the one-off. They are not a project structure. If you catch yourself making your fourth or fifth related Space route, you wanted a Site three routes ago. Tell Zo to export your Space into a Site, or start one fresh, and you get a real folder you own with room to grow.

Pick by the table. The names lie a little; the table does not.

Zo Computer 101 is a growing library of beginner guides for people who'd rather build than read a manual. Once you've picked where something lives, the natural next reads are getting an app you already built onto your Zo, and getting your work back out to your laptop or GitHub. The whole library lives at jeffkazzee.zo.space/writing.
