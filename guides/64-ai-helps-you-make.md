---
title: "AI should help you make things, not make things for you"
id: ai-helps-you-make
category: opinion
kind: opinion
date: 2026-06-18
updated: 2026-06-18
excerpt: The loud version of AI is the one that replaces the person. The useful version is the one that hands the person more leverage. Here's the difference, and why the second one is the only one worth building on.
tags: [zo, ai, opinion, anti-slop, craft]
related: [spot-ai-slop, what-zo-actually-is, manual-evaluation]
difficulty: beginner
reading_time: 7
---

The pitch you keep hearing is that AI will run the whole thing for you. Write the post, answer the customers, build the product, ship the company, while you sleep. I think that version is mostly garbage, and I say that as someone who builds with these tools every day and would be lost without them.

Side with the skeptic for a second, because the skeptic is right about the part that matters. When you ask a model to do the entire job end to end, with no taste and no judgment in the loop, you get output that is fluent and hollow. It reads fine. It says nothing. It could have been generated for anyone, about anything, which is exactly the problem.

> Specificity and the final call are what make work yours. Full automation quietly throws both away.

## Where the slop comes from

The slop is not a bug in the model. It is what you get when you remove the person.

A good piece of writing has a position someone could argue with. A good product has an opinion about who it is for and who it is not for. A good email answers the actual question instead of three adjacent ones. None of that survives "AI, handle this for me," because the model has no stake in the outcome and no taste of its own to defend. It optimizes for plausible. Plausible is the floor, not the ceiling.

You can see it the moment you read closely. The post that hits every SEO beat and lands on no actual claim. The landing page that describes a "powerful solution for modern teams" and could be selling a CRM or a yoga mat. The reply that is polite, complete, and useless. If you want the full field guide for catching this, that is what the spotting slop guide is for. The short version: the absence of specifics is the tell.

## The version that actually works

Now the narrow useful version, the one I will defend. AI is leverage. It does the tedious 80 percent so you can spend your judgment on the 20 percent that decides whether the thing is any good.

Here is the split I actually run with:

| Hand to the model | Keep for yourself |
| --- | --- |
| Boilerplate, scaffolding, first drafts | The position, the argument, the point of the thing |
| Research legwork and summarizing sources | What's true, what's load-bearing, what to cut |
| Reformatting, renaming, converting files | Taste: what stays, what's too clever, what's a lie |
| The dumb mechanical busywork | The final call, with your name on it |

The model drafts, pulls sources, generates the function. You decide what it is actually about, which two of its ten sources are load-bearing, and whether the error case it skipped will wreck you in production, because it usually skipped them.

That last part is the whole job, and it does not go away. The leverage is real only if you stay in the loop to catch what the model got confidently wrong. That is its own skill, and I wrote the manual evaluation guide about exactly how to do it in five minutes without an eval framework.

## Two ways to write the same post

Same tool, same prompt budget, completely different result depending on where the human sits.

1. **Slop version.** "Write me a blog post about AI coding tools." You paste whatever comes out. It has a title-case heading, a tidy intro, three bullet points that restate the intro, and a conclusion that restates the bullets. You ship it. Nobody remembers it, including you.

2. **Leverage version.** You decide the one claim worth making, say, that auto-generated tests give people false confidence. You make the model draft around that claim, then you rip out every sentence that hedges, add the specific failure you actually hit, and cut the post by a third. The model did the typing. You did the thinking. The piece sounds like a person because a person made the calls.

The difference is not the model. It is whether you treated it as the maker or the assistant.

## Why this is the only version worth building on

A tool that replaces you has no use for your taste, which means it has no way to get better than average, because average is the whole training target. A tool that amplifies you gets better as you do. Your judgment is the input that does not commoditize. Everyone has the same model. Almost nobody brings the same specificity, the same opinion, the same willingness to cut the thing that is technically fine and still wrong.

That is why I use [Zo Computer](https://docs.zocomputer.com) the way I do. Not to push a button and walk away. To compress the busywork, the file wrangling, the first 80 percent of a project, so the part that is mine stays mine. The drafts are fast. The taste is slow, and it should be, because the taste is the point. If you want the plain explanation of what the tool even is before you decide how to use it, read what Zo actually is.

Pro-tool, anti-slop. Those two things only contradict each other if you let the machine do the making. Keep the making, hand off the grind, and the same AI that produces forgettable mush for one person produces work worth signing for another.

The rest of Zo Computer 101 argues the same way, pro-tool and anti-slop, with the person doing the making always in the frame. It lives at jeffkazzee.zo.space/writing.
