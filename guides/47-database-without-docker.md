---
title: "Run a real database on Zo without Docker"
id: database-without-docker
category: building
kind: how-to
date: 2026-06-18
updated: 2026-06-18
excerpt: You want Postgres or Redis on your Zo, but Docker isn't the path here. Here's how to run a real database as a process-mode service bound to localhost, the way the platform actually wants.
tags: [zo, services, database, postgres, building, beginner]
related: [process-mode-worker, sqlite-on-a-site, zo-hosting-explained]
difficulty: beginner
reading_time: 7
---

You asked Zo for Postgres and your first instinct was to reach for Docker, because that's how every tutorial on the internet starts. On Zo that instinct sends you down a road you don't need. Your Zo is already a Linux sandbox with root, so anything that runs on Linux runs here natively, and a database engine is just a Linux program that listens on a port. You install it, you keep it running, you point your app at it. No container layer in the middle.

> Docker is a way to carry Linux somewhere it isn't. You're already on Linux. You don't need to pack a suitcase to walk across the room.

## First, an honest gut-check: do you even need this?

If you're building a Site and you ask for a database, Zo reaches for SQLite by default, and for most projects that's the right call. SQLite lives as a file next to your code, handles real concurrent reads, and survives restarts without you doing anything. A contact form, a small CRUD app, a personal tracker: SQLite is enough, and the SQLite guide walks through it.

Reach for Postgres or Redis when SQLite genuinely runs out. Heavy concurrent writes. A queue or cache that wants Redis semantics. A schema that leans on Postgres features SQLite doesn't have, like real `JSONB` indexing or `LISTEN/NOTIFY`. If you can't name the specific thing SQLite is failing at, you probably haven't hit the wall yet, and you're about to maintain a database engine for no reason.

Still here? Good. Here's the shape that works.

## Use process mode, bind to localhost

Zo services run in one of three modes, and the difference is whether the thing has a public door:

| Mode | Public endpoint | Use it for |
| --- | --- | --- |
| `http` | yes, at `*.zocomputer.io` | web servers and APIs |
| `tcp` | yes, raw host and port | non-HTTP protocols, game servers |
| `process` | none | databases, workers, bots, anything internal |

A database your own app talks to does not belong on the public internet. It belongs in `process` mode, listening on `127.0.0.1` so only programs inside your Zo can reach it. Two things fall out of that choice for free: there's no public URL for an attacker to find, and process services don't count against your hosted-service limit, so a Postgres running this way is effectively invisible to your quota.

The mode you want to avoid is `tcp` for this. A raw TCP service is always public with no auth in front of it, so exposing Postgres that way drops your database on the open internet behind nothing but its own password.

> Never put a database on a public TCP service unless that database has strong auth turned on and you've thought hard about it. The default move is localhost-only, every time.

## The three steps

**1. Install the engine.** Your sandbox is Debian, so the database comes from `apt`. For Postgres that's the `postgresql` package; for Redis, `redis-server`. Ask Zo to install it and initialize the data directory rather than guessing flags, because the init step (creating the cluster, setting the data path) varies by version and is the part people get wrong. The goal: an engine installed, plus a config that tells it to listen on `127.0.0.1` and nothing else.

**2. Register it as a service, not a terminal command.** This is the step that matters most, and it's the one that's easy to skip. You can start Postgres by hand in a terminal and it'll run fine, until your Zo does its periodic restart to pick up updates and snapshots. That happens on paid plans too. A process you launched yourself does not come back. A registered service does. Ask Zo to register the database with:

- **Mode:** `process`
- **Entrypoint:** the command that runs the server in the foreground (for Postgres, `postgres` pointed at your data directory; for Redis, `redis-server` with your config file)
- **Working directory:** wherever the data and config live, often somewhere under `/home/workspace`
- **No local port:** process mode has no public tunnel, so the port is internal only

Once it's registered, Zo brings it back with the same config every time the sandbox boots. That's the line between something that runs and something that stays running.

**3. Point your app at it over localhost.** Your Site or service connects the way it would to any local database: host `127.0.0.1`, the engine's normal port (`5432` for Postgres, `6379` for Redis), and credentials you keep in the app's environment variables instead of hardcoding them. Both processes live inside the same sandbox, so the connection never leaves your Zo.

## What this gets you, and the one gotcha

You end up with a real Postgres or Redis that auto-restarts, stays off the public internet, and costs nothing against your service count. Clean.

The gotcha to watch: process-mode services have no public URL, which means you can't poke the database from your laptop with a GUI client over the internet. That's the security feature working as intended. When you need to inspect data, do it from inside the Zo (ask Zo to run a query, or open a shell), or stand up a small admin route on a Site that talks to the database over localhost and gate it behind auth.

If you only needed a background job and not a full engine, the process-mode worker guide covers that same registration pattern for scripts and sync loops. And if you're still deciding between Space, Sites, and Services for the whole project, the hosting guide lays out the map before you commit.

 The rest of them live at jeffkazzee.zo.space/writing.
