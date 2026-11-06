---
title: "Give Zo a different job, voice, and set of keys: personas explained"
id: personas-explained
category: personas
kind: explainer
order: 1
date: 2026-06-18
updated: 2026-06-18
excerpt: A persona is a saved version of Zo with its own instructions, its own voice, and its own set of keys. Here's what they're for, the permission presets that make them safe, and the one nobody sets up that they should.
tags: [personas, scopes, integrations, prompting, beginners]
related: [persona-scopes, build-a-persona, plugin-inside-automation]
difficulty: beginner
reading_time: 7
---

A persona is a saved Zo with three parts: instructions, a voice, and permissions. It is how you give the same assistant one job and one toolset, instead of re-explaining yourself every session. You are not training a new AI. You are handing the same Zo a job description and a keyring, and saying "be this for a while."

Most people run one default Zo for everything and never touch personas. That works fine right up to the moment it doesn't: you want Zo to write in a specific voice without re-explaining it every time, or you want an automation that can read your inbox but physically cannot fire off a tweet. Both of those are a persona, and once you've made one you start making more.

> A persona is not a different brain. It's the same Zo with a job description taped to the monitor and only the keys it needs to do that job.

## The three things a persona carries

**Instructions.** This is the prompt: who this persona is, what it knows, how it should behave. It can be a personality ("you are a blunt editor who hates filler") or it can be pure context you are tired of repeating ("here is my product, my audience, and the five things I always want considered"). The docs put it well: one use is roleplay, the other is standing context you always want loaded for a kind of work. The second one is the quiet workhorse.

**Voice.** A persona can hold a consistent tone so you stop re-specifying it. A writing persona that already knows your style. A tutor that always explains at the level you actually are. The voice lives in the persona, not in your memory of how to ask.

**Keys.** This is the part that matters most and gets ignored most. Every persona has a permission set: which tools it can touch. This is what turns a persona from "a saved prompt" into a safety boundary, and it is the reason personas matter for anything running unattended.

## Permissions: the part that actually protects you

When a persona does not have access to a tool, that tool is gone from the conversation. Not "Zo tries and fails." Gone. Zo cannot use it and will not mention it, because it is not in the room. That is what makes a scoped persona genuinely safe instead of politely-asked-to-behave.

Zo ships four presets, and most personas fit one:

| Preset | What it can do |
| --- | --- |
| All access | Everything, no restrictions |
| Workspace | Files, web, media, read-only settings/hosting/commerce. No shell, no messaging |
| Read only | Read files, search the web, view settings. Can't change anything |
| Chat only | Conversation, no tools at all |

If a preset is close but not exact, you pick **Custom** and choose individual scopes: `files:read`, `web:browse`, `comms:email`, and so on. Write scopes pull in their read scope automatically, so granting `files:write` gives you `files:read` too. You set all of this in Settings, AI, Personas, when you create or edit the persona.

The mental model: decide what the job needs, grant exactly that, nothing else. A research persona gets `web:search` and `web:browse` and `files:read` and stops there. It can dig, read dashboards, and write up notes, and it could not delete a file or send a message if it tried, because those tools were never handed over.

## Where personas earn their keep

A few concrete jobs that are obviously better as a persona than as a one-off prompt:

- **A writing voice.** Instructions hold your style and rules, so every draft starts in the right tone instead of you pasting the same guidance each time.
- **A scoped researcher.** Read-only plus web access. It pulls information and writes notes, and cannot touch anything destructive. Safe to point at a big task and walk away.
- **A safe automation runner.** This is the big one. An automation runs with whatever access it has, unattended. Run it under a persona scoped to exactly its job, and a bad prompt can't do real damage. A "morning reporter" that can read your calendar and email you, and nothing else, is a safe thing to leave firing every day.
- **A per-channel character.** You can assign different personas to different channels. One voice on Discord, a different one over SMS. Same Zo, different hat per door.

## Switch them anytime

Personas are not a commitment. You switch between them whenever you want, mid-work, and you can set which persona answers on which channel. The default Zo is just the persona you have not replaced yet. Making a new one does not take anything away; it adds a hat you can put on when the job calls for it.

## The one nobody sets up

Make a read-only research persona before you need it. It is thirty seconds of setup: name it, give it the Read only preset, write one line of instruction about what it researches and how you want notes formatted. Now you have something you can hand any "go find out about X" task to, with zero risk that it edits or sends anything by accident. It is the persona that proves the concept, and the one you will reach for constantly once it exists.

You do not have to design a cast of characters on day one. You need one scoped persona doing one job well. Build the read-only researcher, feel how it changes the way you delegate, and the rest will suggest themselves.

If you set up one persona first, make it a read-only researcher. Give it the Read only preset, one line about what it researches, and hand it your next "go find out about X" task. The rest of Zo Computer 101 is built to be read this way, one job at a time: jeffkazzee.zo.space/writing.
