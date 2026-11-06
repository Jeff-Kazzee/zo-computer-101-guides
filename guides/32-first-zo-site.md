---
title: "Your first Zo Site: a real project in a folder you own"
id: first-zo-site
category: hosting
kind: how-to
date: 2026-06-18
updated: 2026-06-18
excerpt: A Space page is one file. A Site is a whole project in a folder on your server, with its own dependencies and a database if you want one. Here's how to make your first one and when it beats a Space.
tags: [zo, sites, hosting, beginner, web, sqlite]
related: [first-space-page, space-to-site, zo-hosting-explained]
difficulty: beginner
reading_time: 7
---

A Space page is great until the day you want a second page, a database, and a dependency that Space won't let you install. That's the wall. A Zo Site is what's on the other side of it: a full website project living as a real folder on your server, with its own files, its own packages, and a SQLite database sitting right next to your workspace data if you ask for one. The good part is you still don't have to write any of it. Zo does. You just have to know when to reach for a Site instead of a Space, and what the workflow looks like.

> A Space is a page you put on the internet. A Site is a project you keep building, and it happens to be on the internet.

## What a Site actually is

A Site is a folder on your Zo, built on [Hono](https://hono.dev) and [Bun](https://bun.sh). When you ask Zo for a database, it reaches for SQLite by default and drops the file in your project. That folder is yours. You can open it in Files, read every line Zo wrote, edit it, and add your own.

The thing that makes a Site different from anything you'd deploy on Vercel or Netlify is where it lives. It runs on your personal server, in the same workspace as your files. So the site can read and write files in your workspace, save form responses to a database next to your other data, and pull in any folder you mention while you're chatting with Zo. A contact form that writes straight to a SQLite table you can query later. A dashboard that reads a CSV you already have sitting in `Documents/`. None of that needs an external service or an API key.

Sites are private by default. While you're signed in to your Zo, you get a dev URL only you can open. Nobody else sees it until you decide they should.

## Make your first one

Two ways in. Both end up in the same place.

1. Open the **Sites** page and hit **Create site**. A new folder shows up in your Files with a lightning icon on it, which is how you tell a Site folder apart from a normal one.
2. Or skip the menu and ask Zo in chat: "build me a Site for a one-page portfolio with a contact form." It scaffolds the folder, writes the code, and starts the dev server.

I lean on the second way almost every time. Describing what I want in a sentence is faster than clicking through anything, and Zo makes the same project either way.

Once it exists, the dev server runs automatically and the site shows up in a preview iframe right there in the app. You don't refresh anything or run a build by hand. Change a line, the preview updates.

## The loop that matters

The actual rhythm of building a Site is short and you'll repeat it a hundred times:

| Step | What you do |
| ---- | ----------- |
| Create | Ask Zo, or hit Create site |
| Preview | Watch it render in the iframe |
| Change | "Make the header dark and add an about section" |
| Repeat | Keep refining until it's right |
| Publish | When you're ready for the world |

The change step is where a Site earns its keep. You're not editing one file and hoping. You're describing what's wrong and watching Zo fix it across however many files the change touches. "The form submits but I never see the responses" turns into Zo wiring a SQLite table and a route to read it. You see the result in the iframe before anyone else ever loads the page.

## Publishing

When the dev preview looks right, click **Publish**. The Site becomes a public service at `sitename-yourhandle.zocomputer.io`, and now anyone with the link can open it. No sign-in required on their end. If you've got a paid plan and want it on `app.example.com` instead, you can point a custom domain at the published service.

Publish is a deliberate switch, not a default. Until you flip it, the project stays private and only you can see the dev URL. Build in private, ship when you mean to.

## When a Site beats a Space

Space is the right tool for a single small thing: one landing page, one webhook, one tip calculator. The moment your idea grows past that, move up. Reach for a Site when you hit any of these:

- **More than one page.** A portfolio with a home, an about, and a projects page is a project, not a widget.
- **Your own dependencies.** Space runs on a fixed set of installed packages and you can't add to it. A Site lets you install what you need.
- **A real database.** Form submissions, a small CRM, anything you want to store and query later. SQLite lives in the folder and your data stays on your server.
- **Something you'll keep evolving.** If you expect to come back next week and add a feature, you want a folder you own, not a one-off route.

If you already have a Space page that's outgrowing itself, you don't start over. Zo can export a Space into a Site and carry the routes across, which is its own short guide in the space-to-site walkthrough.

The honest test: if you can describe the whole thing in one breath and it's one page, build a Space. If you keep saying "and then it also," you want a Site.

That's the entire workflow. Create, preview, refine in chat, publish when it's ready, and the whole project sits in a folder you can open and read. The rest of Zo Computer 101 works the same way, specific and tested with no hand-waving, over at jeffkazzee.zo.space/writing.
