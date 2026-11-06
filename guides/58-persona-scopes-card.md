---
title: "Persona permission scopes, cheat sheet"
id: persona-scopes-card
category: reference
kind: reference
date: 2026-06-18
updated: 2026-06-18
excerpt: Personas can be locked to exactly the tools a job needs. This is the cheat sheet: the scope model, the read-vs-write-vs-manage pattern, and a few ready-made loadouts to copy.
tags: [zo, personas, scopes, security, reference]
related: [persona-scopes, personas-explained, plugin-inside-automation]
difficulty: beginner
reading_time: 4
---

A persona with full access can read every file, run shell commands, send email as you, and delete things. That is fine when you are sitting there watching it. It is a bad default for a research assistant you spun up to skim the web, and a worse one for anything that fires on a schedule while you sleep. Scopes are how you hand a persona exactly the keys for its job and nothing else.

> The question is never "can this persona do the task." It's "what could this persona do if it misreads the task," and scopes are how you make that answer boring.

## The mental model: scopes are a keyring

Each persona carries a keyring. Every key opens one category of tool. No key, no tool, and when a tool is locked out it vanishes from the conversation entirely. The persona does not try and fail. It does not announce the limitation. The tool is simply not in the room, which means a research persona with no `comms:email` key cannot send an embarrassing draft even if you ask it to, because it has no idea sending mail is a thing it could do.

The keys come in categories like `files`, `web`, `comms`, `hosting`, `settings`, and `commerce`, plus per-integration keys like `integrations:gmail`.

## Read, write, manage

Most categories split into a layer cake, and the layers stack downward. You cannot hold a higher key without the one beneath it.

| Layer | What it grants | Requires |
| --- | --- | --- |
| read | look, search, view | nothing |
| write | create and edit | the matching read |
| manage | configure, control the system itself | the matching read |

So `files:write` pulls in `files:read` automatically, because editing a file you cannot read is nonsense. `hosting:manage` requires `hosting:read`. The one to respect is `settings:manage`. That is the admin key. A persona holding it can edit personas, agents, and rules, which means it can rewrite its own permissions. Hand that out only to a persona you trust with the whole machine.

## Start from a preset

You do not have to build a keyring bolt by bolt. Four presets cover most jobs:

1. **All access** opens everything. Use it for your main interactive persona, the one you drive by hand.
2. **Workspace** gives files, web, media, and read access to settings, hosting, and commerce. No shell, no sending messages. A solid default for "do real work but don't text anyone."
3. **Read only** reads files, searches the web, views settings, changes nothing.
4. **Chat only** strips every tool. Pure conversation. Good for a roleplay or tutor persona.

Pick the closest preset, then drop to **Custom** and toggle individual keys when you need a sharper edge.

## Loadouts to copy

Four starting points. Treat them as recipes, not law.

**The read-only researcher.** Reads files and searches the web, posts and sends nothing.
- `files:read`
- `web:search`
- `web:browse`

It can pull sources and read your notes. It cannot email a contact, edit a file, or touch a setting. This is the safest persona to leave pointed at the open internet.

**The reporting persona.** Gathers, then sends a digest to you and only you.
- `files:read`
- `web:search`
- `comms:email`

Useful behind a scheduled job that mails you a morning brief. It can compose and send, so keep the recipient as your own address in the prompt and do not also give it `files:write` unless the report needs to write a file.

**The builder.** Edits the project and ships it.
- `files:read` and `files:write`
- `shell:execute`
- `hosting:read` and `hosting:manage`

This persona changes code and manages sites and services. Powerful, and worth a second look before any of it runs unattended, because `shell:execute` plus `files:write` is a persona that can rewrite your workspace.

**Full access.** Everything, for the persona you operate live and watch.

## The safety rule

Here is the line that matters more than any table on this page. Scope down anything that runs without you watching.

An automation runs with the access of whatever persona it uses. A morning brief that only needs to read your calendar and email you should not be carrying `files:write`, `shell:execute`, or `settings:manage`. If it misreads its own prompt at 6am, the blast radius is whatever keys you left on the ring. Build a narrow persona for the unattended job, give it the two or three keys the task actually needs, and point your automation at that. The minute a persona can act while you are away from the keyboard, every extra key is a liability with no upside.

For interactive work where you read every action before it lands, loosen up. That is the whole trade. Trust scales with how closely you are watching.

## Where the exact names live

The scope names above are the real categories, but the full list and the toggles live in **Settings → AI → Personas** under the permissions section for each persona, with the integration keys appearing for whatever apps you have connected. Build the keyring there, not from memory, because the available integration scopes change as you connect and disconnect apps.

If you want the longer version of how a locked-down persona behaves in practice, the personas explainer covers the why, and the deeper scopes walkthrough covers the how. Both live with the rest of Zo Computer 101 at jeffkazzee.zo.space/writing.
