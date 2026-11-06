---
title: "Build a persona with AI, then tune it until Zo performs"
id: build-a-persona
category: personas
kind: how-to
order: 2
date: 2026-06-18
updated: 2026-06-18
excerpt: You don't write a persona from a blank page. You have Zo draft it, then you tune it by reading what it produces. Here's the build loop, the prompt structure that works, and how to fix a persona that's underperforming.
tags: [personas, prompting, ai-quality, evaluation, beginners]
related: [personas-explained, manual-evaluation, prompting-zo]
difficulty: beginner
reading_time: 7
---

A persona is not a prompt you finish. It is a prompt you test on a real task, then tighten where it fails. People write one clever paragraph, save it, and wonder why the output still drifts. The fix is a hire's loop: write a rough job description, watch the work, correct what's off. It takes minutes instead of weeks, and Zo writes the first draft of its own job description for you.

> You are not writing a perfect prompt. You are starting a feedback loop. The first draft is supposed to be wrong in small ways, and fixing those is the actual work.

## Step 1: let Zo draft it

Don't start from a blank box. Tell Zo what you want and have it write the persona prompt:

```
Draft a persona prompt for a [job]. It should [what it's for].
It needs to know [standing context]. Its voice is [tone].
It should never [hard constraints]. Ask me anything unclear before you write it.
```

That last line matters. A good drafting pass asks you the two or three questions that sharpen the persona before it commits. You answer, it drafts, and you have a starting prompt that is already eighty percent there. This is the build-with-AI move: the AI is better at turning your intent into a structured prompt than you are at writing one cold.

## Step 2: the prompt structure that holds up

Whether Zo drafts it or you do, the personas that perform share a shape:

- **Identity in one line.** Who this is and what it's for. "You are a blunt copy editor for my newsletter."
- **Standing context.** The stuff you're tired of repeating. Your audience, your product, your constraints, the facts it should always have loaded.
- **How it behaves.** The voice and the method. Does it ask before acting, or just go? Does it explain its reasoning or stay terse?
- **Hard limits.** The "never do this" list. Stronger than preferences. "Never send anything without showing me first." "Never invent statistics."
- **What good output looks like.** One concrete example of a great response beats a paragraph describing one.

## Step 3: set the keys to match the job

Before you run it, scope it. A persona's permissions are part of its performance, not just its safety. A writing persona with shell access and messaging scopes is a persona that can wander off task. Give it `files:read` and `files:write` and stop. The narrower the keyring, the more focused the work, and the safer it is to leave running. (The personas explainer covers the full scope list; the rule here is grant the job, nothing more.)

## Step 4: tune by reading the output

Here's where most people quit too early. You run the persona, the first few results are *almost* right, and you assume the prompt is just how it is. It isn't. Every "almost" is a tuning signal:

- Output too long? Add "be terse, no preamble" to behavior.
- Keeps hedging? Add "state your actual opinion, don't list options."
- Drifts off your style? Your voice section is too vague. Add a real example of the voice you want.
- Forgets context you gave once? That context belongs *in the persona prompt*, not in the chat.
- Asks permission for everything? Tell it which actions are pre-approved.

The loop is: run it on a real task, read the result like an editor, find the one thing most off, fix that line in the prompt, run again. Three or four passes and a mediocre persona becomes one you trust. You are not rewriting; you are correcting one thing at a time, which is faster and teaches you what actually moved the needle.

## Step 5: when it's still underperforming

If tuning the prompt isn't fixing it, the problem is usually one of three things, in order of likelihood:

1. **The context is missing, not the instruction.** The persona can't do good work on facts it doesn't have. Feed it the real material, don't just describe the material.
2. **The model is wrong for the job.** A persona can prefer a specific model. A reasoning-heavy job on a fast-but-shallow model underperforms no matter how good the prompt is. Switch the persona's model and re-test.
3. **You're asking one persona to do two jobs.** A persona that both researches and writes and reviews is three personas wearing a trenchcoat. Split it. Focused personas outperform a single do-everything one every time.

## The honest part about "performance"

There's no magic word that makes Zo smarter. Persona tuning is not a cheat code; it's removing the friction between what you want and what Zo produces. A well-built persona performs better because it starts every task with the right context, the right constraints, and only the tools it needs, so Zo isn't guessing at any of that. That's the whole mechanism. No secret, just less ambiguity.

Build one real persona this way, end to end, on a job you actually do. Have Zo draft it, scope it tight, run it on a live task, and tune three times by reading the output. Once you can tune one persona on one real task, you can reuse the same process everywhere else.

The tuning loop only works if you can actually tell good output from bad, which is its own skill. That's the next guide: judging AI output by hand, no eval suite required. It's at jeffkazzee.zo.space/writing.
