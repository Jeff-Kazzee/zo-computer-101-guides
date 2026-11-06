---
title: "No auto-evals, just you and the model: how to judge AI output by hand"
id: manual-evaluation
category: working-with-ai
kind: how-to
order: 1
date: 2026-06-18
updated: 2026-06-18
excerpt: You don't need an eval framework to know if Zo did good work. You need a five-minute reading method that catches the confident-and-wrong answer before it costs you. Here it is.
tags: [evaluation, ai-quality, prompting, working-with-ai, beginners]
related: [build-a-persona, personas-explained, manual-prompting]
difficulty: beginner
reading_time: 7
---

There is a whole industry growing up around evaluating AI output with automated test suites, scoring rubrics, and dashboards that grade one model against another. If you are one person getting real work out of Zo, you probably do not need a full eval stack first. You do need a repeatable reading method, because "looks good to me" is how a confident wrong answer slips into your work and costs you an afternoon later. This guide is that method.

The trap with modern models is specific: the output is fluent. It reads like someone competent wrote it, which makes your brain want to accept it. Fluency is not correctness. The whole skill of manual evaluation is learning to distrust the polish and check the thing underneath it.

> The dangerous output isn't the one that looks wrong. It's the one that looks right and isn't. Fluency is the disguise.

## The five-minute read

Most outputs need one pass, done deliberately. Not skimming for vibe, reading for four specific failures. Here is the order I run them in, hardest-to-spot first.

### 1. Check the claims that sound most authoritative

The sentences delivered with the most confidence are the ones to check first, because confidence is exactly where a model hides a fabrication. A specific number, a named function, a quoted fact, a command. If Zo says "the flag is `--force-sync`," go confirm that flag exists. The fluent specific claim is the highest-risk thing in any output, and it's the easiest to wave through because it sounds so sure.

### 2. Look for what's missing, not just what's wrong

This is the move people skip, and it's the most valuable one. Reviewing for errors catches bad lines. It does not catch the case the output never addressed. Ask: what did I expect to see here that isn't here? A function with no error handling. A plan with no rollback. An email that answers two of my three questions. The gap is invisible if you only read what's on the page, so you have to read against your own expectation of what a complete answer would contain.

### 3. Trace one example all the way through

Do not validate logic in the abstract. Take one concrete input and walk it through whatever Zo produced, by hand. A real row through the script. A real customer through the workflow. One actual case, traced end to end, surfaces the broken edge that reading-for-correctness sails right past. If it's code, run it on one input. If it's a process, walk one item through it. Abstract review lies; a traced example doesn't.

### 4. Read the seams, not the center

AI output is usually strongest in the middle of a task and weakest at the boundaries: the first step, the last step, the error case, the empty case, the handoff to something else. When you're short on time, read the seams and skim the center. That's where the bugs and the hand-waving live.

## The tell that you're being snowed

A reliable signal something is off: the output is longer and more elaborate than the problem deserves. When a model is unsure, it often pads. More caveats, more structure, more restatement, a confident summary that mostly repeats the question back to you. Length where the answer should be short is a flag. So is a conclusion that doesn't actually commit to anything. If you finish reading and can't say what the output is claiming, that's not your failure to understand, it's often the output failing to say.

## Make Zo evaluate itself (then distrust that too)

Ask Zo to critique its own output, then check whether the flaw it names is real. "What's the weakest part of this?" "What did you assume that might be wrong?" "Where would this break?" Models are frequently better at finding the flaw than at avoiding it in the first place, so this catches real problems.

## When the stakes are high, raise the bar

The five-minute read is for ordinary work. When the output is going to ship publicly, touch money, or be hard to undo, escalate:

- **Get a second model.** Have a different model review the first one's output. Disagreement between two models is a precise map of where to look.
- **Make it show its work.** Ask Zo to explain why, not just what. Reasoning you can follow is reasoning you can check. An answer with no path to it is an answer you're taking on faith.
- **Sleep on it.** The confident-wrong output is most convincing in the moment you receive it. Re-reading cold an hour later is the cheapest quality check there is.

## The one habit to build

Before you accept anything that matters, ask the missing-case question: "what would I expect a complete, correct version of this to include that I should check is here?" That single question does more than any rubric, because it turns passive reading into active checking, and active checking is the whole game. You are not grading the model. You are protecting the work that has your name on it.

If this saved you from trusting one confident wrong answer, the rest of Zo Computer 101 is built the same way: specific, tested, no hand-waving. It lives at jeffkazzee.zo.space/writing.
