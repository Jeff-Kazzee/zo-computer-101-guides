---
title: "Run a background worker that never needs a public URL"
id: process-mode-worker
category: building
kind: how-to
date: 2026-06-18
updated: 2026-06-18
excerpt: Not everything you run should be a website. A sync loop, a bot, a scheduler: these want to run quietly in the background. That's process mode, and it doesn't count against your service limit.
tags: [zo, services, process-mode, building, beginner]
related: [database-without-docker, first-zo-site, zo-hosting-explained]
difficulty: beginner
reading_time: 6
---

You wrote a script that polls an API every ten minutes and writes the result to a file. It runs fine in the terminal. Then your Zo restarts overnight to pull in an update, your terminal process dies with it, and the file quietly stops changing until you notice three days later that the data is stale. That gap between "it runs" and "it stays running" is the entire reason process mode exists, and most people don't find it until something breaks.

> A script you start by hand is a script that ends the next time your Zo reboots. Registering it is how you stop babysitting.

## The thing nobody tells you about hand-started processes

Your Zo restarts periodically to pick up updates and snapshots. This happens on paid plans too; restarts aren't a free-tier-only thing. So a `nohup python3 worker.py &` you fired off in the terminal will run beautifully right up until the next reboot, and then it's gone, with no log of why and no automatic comeback.

A registered service fixes that. When you register a process, Zo brings it back up with the same config every time your Zo starts. If it crashes mid-run, Zo restarts it. When your Zo reboots for an update, the worker comes back up with the same config. You stop being the supervisor.

## Three modes, and why most workers want the quiet one

A service is just any long-running program on your Zo. Every one runs in one of three modes, and the mode decides whether the outside world can reach it.

| Mode | Public endpoint? | Use it for |
| --- | --- | --- |
| `http` | Yes, public by default at `*.zocomputer.io` (can be set private) | APIs, web servers, anything browsers hit |
| `tcp` | Always public, host and port, no auth in front | game servers, sockets, MQTT, custom protocols |
| `process` | None | workers, schedulers, bots, sync loops, internal-only localhost services |

Here's the part that matters for a background job: it doesn't need a URL at all. A polling worker talks to an outside API and writes to your files. A Discord bot connects out, never in. A scheduler wakes up, does work, sleeps. Nobody on the internet should be able to hit any of them. Giving that kind of job an `http` endpoint is handing out a front door to a room with nothing in it.

Two concrete reasons to reach for `process`:

1. **No exposure.** There's no public URL to leak, scan, or get hammered by a bot. The job lives entirely inside your Zo's sandbox.
2. **It's free against your limit.** Process services don't count toward your hosted-service limit. Your `http` sites and services do. So a Postgres bound to `127.0.0.1`, a sync loop, and a Telegram bot can all run as process services without eating the slots you want for actual websites.

## Registering one

The fast path is to just ask Zo. Tell it what you want to run and how often, something like "register my `worker.ts` as a background process service that runs continuously," and it'll set up the config. You can also open the **Sites** page, go to the **Services** tab, and do it by hand. Either way, a process service needs only a few settings:

| Setting | What to put |
| --- | --- |
| Label | A unique lowercase-and-hyphens name, e.g. `feed-sync-worker` |
| Mode | `process` |
| Entrypoint | The command that starts it, e.g. `bun run worker.ts` or `python3 worker.py` |
| Working directory | Where the command runs, defaults to `/home/workspace` |
| Environment variables | Any config or keys the worker needs |

Notice what's missing: there's no local port. Ports are required for `http` and `tcp` because traffic has to land somewhere. A process service has no inbound traffic, so it has nothing to listen on. If your worker still needs to bind a port for an internal reason, say a local server on `127.0.0.1` that another service connects to, you set that up inside your own code or config. Zo isn't routing anything to it.

One honest caveat about the entrypoint: it has to be a long-running command. Process mode keeps a process alive, so your script needs to actually stay up. A loop with a `sleep`, a bot that holds an open connection, a scheduler that blocks. A script that runs once and exits will be treated as a crash and restarted in a tight loop, which is its own mess. If your job is genuinely "do this every morning at 8" and then quit, that's an automation, not a process service, and you'd point it at a schedule instead.

## A worker shaped right

The mental model for a process worker is a program that owns its own clock. Roughly:

```
loop forever:
  do the work
  sleep until next time
```

So a feed poller written as a Bun script with a `setInterval` or a `while (true)` plus an `await Bun.sleep(...)` is exactly the shape process mode wants. You register it once, set the entrypoint to `bun run worker.ts`, leave the working directory as your project folder, drop your API key into env vars, and walk away. It runs, it writes to your files, it survives reboots, and it never shows up on the public internet.

If your worker also needs a database it can talk to without exposing it, that's the same pattern again: a Postgres or Redis registered as its own process service on localhost. The database guide walks through that setup without Docker. And if you're still deciding whether a thing should be a Space page, a Site, a Service, or a folder on zo.pub, the hosting overview lays out the whole map before you commit.

Process mode is the unglamorous primitive that makes the rest of your Zo dependable. There's no public URL and no auth to worry about, and it doesn't burn one of your hosted-service slots. The rest of Zo Computer 101 is written the same way, specific and tested, over at jeffkazzee.zo.space/writing.
