---
title: "Share a folder with a link using zo.pub"
id: zo-pub-sharing
category: hosting
kind: how-to
date: 2026-06-18
updated: 2026-06-18
excerpt: Sometimes you don't need a website, you need to hand someone a folder of files. zo.pub turns any folder into a public link people can browse and download, no Zo account required.
tags: [zo, zo-pub, sharing, files, hosting, beginner]
related: [zo-hosting-explained, get-your-work-out-of-zo, first-zo-site]
difficulty: beginner
reading_time: 5
---

You finished a thing. A folder of edited photos, a data export, a deck plus its press contacts, and now someone wants it. The reflex is to zip it, attach it to an email, watch the attachment bounce off a 25MB limit, then go hunting for a Dropbox link. zo.pub skips all of that. You point Zo at a folder, you get back a URL, and anyone who opens it can browse the files or pull the whole thing down as one archive. No account, no login wall, nothing to approve.

> zo.pub is a download link with a clean listing page attached. That's the whole pitch, and it's enough.

## What it actually is

Every Zo comes with a public namespace at `zo.pub/<your-handle>`. Publish a folder and it shows up there as a collection. A visitor who opens the link lands on a listing of the files inside: name, size, date. They can click any file to view or download it, walk into subfolders, or grab the entire collection as a single zip or tar. They never see your workspace, your other files, or anything you didn't publish.

The thing to get straight up front: zo.pub shares files, it does not run anything. There's no server-side code, no form handling, no auth. If you need any of that, you're looking at a [Site or a Service](zo-hosting-explained), not zo.pub. Think of it as the share button, not the app.

## Publish a folder

The fast path is to just ask Zo. Any of these work:

- "Publish this folder to zo.pub"
- "Give me a link to share these files"
- "Make the `Q4 Launch Kit` folder public"

Zo does the upload and replies with the `zo.pub/...` URL. Copy it, send it, done. That URL is stable, so you can put it in an email or a doc and it keeps working as long as the collection exists.

If you'd rather drive it yourself, there's a CLI. Three commands cover everything:

| Command | What it does |
| --- | --- |
| `zopub ls` | List the collections you've already published |
| `zopub sync <name> <dir>` | Create or update a collection from a local directory |
| `zopub rm <name>` | Take a collection down |

So publishing a folder of launch assets looks like this:

```
zopub sync q4-launch-kit ./launch-kit
```

The sync is incremental. Run it once and it creates the collection. Change two files, run the exact same command again, and only those two files go up. The link you already shared doesn't change. That's the part that makes zo.pub good for living folders, the weekly report, the running photo dump, the asset kit you keep tweaking. You sync, the URL stays put, whoever has the link sees the new version.

## The URLs

Three levels, and they're predictable enough that you can hand-type a deep link if you need one:

| URL | What it shows |
| --- | --- |
| `zo.pub/<your-handle>` | Every collection you've published |
| `zo.pub/<your-handle>/<collection>` | One collection's files |
| `zo.pub/<your-handle>/<collection>/<file>` | A single file |

Your top-level page lists everything you're sharing with a one-line summary of each collection, so if you publish a few folders it doubles as a scrappy little public file index. Bookmark-able. Send someone your handle page and they see the whole shelf.

## The one caveat that matters

Here is the line you do not get to forget:

**Everything on zo.pub is public. There is no password. There is no private mode.**

Anyone with the link can open the folder and download every file in it. The links aren't guessable garbage either, your handle and collection name are right there in the URL. So treat publishing like stapling the folder to a public bulletin board, because functionally that's what it is.

What that means in practice:

- **Good to publish:** photos, data exports, portfolio PDFs, finished reports, meeting recordings, a press kit, anything you'd otherwise mail as a download link.
- **Do not publish:** anything with credentials, client PII, unreleased work you'd be embarrassed to leak, or a folder you "think" is fine without actually opening it and reading the file list first.

Before you run `zopub sync` or tell Zo to publish, do the boring thing and look at what's in the folder. The most common way this bites people is a stray `.env`, an API key in a config file, or a spreadsheet with one column nobody meant to share. zo.pub will faithfully publish all of it. The tool isn't checking your judgment for you.

If you find later you shared too much, `zopub rm <name>` (or "take down my drafts folder") pulls the whole collection immediately and traffic stops routing to it.

## When zo.pub is the wrong tool

Quick gut check before you reach for it:

1. **Needs a login or per-person access?** That's a Site or a Service, not zo.pub.
2. **Needs to run code, handle a form, or react to input?** Same, that's a Site or Service.
3. **Just files, meant to be seen, link-and-go?** zo.pub, every time.

When you just need to hand someone a folder, this is the shortest path. If you want the full map of when to use Space, Sites, Services, or zo.pub, read the hosting overview. And if the thing you're sharing is really a project you'll keep building on, start with your first Zo Site instead, then publish exports from it here.

More beginner guides like this one, specific and tested with no hand-waving, live at jeffkazzee.zo.space/writing.
