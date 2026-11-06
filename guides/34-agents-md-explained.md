---
title: "AGENTS.md: the one file that gives Zo a memory between sessions"
id: agents-md-explained
category: memory
kind: how-to
date: 2026-06-18
updated: 2026-06-18
excerpt: Zo boots fresh every session and reads files to remember you. AGENTS.md is the file it reads first. Here's how to write one that actually helps instead of bloating.
tags: [zo, memory, agents-md, beginner, workspace]
related: [how-zo-memory-works, rules-explained, skills-explained]
difficulty: beginner
reading_time: 7
---

Every time you start a conversation, Zo wakes up with no memory of the last one. It reconstructs who you are and what you're working on by reading files in your workspace, and `AGENTS.md` at the workspace root is the routing map it leans on to get oriented. Write a good one and every future session starts oriented. Skip it, and you spend the first ten minutes of every chat re-explaining where your projects live.

That gap is the whole reason this file exists. Zo is not pretending to forget. It genuinely starts cold, so the quality of its first move depends entirely on what you left behind for it to read.

> AGENTS.md is an index of durable workspace facts. The second it turns into a log of what happened each session, it stops earning its place.

## What AGENTS.md actually is

Think of it as the index in the front of a reference book. Not the chapters, the index. A new session opens it, sees the shape of your workspace, and knows where to go next without you narrating.

A root `AGENTS.md` answers four questions fast:

1. What projects exist
2. Where each one lives (the actual folder path)
3. What each folder is for
4. Where to look next for detail

That's the job. When you're working inside a specific folder, Zo will also read an `AGENTS.md` in that folder if one exists, and the more specific file wins. So your root file stays a high-level map and each project keeps its own deeper notes next to its own code.

## What to put in it

Keep it to durable, structural facts. The stuff that's still true next month.

A solid root file usually has:

| Section | What goes here |
| --- | --- |
| Project map | One line per active project: name, path, one-sentence purpose |
| Canonical paths | Where the important things live, so Zo stops guessing |
| Aliases | Old names a project went by, so a search still finds it |
| Don't-break list | Live URLs, production files, anything a wrong edit takes down |

The don't-break list is the part people forget, and it's the one that saves you. If you have a published site running off a specific file, or a service that breaks the moment someone touches a port config, write it down in plain language. "The cookbook site serves from `Projects/zo-cookbook-app`, do not restart its process by hand" is worth more than a paragraph of architecture.

Here's the shape, not a template to copy:

```md
# Workspace map

## Active projects
- Launchling, Projects/launchling, public launch-page builder. Read its AGENTS.md first.
- Cookbook, Projects/zo-cookbook-app, published Zo Site. Edit source, never the process.

## Don't break
- jeffkazzee.zo.space routes are live. Confirm before replacing "/".
```

## What to keep out

This is where most AGENTS.md files go bad. They turn into a log.

Leave these out:

- Chat transcripts or "here's what we did today"
- One-off facts that won't matter next week
- Secrets, API keys, tokens (those belong in Settings, never in a file)
- Long decision histories that read like a journal

Every line you add costs something. Zo loads this file early, so a bloated AGENTS.md crowds out the context you actually want it spending attention on. A 40-line index that's all signal beats a 400-line scroll where the useful part is buried on line 230. When a project dies or a path changes, delete the stale line. Pruning is part of maintaining it, not a separate chore.

There's a clean division of labor worth knowing. AGENTS.md holds settled facts about your files and projects. Behavioral preferences, the "always do X, never do Y" stuff, belong in Rules instead, covered in the rules guide. Repeatable workflows with bundled steps belong in Skills, covered in the skills guide. AGENTS.md is the map. It sits above the rulebook and the toolbox, pointing at both.

## How to make one without writing it yourself

You don't have to hand-author this. Ask Zo directly:

> Read through my workspace and create a root AGENTS.md that maps my projects, their paths, and what each one is for. Keep it to an index, no chat logs.

It'll explore your folders, find the real projects, and draft the file. Then read what it wrote and cut anything that's noise. The first draft usually over-includes, because Zo would rather give you too much than miss something. Your edit pass is where it gets sharp.

After that, treat it like a living document. When you start a new project, add the line. When you rename something, update the path and drop the old name into aliases so future searches still land. When you finish work and notice a fact that'll matter again, that's the cue to add it.

## The payoff

Here's what changes once you have a good one. You open a fresh chat, type "let's keep going on the launch page," and Zo already knows which folder that is, what's live, and what not to touch, because it read the map before you finished your sentence. No re-onboarding. No "which project do you mean." The running start compounds across every session you'll ever have.

If you want the full picture of how Zo rebuilds context each time, the memory guide explains the system AGENTS.md sits inside. The rest of Zo Computer 101 is built the same way this file is: specific, tested, no hand-waving. It lives at jeffkazzee.zo.space/writing.
