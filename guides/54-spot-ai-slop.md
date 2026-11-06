---
title: "Spot AI slop in your own output before you ship it"
id: spot-ai-slop
category: working-with-ai
kind: how-to
date: 2026-06-18
updated: 2026-06-18
excerpt: AI writing has tells. Once you can see them, you can't unsee them, and you'll stop shipping text that screams 'a model wrote this.' Here's the field guide to the tells that matter most.
tags: [zo, ai-quality, writing, working-with-ai, beginner]
related: [manual-evaluation, zo-pushback, prompting-zo]
difficulty: beginner
reading_time: 7
---

You can ask Zo to write something, read it back, think "yeah, that's fine," and ship a paragraph that announces to every reader you didn't write it yourself. The output is clean. It scans. And it carries a set of fingerprints that anyone who reads a lot now clocks in about four seconds. This guide teaches you to see those fingerprints in your own drafts, so you catch them before they go out with your name attached.

Slop is not a moral failing of the machine. It's what you get when you accept the first fluent draft and don't push the specifics back in. The model fills the shape of an answer with the most average possible words, because average is what it was trained to produce. The job left over is yours.

> The tell isn't that a model wrote it. The tell is that nobody made it specific afterward.

## The tells, ranked by how often they show up

Here's the field guide. Each one is a pattern you can find with your eyes once you know its name.

| Tell | What it looks like | Why it reads as fake |
| --- | --- | --- |
| Negative parallelism | "This isn't about speed, it's about trust." | The model loves the X/Y seesaw. Real people just say the thing. |
| Rule-of-three padding | "fast, reliable, and scalable" | Three is a rhythm the model reaches for when it has nothing specific to say. |
| Puffery verbs | "stands as," "serves as," "unlocks," "empowers" | Filler dressed up as motion. The sentence works better with the verb deleted. |
| The hedge clause | "it's important to note that" | Pure throat-clearing. Cut it and the sentence loses nothing. |
| Demonstrative wrap-up | "That is the whole point." | The canned essay-ending move. Says nothing, sounds final. |
| Boldface confetti | **random** words **bolded** mid-sentence | The model bolds for emphasis it didn't earn. |
| Em dash everywhere | a sentence, then a dash, then a dependent thought tacked on | A real overuse signal once you start counting them. |

None of these are crimes on their own. Stacked three to a paragraph, they're a confession.

## The two that are harder to catch

A couple of tells hide better, because they're about rhythm instead of words.

**Dead word-echo.** The model repeats a plain word three or more times in one paragraph when it should vary or cut. Watch how often "system," "process," "important," or "powerful" shows up in a short span. A human writing fast reuses words too, but they don't lean on the same one like a crutch across every sentence.

**The metronome.** Every sentence lands at roughly the same length. Fifteen words, then sixteen, then fourteen. It reads smooth and feels dead, because real writing swings. A nine-word sentence followed by a thirty-word one that earns its length, then a fragment. When your draft has no variation in sentence length, a model wrote it and you didn't fix it.

## Before and after

The fix for every tell above is the same two moves: get specific, and vary the rhythm. Watch what that does.

**Before:** "Zo is a powerful tool that empowers users to unlock their full potential and streamline their workflows in terms of productivity."

**After:** "Zo runs a real Linux box you can SSH into, so the script you wrote in chat can be the same script a scheduled automation runs at 7am."

The first sentence could describe any SaaS product launched since 2019. The second one only describes Zo, and it makes a claim you could check.

**Before:** "It's important to note that automations aren't just convenient, they're transformative for your daily routine."

**After:** "An automation is a prompt on a schedule. For example, one can check a status page every 15 minutes and text you only when something flips from green. Most days it says nothing, which is the point."

The hedge is gone. The negative parallelism is gone. What replaced them is a real example with a real cadence and a number you could argue with.

## How to run the check on your own draft

Three passes, ninety seconds total.

1. **Read it out loud.** The metronome and the dead word-echo are obvious to your ear and invisible to your eye. If you sound like a brochure, you are one.
2. **Hunt the seven tells.** Search the literal phrases. Find "it's important," find "not just," count your em dashes, count your bolds. Cut on sight.
3. **The "any product" test.** Take your strongest-sounding sentence and ask whether you could paste it into a competitor's homepage unchanged. If yes, it says nothing. Replace it with a fact only you could write.

That third test is the whole game. The manual evaluation guide makes the same argument about checking AI output for correctness, that the work has to come from you and not the polish. Slop is the writing version of the confident-wrong answer. It looks done, and it isn't.

The specificity has to come from somewhere the model can't reach, which is your actual experience, your actual numbers, the actual file path where the thing broke. Zo can give you a fluent first draft in two seconds. It cannot tell you what happened on your machine last Tuesday. That's the part you bring, and it's the only part that makes the writing yours.

If you want Zo to argue back when a draft is weak instead of cheerfully polishing slop, the pushback guide covers how to set that up. If you want better raw material to edit in the first place, start with the prompting guide.

This is how the rest of Zo Computer 101 is written too: specific, opinionated, no filler dressed up as insight. It lives at jeffkazzee.zo.space/writing.
