---
title: "Rule, skill, persona, or automation? The four-way decision, settled"
id: rule-skill-persona-automation
category: memory
kind: reference
date: 2026-06-18
updated: 2026-06-18
excerpt: Four ways to make Zo remember or repeat something, and beginners constantly pick the wrong one. Here's the one-line test for each, with a decision table you can actually use.
tags: [zo, rules, skills, personas, automations, reference, beginner]
related: [rules-explained, skills-explained, personas-explained]
difficulty: beginner
reading_time: 6
---

Zo gives you four ways to make it remember something or repeat itself, and people pick the wrong one constantly. They write a 600-word skill for what should have been a one-line rule, or stuff a behavior preference into a persona prompt where it only applies half the time. The fix is knowing which of the four you actually need before you build anything, and that comes down to four questions.

Here are the four, and the single question that picks each:

> A rule changes how Zo behaves. A skill is how Zo does one specific job. A persona is who Zo is and what it's allowed to touch. An automation is when Zo acts without you.

## Rule: how Zo behaves

A rule is a durable behavior preference. It sits in the background of every conversation it applies to and bends Zo's defaults toward what you want. Some rules are always on. Others are conditional, scoped to a situation: when you're writing prose, when a task gets big, when you text a certain prefix.

Reach for a Rule when: **"I want Zo to always, or whenever X, behave like this."**

Rules are short by design. "Never use em dashes." "When a task needs more than three tool calls, write a plan first." You're not handing Zo a procedure. You're setting a preference it carries into work it was already going to do. If you find yourself describing steps, you've outgrown a rule.

## Skill: how Zo does one specific thing

A skill is a packaged, repeatable workflow. It lives at `Skills/<skill-name>/SKILL.md` in your workspace, with optional `scripts/`, `references/`, and `assets/` folders next to it. The frontmatter has a `description` that tells Zo when the skill applies. When your request matches, Zo reads the full instructions into context and follows them, loading bundled files or running scripts only as needed.

You want a Skill when: **"I keep re-explaining the same multi-step process."**

That's the trigger. The third time you walk Zo through the same eight steps to format a report or scrub a draft, those steps want to be a skill. Ask Zo to create one, or use the Create Skill action in the command palette. The payoff is that the procedure lives in one file you can read, audit, and edit, instead of getting half-remembered differently each time.

A rule says *be terse*. A skill says *here is exactly how to produce the weekly report, in order*.

## Persona: who Zo is, and what it can touch

A persona is a saved identity. It bundles a prompt (voice, role, standing context), a model choice, and a tool-access scope. You switch between personas at any time, and assign different ones to different channels, so Zo can be one character in Discord and another over SMS.

The scope part is the piece beginners miss. In Settings → AI → Personas you control which tools a persona can use, through presets:

| Preset | What it can touch |
| --- | --- |
| All access | Everything, no restrictions |
| Workspace | Files, web, media, read-only settings and hosting, no shell, no messaging |
| Read only | Read files, search web, view settings, can't modify anything |
| Chat only | Conversation, no tools at all |

When a persona lacks a tool, that tool is gone from the conversation. Zo won't try it and quietly fail. It simply isn't there.

A Persona fits when: **"I want a different voice, a different job, or a tighter set of tools for this kind of work."**

A research persona that can search the web but can't edit your files is a persona. A writing persona that always knows your style guide is a persona. The voice and the guardrails travel together.

## Automation: when Zo acts on its own

An automation is Zo running a prompt on a schedule. Same files, same tools, same integrations as your chats, just firing without you in the room. You describe the cadence in plain English ("every weekday at 7:30am") and Zo parses it. Every run is a real conversation saved to your history, so you can open a misfire and ask Zo why the calendar section came back empty.

It is an Automation when: **"I want this to happen on a schedule, whether or not I remember."**

Morning briefings, page watchers, Friday reports. The strongest ones want fresh context each run and save you from having to remember to ask. Pair them with conditional delivery so the automation becomes a filter instead of another inbox: "text me only if the deploy failed."

## The decision table

| You're thinking... | You want a |
| --- | --- |
| "Zo should always do this" | Rule |
| "Only do this when X is true" | Rule (conditional) |
| "I keep re-explaining these steps" | Skill |
| "I want a different voice or job" | Persona |
| "Limit what these tools can touch" | Persona |
| "Make it happen on a schedule" | Automation |

## They stack

These aren't rivals. They compose, and the good setups use three at once. An automation can run under a persona and invoke a skill: a scheduled job that fires every Friday at 4pm, runs as your locked-down reporting persona that can read files but can't send email, and calls your weekly-report skill so the exact procedure stays in one place. The automation is the *when*, the persona is the *who* and the *guardrail*, the skill is the *how*. Your rules sit underneath all of it, shaping behavior the whole time.

Pick wrong and you feel it. A behavior preference buried in a skill never fires when you expect. A multi-step procedure crammed into a rule gets ignored under pressure. Match the thing to the question and Zo stops drifting.

If this cleared up the four-way muddle, the rules guide, the skills guide, and the personas guide each go one level deeper. They live at jeffkazzee.zo.space/writing.
