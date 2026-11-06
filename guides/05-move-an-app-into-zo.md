---
title: That app rotting on your laptop? Put it on your own server today.
id: move-an-app-into-zo
series: Zo Computer 101
category: building
kind: how-to
order: 1
date: 2026-06-18
updated: 2026-06-18
excerpt: You have a project on your laptop. The three honest ways to get it onto your Zo and keep it running, the one that fits most people, and the question that tells you which to pick.
tags: [building, sites, services, github, sqlite, beginners]
related: [zo-hosting-explained, get-your-work-out-of-zo]
difficulty: beginner
reading_time: 8
---

You already built something. A little web app, a script that does a job, a project that has been sitting on your laptop because deploying it always felt like more work than building it. Zo is a personal server, so the obvious question is: can I just run this here? Yes. There are three honest ways to do it, and the only real decision is which one fits what you built.

Skip the hard part first: you do not need to know "deployment." You move the files onto your Zo, tell Zo what the thing is and how it starts, and it gets it running and keeps it running.

The whole decision is one fork. A single page or tiny widget goes to **Space.** An app with its own files and dependencies goes to a **Site.** A bot, API, worker, or database goes to a **Service.** The rest of this guide is getting your files in, then those three paths in detail.

> A process you start by hand in the terminal dies the next time your Zo restarts. The whole point of doing this right is the difference between something that runs once and something that stays running.

## Step one, always: get the files onto your Zo

Before any of the three paths, your code has to live on your Zo. Three ways in, pick whatever is least friction for you:

- **GitHub.** If your project is already in a repo, connect GitHub and clone it straight onto your Zo. This is the cleanest path and the one I'd reach for. (The next guide covers the GitHub round-trip in full.)
- **Desktop sync.** The Zo desktop app can sync a folder on your computer to your Zo workspace. Add the folder, and your project shows up on your Zo, staying in sync both ways. Good if you want to keep editing locally.
- **Drag and drop.** For a small project with no repo, just upload the folder into your workspace. Done.

Once the files are there, you choose a path based on one question: what kind of thing did you build?

## Path 1: it's a website or web app, and you want to own the files

Use a **Site.** If what you built is a web project and you want it to live as a folder you own and keep editing, this is the fit. Get the files into your workspace, then tell Zo: "turn this folder into a Zo Site." Zo wires it up to run on your server. While you develop, the site is private, only visible to you signed in. When it's ready, hit Publish and it becomes public at `sitename-yourhandle.zocomputer.io`.

The reason Sites are the sweet spot for most brought-in apps: because the site runs on your server, it can reach the rest of your workspace. It can read your files, write to a database sitting next to your other data, and use your AI. Your laptop app was an island. The same app on a Zo Site is wired into everything else you keep there.

One caution: your project will have its own dependencies, and Zo handles installing them as a Site. Tell it the framework and how the thing starts ("it's a Vite React app, runs with npm run dev") so it sets up the build correctly the first time.

## Path 2: it's a server, a bot, a worker, or a database

Use a **Service.** If what you built is not a tidy website but a long-running program, a custom API server, a Discord bot, a script that loops and syncs something, a database, that is a Service. You give Zo three things: the command that starts it (the entrypoint, like `python3 app.py` or `bun run start`), the folder it runs in, and a port if it serves web traffic. Zo registers it and keeps it alive across restarts.

Services have three modes, and picking the right one matters:

- Your app serves a website or API: **http** mode, public or private.
- It needs a raw, non-web port (a game server, a socket protocol): **tcp** mode.
- It runs in the background with nothing to expose, a worker or a bot or a localhost-only database: **process** mode. Bonus, process services don't count against your service limit.

If you're stuck, describe what it does in one sentence and let Zo choose the mode.

## Path 3: it's a one-off page or a tiny tool

Use **Space.** If what you brought in is really just a single page or a small widget, you do not need a whole project. Ask Zo to make it a Space route and it lives at `yourhandle.zo.space` with zero setup. This is the right call only when the thing is genuinely small. The moment it has multiple files and its own dependencies, it wanted to be a Site.

## The two things that break imports

Two things break brought-in apps more than anything else.

**Dependencies.** Your app expects certain packages installed. On a Site or Service, Zo installs them, but it needs to know your project's setup. If something fails to start, the error is almost always a missing dependency or a wrong start command. Paste the error to Zo and it fixes it; that loop is faster than guessing.

**Secrets.** If your app uses API keys or a database password, those do not travel safely inside the code, and they should not. Put them in Settings under Advanced as secrets, and Zo reads them as environment variables the same way your app expects. Never paste a live key into a file you'll publish.

## The pick, one more time

- Web app you'll keep editing and own: **Site.**
- A server, bot, worker, or database: **Service** (http / tcp / process).
- A single page or tiny tool: **Space.**

Get the files in, answer "what kind of thing is this," pick the path, hand Zo the start command, and you have taken something off your laptop and put it on a server that keeps it running. That is the part that used to be a weekend. Now it's a conversation.

Zo Computer 101 is a growing library of beginner guides for people who build. If you haven't sorted out where things should live yet, read the hosting guide first, it's the decision rule behind this whole piece. And when you want a copy of your work off your Zo, the get-your-work-out guide covers the round-trip. Both are in the library at jeffkazzee.zo.space/writing.
