---
title: "Rules: teach Zo your preferences once and stop repeating yourself"
id: rules-explained
category: memory
kind: how-to
date: 2026-06-18
updated: 2026-06-18
excerpt: If you correct Zo the same way three times, that correction wants to be a Rule. Here's how Rules work, the always-vs-conditional split, and the trap of over-stuffing them.
tags: [zo, rules, memory, beginner, preferences]
related: [agents-md-explained, how-zo-memory-works, rule-skill-persona-automation]
difficulty: beginner
reading_time: 6
---

You tell Zo to drop the em dashes and it does, for that conversation. Next week, in a fresh chat, the em dashes are back and you are typing the same correction you already gave once. That loop is the exact thing Rules exist to kill. A Rule is a standing instruction about how Zo should behave, saved once, applied automatically, so you stop re-teaching the same preference every time you open a new conversation.

The thing to get straight up front: a Rule is about behavior, not knowledge. "Never use em dashes" is a Rule. "My main project is called [Project]" is not, that's a fact and it belongs in your AGENTS.md. Mixing those two up is an easy way to make a Rule that does nothing useful.

> A Rule changes how Zo acts. A fact changes what Zo knows. If you can't tell which one you're writing, you'll get a Rule that quietly does nothing.

## Always or conditional

Every Rule is one of two shapes, and picking the right one is most of the skill.

An **always-applied** Rule fires on every turn, no matter what you're doing. Use it for preferences that are true across all your work. Voice, formatting, defaults. "Write in sentence case." "Plan before any task that touches more than one file." These are cheap to keep on because they apply everywhere anyway.

A **conditional** Rule only fires when a condition you describe is true. You write the trigger in plain language and Zo checks it against what's happening in the conversation. The condition does the gating, so the Rule stays out of the way until it's relevant.

| Rule | Type | Why |
| --- | --- | --- |
| Use sentence case for all headings | Always | Applies to every piece of writing |
| When writing SQL, prefer CTEs over nested subqueries | Conditional | Only matters when there's SQL |
| Never send an email without showing me the draft first | Conditional | Only fires on email actions |
| When I say "ship it," skip the recap and just do the work | Conditional | Triggered by a specific phrase |

The win with conditional Rules is that you can pile up a lot of narrow, useful behaviors without making every single conversation heavier. A rule that only loads when you're touching email costs you nothing on the days you're writing copy.

## How to make one without overthinking it

The fastest path is to just say it. Tell Zo "remember this as a rule: never use exclamation points unless something is genuinely alarming" and it'll write the Rule and save it. You can also open Settings → AI → Rules and manage them by hand, which is worth doing once just to see what's already in there.

A clean way to find Rules worth making: watch your own corrections. If you've told Zo the same thing three times across three different chats, that correction has earned a Rule. The rule of three is a decent filter because a one-off fix is just a one-off fix, but a pattern of corrections is a preference you keep having to re-explain.

Good Rules to start with, in roughly the order most people want them:

1. A voice rule. How your writing should sound, what words to avoid, sentence case or not.
2. A planning rule. Whether Zo should sketch a plan before large tasks or just start building.
3. A safety rule. Anything that should never happen without your sign-off: sending mail, deleting files, publishing a page.
4. A format rule. How you want output structured by default, tables vs prose, length, citations.

## The trap nobody warns you about

Here's the failure mode that creeps up on you. Every Rule is context that gets loaded on the turns it applies to. A handful of sharp Rules makes Zo behave like you want. A hundred fussy ones turn into noise that buries the few that matter and makes the model spend attention parsing your preferences instead of doing the work.

So the discipline is subtraction. Keep Rules that change behavior in a way you'd actually notice if they were gone. Drop the ones that just feel tidy. "Never use the word 'utilize'" earns its place because you'd see the difference. "Prefer slightly warmer phrasing in casual contexts" is the kind of vague mush that sounds nice and does nothing checkable, and it's costing you context the whole time it sits there.

A quick test before you save one: could you tell, by reading the output, whether this Rule fired? If the answer is no, it's probably not a Rule, it's a feeling. Cut it.

## Rules vs the other memory tools

Rules are one of several ways Zo remembers things, and they overlap enough to confuse people. Short version:

- **Rules** are how Zo should behave.
- **AGENTS.md** is what your projects and files are. The AGENTS.md guide covers that one in full.
- **Personas** bundle a behavior set, a voice, and a tool scope together for a specific mode of working.

If you want the whole map of which tool to reach for when, the rules vs skills vs personas guide lays them side by side. For Rules specifically, the mental model is simple: durable preferences, applied automatically, always or on a condition, kept few and sharp.

Get three or four good Rules in place and the difference is immediate. Zo stops drifting back to its defaults and starts behaving like it already knows how you work, because now it does. The rest of Zo Computer 101 is built the same way, specific and tested with no hand-waving, and it lives at jeffkazzee.zo.space/writing.
