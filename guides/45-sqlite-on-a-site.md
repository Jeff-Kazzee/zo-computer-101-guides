---
title: "Save form responses to a database that sits next to your files"
id: sqlite-on-a-site
category: building
kind: how-to
date: 2026-06-18
updated: 2026-06-18
excerpt: A contact form is useless if the submissions vanish. On a Zo Site, they land in a SQLite database that lives in your own folder, no external service, no monthly fee. Here's how.
tags: [zo, sites, sqlite, database, building, beginner]
related: [first-zo-site, space-to-site, zo-hosting-explained]
difficulty: beginner
reading_time: 6
---

Most contact forms you build in a weekend have the same silent bug: someone fills it out, hits submit, sees a thank-you message, and the data goes nowhere. The form looks finished. It isn't, because there's no table on the other end catching what people typed. On a Zo Site you skip the usual fix, which is wiring up a hosted database and paying a monthly fee for the privilege. The submissions land in a SQLite file that lives in the same folder as the rest of your project.

> The database is a file in your folder, not a service you rent by the month. That one fact changes what you can do with it.

## What a Zo Site actually is

A Site is a real web project that lives as a folder on your Zo. It runs on Hono and Bun. Hono handles the routes, Bun runs the server and ships with a SQLite driver built into the runtime, so there's nothing to install for the database to work. When you ask Zo for a Site that needs to store data, it reaches for SQLite by default. The whole database is one file, something like `data.db`, sitting next to your `server.ts` and your pages.

You can point a Site at an external database instead. Convex and Supabase both work if you have a reason to use them, like sharing one dataset across several apps. For a form on a single Site, that's extra moving parts you don't need. SQLite is the default for one reason: it's already there.

## Ask Zo to build the form

You don't write the SQL or the route by hand unless you want to. Describe what you want in plain language:

> "Add a contact form to my Site with name, email, and message fields. Save every submission to SQLite, and give me a page where I can read them."

Zo writes the form component, the route that handles the POST, and the database code that inserts the row. Here's what shows up in your project folder afterward:

| What | Where it lives | What it does |
| --- | --- | --- |
| The form | a page route | renders the inputs, posts to your API |
| The handler | an API route in `server.ts` | validates and inserts the submission |
| The table | inside `data.db` | one row per submission, with a timestamp |

The insert itself is a few lines of Bun's SQLite API. A `CREATE TABLE IF NOT EXISTS` so the table exists on first run, then an `INSERT` on every POST. You can read it, but you don't have to touch it to get a working form.

## See the data

A form you can't inspect is a form you don't trust yet. Two ways to look at what's coming in:

1. **Open the file in Zo.** The `.db` file shows up in your workspace like any other file. Zo has a built-in SQLite explorer, so you click the file and read the rows in a table view. You can change the shape there too, add a column, fix a typo in a field name, without leaving the app.
2. **Ask Zo.** "Show me the last ten contact form submissions" runs the query and hands you the results in chat. Faster than writing `SELECT * FROM submissions ORDER BY created_at DESC LIMIT 10` yourself, though you can do that too if you like the keyboard.

Either way you're reading your own file on your own server. No dashboard login, no API token, no waiting on a third party's status page when it goes down at the wrong moment.

## Why "just a file" beats a hosted database for this

The instinct from working with normal web stacks is that a real database has to be a separate hosted thing with its own credentials. For a Site collecting form responses, that instinct costs you more than it gives. A few things you get for free when the database is a file in the project folder:

- **It syncs.** The `.db` file moves with the rest of your workspace. If you run the Zo desktop app's folder sync, the database comes along with your code, same as any other file.
- **It backs up with the project.** Copy the folder, you copied the data. There's no separate export step, no "remember to also dump the database" footgun.
- **It moves when the project moves.** Hand the folder to a future version of yourself six months from now and the submissions are still in it. Nothing to reconnect.
- **It scales fine for this.** SQLite handles a contact form, a waitlist, a small order log without breaking a sweat. You'd have to get genuinely popular before a single file becomes the bottleneck, and that's a good problem to have later.

The tradeoff is real and worth naming. SQLite is one file, so it's built for one writer at a time, not a fleet of servers hammering the same table. A contact form on a personal Site is exactly the workload it's good at. A high-traffic multi-region app is where you'd graduate to Postgres or one of the hosted options. Match the tool to the job and SQLite wins the small jobs easily.

## Where to start

If you don't have a Site yet, build one first and come back. The first Zo Site guide walks through spinning one up from a single sentence. If you already have something running on your `zo.space` and want to grow it into a full project with a database, the Space to Site guide covers that move. And if you're still deciding whether you even want a Site versus a Space, the hosting guide lays out which one fits.

Once the Site exists, adding the form is the easy part. Ask Zo for the form, check the rows came through, ship.

Real files, real code, nothing you have to rent. That's every guide in Zo Computer 101, and the rest of them live at jeffkazzee.zo.space/writing.
