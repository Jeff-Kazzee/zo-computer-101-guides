---
title: No lock-in: get your work out of Zo to your laptop and GitHub anytime
id: get-your-work-out-of-zo
series: Zo Computer 101
category: building
kind: how-to
order: 2
date: 2026-06-18
updated: 2026-06-18
excerpt: Your files live on your own server, so getting them out is easy and nobody's holding them hostage. The round-trip to your laptop, to GitHub, and to a public link, plus the one-time GitHub setup.
tags: [building, github, sync, zo-pub, beginners]
related: [move-an-app-into-zo, zo-hosting-explained]
difficulty: beginner
reading_time: 7
---

The flip side of building on Zo is the question every careful person should ask before they invest in a tool: how do I get my stuff out? On a lot of platforms that answer is ugly, an export button that gives you a sad zip, or nothing at all. On Zo it is easy, and that is not an accident. The whole design is built on the idea that your files live on your own server in open formats. Nobody is holding them hostage.

There are three directions you'll want, and they cover everything: down to your own computer, over to GitHub, and out to a public link. Here's each one.

> Your files sit on your server as plain markdown and real folders. You can open a terminal and `cat` them. Nothing has to translate them back to you first. Custody of your own files is the whole point of a personal server.

## Direction 1: down to your own computer

The cleanest way to keep a copy on your laptop is the **desktop app's folder sync.** Install the Zo desktop app, sign in, and use Sync, Add Folder to pick a folder on your computer that mirrors a folder in your Zo workspace. From then on, changes on either side sync to the other automatically. Edit on your laptop, it shows up on your Zo. Zo writes a file, it shows up on your laptop.

This is the move if you want a continuous local copy, not a one-time dump. Your work is in two places at once, which is also a backup. If you just want a single file or folder right now without setting up sync, you can download it straight from the workspace. But for anything ongoing, set up the folder sync once and stop thinking about it.

## Direction 2: over to GitHub

For code, GitHub is where it should live: version history, a backup off your Zo, and the ability to collaborate or open it on any machine. Zo ships with the GitHub CLI (`gh`) already installed, so the only thing standing between you and pushing a repo is a one-time authentication.

**The one-time setup.** The easiest path is to ask Zo to connect GitHub, which surfaces a Connect button that walks you through the whole thing. Take it. You'll create a personal access token (classic) in your GitHub settings with the scopes Zo asks for (`repo`, `read:org`, and `gist`), and the button handles the rest.

If you'd rather authenticate by hand in your Zo terminal, the one gotcha that bites people: `gh auth login --with-token` reads the token from stdin, it is not an argument you paste after it. So you pipe it in:

```bash
echo YOUR_TOKEN_HERE | gh auth login --with-token
```

Paste the token as a bare argument and it errors. Pipe it and you're done. Once `gh` is authenticated, you and Zo can both work with GitHub.

**The round-trip.** After that, it's plain English:

- "Create a GitHub repo for this project and push it."
- "Commit what we changed and push it."
- "Pull my repo `foo` into Zo and get it running."

That last one is the inbound half from the previous guide: a repo on GitHub clones onto your Zo in one step, which is the cleanest way to bring a project in. So GitHub is both your exit and your entrance. Push from Zo to back up and share, pull into Zo to work on it. The code never gets stuck in one place.

## Direction 3: out to a public link

Sometimes "get it out" doesn't mean to your laptop or a repo, it means hand it to someone. For files, that's **zo.pub.** Ask Zo to publish a folder and you get a public link, `zo.pub/yourhandle/<name>`, that anyone can open with no Zo account, browse the files, download any one, or grab the whole folder as a zip. A portfolio PDF you're handing a client, say. The catch worth repeating: zo.pub is fully public, no password, so only put shareable things there.

For a website or app rather than files, the public version is publishing a **Site** or **Service**, covered in the hosting guide. Same idea, different output: a public URL you control.

## A quick map of the exits

| You want | Use | What you get |
|---|---|---|
| A live copy on your laptop | Desktop folder sync | Two-way mirror, automatic, doubles as backup |
| One file or folder, right now | Download from workspace | A one-time copy |
| Code backed up and shareable | GitHub via `gh` | Version history, off-Zo backup, collaboration |
| Hand someone a folder of files | zo.pub | Public link, browse and download, zip |
| A live website or app | Publish a Site/Service | A public URL you control |

## The honest takeaway

This is the guide I'd point a skeptic at. The fear with any AI platform is lock-in, that you build on it and then you're trapped. Zo's answer is structural: your files are already on your server in formats you can read, the desktop app keeps a local mirror, and GitHub is one auth away. You are never more than a sync or a push from having your work somewhere else entirely.

Set up the desktop sync and authenticate GitHub in your first week. Knowing you can walk away is what lets you build on something like you mean it.

Zo Computer 101 is a growing library of beginner guides written by someone who builds on this thing every day. The other half of this round-trip is bringing work in, covered in the move-an-app guide, and the hosting guide explains where it all lives once it's on your Zo. Both are in the library at jeffkazzee.zo.space/writing.
