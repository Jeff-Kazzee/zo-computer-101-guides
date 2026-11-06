---
title: "Pick a model: when to switch and what the defaults are good for"
id: picking-a-model
category: working-with-ai
kind: explainer
date: 2026-06-18
updated: 2026-06-18
excerpt: Zo lets you choose which AI model drives it, per chat and per channel. Here's when the default is fine, when to switch, and why a bigger context window isn't the same as a smarter model.
tags: [zo, models, working-with-ai, byok, beginner]
related: [byok-setup, prompting-zo, manual-evaluation]
difficulty: beginner
reading_time: 6
---

Zo ships with a default model that's tuned for general work, and for most of what you'll throw at it the default is the right answer. People don't get burned by picking the wrong one. They get burned by not knowing there was a choice, so they grind a hard reasoning task on something underpowered, or they burn money running a fancy model on a job a cheap one would have nailed.

The switch lives in **Settings > AI > Models**. You set the default model that drives chat, and you can set separate models per channel: one for SMS, one for email, one for Telegram. So your phone can run something fast and cheap for quick texts while your main chat runs something stronger. Most people set the default once and forget it. That's fine. The point of this guide is knowing the three or four moments when reaching up to the picker actually pays off.

> A giant context window on a weak model is a bigger junk drawer, not a smarter assistant.

## What the default is good for

The built-in default handles the wide middle of real work. Drafting and editing, summarizing a doc, writing a script, answering a question, running an ordinary multi-step task in your files. If you can't articulate why you'd want something different, you don't, and the default will serve you better than a model you picked because it sounded impressive.

Every plan includes Zo's built-in models. Premium models are billed at-cost, so you pay what they cost to run, and on the free plan there's a daily allowance of free models to work with. That billing shape is the whole reason model choice matters: switching up costs more, switching down costs less, and you want the cost to match the difficulty of the job.

## When to switch up

Reach for a stronger model when the task has one of these shapes:

1. **Hard reasoning.** Tricky logic, math you can't eyeball, a thorny refactor, untangling a bug that's survived two attempts already. This is where a smarter model earns its price in one shot instead of three.
2. **Long agentic runs.** A task that chains many tool calls and has to keep track of what it did twenty steps ago. Weaker models lose the thread on long horizons and start repeating or contradicting themselves.
3. **The output is going to ship.** Public writing, anything touching money, anything hard to undo. Pair this with judging the result by hand, covered in the guide on evaluating AI output.

A good tell: you've already asked the default twice and it's circling instead of converging. Stop feeding it more prompt. Switch up and re-run the original ask once.

## When to switch down

Switch to a cheaper or free model when the work is simple and there's a lot of it:

- Bulk reformatting, renaming, tagging, light cleanup.
- High-volume classification where each item is easy.
- A scheduled automation that fires often. A 15-minute automation on a premium model adds up fast, and most automations are doing dull, repeatable work that a cheap model handles fine.

The instinct to run everything on the best available model is expensive and usually pointless. Match the tool to the job.

## Context window is not intelligence

This is the trap that costs beginners the most confusion. Models advertise context windows: how much text they can hold at once, sometimes hundreds of thousands of tokens. Bigger sounds better. It often isn't the thing you actually care about.

A bigger context window gives the model more room to hold your prompt at once. It does not make the model smarter. More junk drawer, not more brain.

A model with a huge window and weak reasoning will happily ingest your entire codebase and still give you a shallow, confidently-wrong answer about it. The window decides whether the relevant material fits. Reasoning decides whether the answer is any good. When you're choosing, weight the quality of the thinking first and the window second, and only stretch for a big window when you genuinely need to feed in a lot of material at once.

## Bring your own keys

If you already pay OpenAI, Anthropic, or a Groq endpoint, or you route through OpenRouter, you can plug those keys into Zo under **Settings > Advanced** and drive Zo with models you're billing yourself. That skips Zo's usage charges entirely and gives you access to specific models you want.

One sharp edge worth knowing before you rely on it: a custom model won't fall back to Zo's built-in models if it fails. If your key is invalid or out of credits, the call errors instead of silently rerouting. So test the connection after you add it, and keep an eye on your own balance. The full setup is in the BYOK guide.

Zo also includes free models you can run without spending credits, with their own daily allowance. There's a separate guide on which free models are worth using and where they fall short, so I won't relitigate it here.

## The decision in one line

Start on the default. Switch up when the task is genuinely hard or the output ships. Switch down when the work is easy and there's a pile of it. Ignore the context-window number until you actually have too much text to fit, and even then, care more about whether the model can reason than how much it can swallow.

Once the model fits the task, your prompts get shorter and your results get steadier. The rest of Zo Computer 101 lives at jeffkazzee.zo.space/writing. They all live at jeffkazzee.zo.space/writing.
