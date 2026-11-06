---
title: "Skills: turn a workflow you keep re-explaining into something Zo just runs"
id: skills-explained
category: memory
kind: how-to
date: 2026-06-18
updated: 2026-06-18
excerpt: A Skill is executable memory: a folder with a SKILL.md that Zo loads only when a task matches. Here's how they keep Zo fast and how to make your first one without writing code.
tags: [zo, skills, memory, workflows, beginner]
related: [agents-md-explained, rules-explained, rule-skill-persona-automation]
difficulty: beginner
reading_time: 7
---

You have a workflow you've explained to Zo four times this month. Six steps in a fixed order, a format you keep re-specifying, and the same "no, like last time" correction halfway through. That re-explaining is wasted motion, and it's the exact thing a Skill kills. A Skill is a folder in your workspace that holds a written procedure Zo can pull up and run, so the instructions live in one place instead of in your memory and your patience.

The format is open. Zo Computer implements [Agent Skills](https://agentskills.io/), so a skill is just a folder with a `SKILL.md` file inside it. There is no proprietary builder in the way, just a folder of markdown. A text file with some structure on top.

> A Skill isn't a macro you record once and pray it still works. It's a written procedure you can read, edit, and hand to anyone, including future you.

## What's actually in one

Every skill lives at `Skills/<skill-dir>/SKILL.md`, where the directory name is a lowercase slug that matches the `name` in the file's frontmatter. The frontmatter is short. Two fields do almost all the work:

| Field | What it does |
| ----- | ------------ |
| `name` | The slug. Must match the folder name. |
| `description` | One line describing what the skill does and when to use it. This is the part Zo always sees. |

There are three optional fields if you need them: `compatibility` for environment requirements, `metadata` for extra key-values, and `allowed-tools` to pre-approve specific tools. That's the whole spec. Below the frontmatter is plain markdown: the instructions, written the way you'd explain the job to a competent person who's never done it before.

Here's a minimal one for a recurring chore, drafting a weekly client update from notes:

```md
---
name: weekly-client-update
description: Draft the Friday status email to [client] from this week's notes. Use when I say "do the client update."
---

1. Read this week's entries in notes/[client]/.
2. Pull the three things shipped, anything blocked, and what's next.
3. Write it as a short email: no preamble, bullets under three headers.
4. Match the tone of last week's sent update in the same folder.
5. Hand me a draft. Do not send it.
```

That file replaces the six-step prompt you've been retyping. From now on you say "do the client update" and Zo loads those steps.

## The part that matters: progressive loading

This is the detail that makes skills worth caring about, and it's easy to miss. Zo does not stuff every skill into its head at once. It works in layers.

1. **Always loaded:** the one-line `description` from every skill's frontmatter. Cheap to keep around, so Zo always knows roughly what each skill is for.
2. **Loaded on match:** when your request lines up with a description, Zo reads that skill's full `SKILL.md` and follows it.
3. **Loaded on demand:** if those instructions point at a script, a reference doc, or a template, Zo only opens that file when the instructions actually call for it.

Why you should care: it means you can have forty skills and Zo stays fast, because thirty-nine of them are sitting at one line of context until the moment one is needed. Compare that to dumping every procedure into a giant `AGENTS.md` that gets read on every single turn whether it's relevant or not. Skills are the opposite shape. Dormant until summoned, then fully present. (For the always-on context that genuinely should load every time, see the AGENTS.md guide.)

## Bundling more than text

A `SKILL.md` is enough for most things. When a job has a deterministic step that code does better than prose, a skill can carry that code with it. The layout:

```
Skills/
└── your-skill-name/
    ├── SKILL.md          # required
    ├── scripts/          # optional code Zo can run
    ├── references/       # optional docs and examples
    └── assets/           # optional templates or data
```

Say your workflow includes parsing a messy CSV the same way every time. Put a `scripts/clean.py` next to the SKILL.md, tell the instructions to run it, and you've turned a flaky "interpret this data" step into a deterministic one. Zo runs the script instead of re-reasoning the parse from scratch each time, which is both faster and less likely to drift.

## Making your first one

Two paths, both fine:

- **Ask Zo.** "Make a skill that does [thing], here are the steps." It writes the folder and the `SKILL.md` for you. This is the path I reach for, because describing the workflow out loud is usually how I figure out what the steps actually are.
- **Create Skill in the command palette.** Scaffolds the folder structure so you can fill in the markdown yourself.

The real judgment is knowing which workflow deserves its own folder. The signal is repetition with correction. If you keep pasting the same multi-step prompt, and you keep nudging the output back into shape the same way, that nudging is the spec. Write it down once. The first version won't be perfect, and it doesn't need to be, because a skill is a text file you edit when it gets something wrong, the same way you'd correct it in chat.

A skill is for a procedure, the how of a repeatable job. It's not the place for standing preferences ("always write in sentence case"), which belong in the rules guide, or for a whole personality and tool set, which is what a persona is for. When you're deciding which of those four to reach for, the rule, skill, persona, and automation guide lays out the call.

Start with the workflow that annoys you most to re-explain. Write five lines. Run it once, fix the one step it botched, and you've got a tool that didn't exist this morning.

If this saved you from typing the same prompt a fifth time, the rest of Zo Computer 101 is built the same way: specific, tested, no hand-waving. It lives at jeffkazzee.zo.space/writing.
