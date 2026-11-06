---
title: "Prompt Zo so it does the thing the first time"
id: prompting-zo
category: working-with-ai
kind: how-to
date: 2026-06-18
updated: 2026-06-18
excerpt: Most 'the AI got it wrong' moments are really 'I described it wrong' moments. Here's how to prompt Zo so you get the result on the first pass instead of the third.
tags: [zo, prompting, working-with-ai, beginner]
related: [manual-evaluation, picking-a-model, zo-pushback]
difficulty: beginner
reading_time: 7
---

You ask Zo for something, it hands back the wrong thing, and your first instinct is that the model is dumb. Most of the time it isn't. You gave it a sentence that had three valid readings and it picked the one you didn't mean. Prompting well is mostly the unglamorous skill of removing the readings you didn't mean before Zo has to guess.

> When you find yourself on the third re-prompt, the problem usually isn't the model. It's that you've been editing your description and calling it editing the output.

## Name the outcome, not a feeling

The single most common bad prompt is the vague verb with no target. "Clean up this CSV." Clean up how. Drop empty rows? Normalize the date column? Dedupe on email? Zo will pick something reasonable and reasonable is not what you wanted.

Compare:

| Vague | Concrete |
| --- | --- |
| "Summarize my notes" | "Pull the action items out of `Documents/standup.md` into a checklist, one line each, grouped by who owns them" |
| "Fix the script" | "`scripts/import.py` throws `KeyError: 'sku'` on row 1, the column is actually `SKU`, make it case-insensitive" |
| "Make my space nicer" | "On my zo.space home page, add a links section under the bio with my GitHub, X, and Substack" |

The right-hand column took ten extra seconds to type and saved you a round trip. That trade is almost always worth it.

## Give Zo the context it can't infer

Zo can read your files and run commands. It cannot read your intent. The stuff in your head that makes the task make sense is exactly the stuff that has to go in the prompt: what the thing is for, who it's for, the constraints that aren't negotiable, and what "good" looks like to you specifically.

If a rule belongs on every task, put it in a persona once and stop retyping it. The build a persona guide walks through it.

## Match the prompt size to the job

Short directives and full specs both work. They work in different situations, and using the wrong one is where people waste time.

- **Short directive** works when you've already loaded the context. Mid-conversation, after Zo has seen the files and you've agreed on the shape, "now do the same for the other three folders" is enough. It's leaning on everything above it.
- **Full spec** works for new, complex, cold-start work. No shared context yet, real stakes, multiple moving parts. This is where you write the paragraph: goal, inputs, constraints, output format, edge cases.

The failure mode is firing a one-word ask into a cold conversation and expecting a mind-reader. "Refactor it." Refactor what, toward what. Zo will guess, and a guess on a complex task is a coin flip you then have to debug.

## Show the shape you want

Telling Zo the format gets you close. Showing it gets you there. If you want a table, paste two rows of the table. If you want JSON, paste the object shape with the keys you expect. If you want a three-line summary, write one three-line summary and say "like this."

This matters most for anything structured. "Give me the data as JSON" leaves the key names, nesting, and types up for grabs. "Give me JSON shaped like `{ "sku": string, "price_cents": number, "in_stock": boolean }`" leaves nothing up for grabs. The example is the spec.

## Say what to avoid out loud

People describe the target and assume the obvious wrong turns are obvious. They aren't. If you don't want Zo to install new packages, say "don't add dependencies." If you don't want it touching a file, name the file. If a previous attempt went sideways a specific way, name that too: "last time you put everything in one function, keep them separate."

Negative constraints are cheap and they kill whole categories of wrong answer. A prompt that says what good looks like and what bad looks like is harder to misread than one that only points at good.

## For big work, ask for a plan first

When a task spans multiple files or several steps with dependencies, don't ask Zo to just go. Ask for the plan, read it, then green-light it. "Before you write anything, give me the steps and which files each one touches." Thirty seconds reading a plan catches the misunderstanding while it's still words, before it's a pile of edits you have to unwind. The manual evaluation guide is the same instinct applied after the work exists. This applies it before.

## Tell Zo the goal, let it pick the tools

A common over-correction is micromanaging the how. "Use grep to search the files." You don't need to. Zo has files, shell, web, browsing, image generation, and a stack of integrations, and it's better than you at choosing which one fits. Tell it the destination, not the route. "Find every place I reference the old domain across my workspace" beats "run ripgrep with these flags." Save the specifics for when you genuinely care about the method, like a particular library or a particular output format. The rest of the time, the goal is the instruction.

The pattern under all of this is the same: every ambiguity you leave in the prompt is a decision you've handed to Zo, and you won't like all the decisions it makes on your behalf. Spend the ten seconds up front. You'll re-prompt less.

If the model choice is wrong, the prompt does extra work it should not have to. The picking a model guide is the natural next stop. The rest of Zo Computer 101 lives at jeffkazzee.zo.space/writing.
