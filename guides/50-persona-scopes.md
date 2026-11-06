---
title: "Lock a persona down: scopes and tool access for safe unattended work"
id: persona-scopes
category: personas
kind: how-to
date: 2026-06-18
updated: 2026-06-18
excerpt: A persona isn't just a voice, it's a keyring. Give an unattended automation a persona that can read and draft but not send or delete, and a bad prompt can't do real damage. Here's how.
tags: [zo, personas, scopes, security, automations, beginner]
related: [personas-explained, build-a-persona, plugin-inside-automation]
difficulty: beginner
reading_time: 7
---

An automation runs with the same tool access as the persona behind it. If that persona can send mail, post messages, or manage your store, the automation can do those things too while you are asleep. Nothing sits between an ambiguous 3am prompt and your accounts unless you put it there. Nothing sits between an ambiguous 3am prompt and your real accounts unless you put it there. A persona's permission set is the thing you put there.

Most people treat a persona as a voice. A tone, a saved prompt, a character you switch to when you want a certain kind of answer. That is half of what it is. The other half is a keyring, because every persona carries a set of scopes that decide which tools it can touch at all. When a persona doesn't have a tool, that tool is removed from the conversation entirely. Zo cannot fumble it, cannot half-use it, cannot apologize for failing to use it. The capability simply is not in the room.

> A scope isn't a suggestion the model tries to honor. It's a wall. The tool either exists in that conversation or it doesn't.

## Why this matters for automations specifically

In a live chat you are the safety check. You see the draft before it sends, you catch the rm before you confirm it, you read the email before it leaves. An automation deletes that step on purpose, because the entire point is that you are not there. So the blast radius of a bad run is whatever the persona running it is allowed to do.

Run a daily inbox-triage automation under your default all-access persona and one weird prompt interpretation can fire off a reply to a client. Run that same automation under a persona that can read your inbox and email you a summary but physically cannot send mail on your behalf, and the worst case is a useless summary in your inbox. Same job, wildly different downside.

## The pattern: a reporting persona

The shape I reach for first is a read-and-draft persona with no ability to act on the world. Call it something like "Reporter." It can:

- read files and search the workspace
- read your calendar and inbox through connected integrations
- search the web for context
- email the result to you

And it cannot send messages as you, post anywhere, delete files, run shell commands, or touch payments. You hand it the risky overnight jobs. An ambiguous instruction can produce a wrong report. It cannot produce a wrong action.

## How scopes actually work

Permissions live in Settings → AI → Personas, set when you create or edit a persona. Most jobs map cleanly onto one of the presets:

| Preset | What it can do |
| --- | --- |
| All access | Everything, no restrictions |
| Workspace | Files, web, media, and read access to settings, hosting, and commerce. No shell, no communications |
| Read only | Read files, search the web, view settings. Changes nothing |
| Chat only | Conversation, no tools at all |

For most reporting automations, Workspace or Read only gets you close, and then you add back exactly the one channel you want, usually email to yourself.

When a preset doesn't fit, go custom and toggle scopes by category. They follow a read / write / manage shape: `files:read` versus `files:write`, `hosting:read` versus `hosting:manage`, `commerce:read` versus `commerce:manage`. Communications split by channel, so `comms:email` is a separate grant from `comms:sms` or `comms:discord`. Connected apps get their own integration scopes too.

One rule worth internalizing: write implies read. Granting `files:write` automatically pulls in `files:read`, because you cannot meaningfully edit a file you can't see. The dependency runs one direction only. Read-only stays read-only. For the full list of scope names and what each one covers, see the scopes cheat sheet guide instead of trying to memorize them here.

## Wiring it up, start to finish

The whole workflow is three decisions:

1. **Write down what the job touches.** Not what it might want someday. What this specific automation reads, and what single output it produces. "Reads my calendar and unread email, writes one summary email to me." That sentence is your scope list.
2. **Grant only that.** Start from Read only, add `comms:email` so it can reach you, stop. If you find yourself granting `shell:execute` to a job that summarizes your day, that is a sign the prompt is doing too much, not that the persona needs more keys.
3. **Run the automation under that persona.** When you set up the automation, point it at the locked-down persona rather than your default. Now the schedule, the prompt, and the permissions are all decided up front, and the overnight run cannot exceed them.

The same move scopes a plugin or integration inside an automation, which the guide on running a plugin inside an automation gets into.

## The mindset shift

You stop asking "do I trust this prompt" and start asking "what is the worst this persona can do if the prompt goes sideways." The second question has an answer you can read off a settings page. The first one is a feeling. Lock the persona down to the smallest keyring the job needs and you get to be wrong about the prompt without being punished for it.

If you want the voice side of this, the personas explainer covers what a persona is and the build-a-persona guide walks through making one from scratch. The rest of Zo Computer 101 is built like this one, specific and tested with the sharp edges left on, and it lives at jeffkazzee.zo.space/writing.
