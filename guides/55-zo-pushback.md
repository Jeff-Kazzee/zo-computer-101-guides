---
title: "Teach Zo to push back on you instead of agreeing"
id: zo-pushback
category: working-with-ai
kind: how-to
date: 2026-06-18
updated: 2026-06-18
excerpt: A yes-man AI will happily help you build the wrong thing beautifully. Here's how to set Zo up to challenge weak ideas, flag risks, and tell you when you're solving the wrong problem.
tags: [zo, prompting, rules, working-with-ai, beginner]
related: [prompting-zo, manual-evaluation, rules-explained]
difficulty: beginner
reading_time: 6
---

The default failure mode of a capable AI is not getting the answer wrong. It is agreeing with you so smoothly that you never find out the plan was bad until you have built half of it. Models are trained to be helpful and pleasant, which in practice means they slide toward yes. You ask "should I do it this way," and Zo finds the version of the world where that way is reasonable, and tells you about that one. The wrong-problem error is the expensive one, and a polite assistant will never catch it for you unless you make it.

> A yes-man with root access to your workspace is not an assistant. It is a faster way to ship a mistake.

So the job is to install friction on purpose. You have to ask for disagreement, bake it into how Zo behaves, and then actually mean it when the pushback shows up.

## Bake it into a Rule so you don't have to remember

The most durable fix is a Rule. Rules apply across your conversations, so you set the behavior once and it follows you instead of depending on whether you remembered to ask nicely today. Go to Settings, AI, Rules, and create the Rule there. Here is text that does real work:

> Before executing any request that involves a plan, an architecture choice, or public output, first tell me the strongest objection to it. If you think the request will produce worse output or solves the wrong problem, say so plainly and give one concrete alternative. Do not soften it. I would rather hear the flaw now than ship it.

That last line matters more than it looks. Without "do not soften it," Zo will technically comply and bury the objection in three paragraphs of reassurance. You want the criticism load-bearing, not decorative.

A second Rule worth adding covers the quiet failure, the thing the output skipped:

> When you finish a task, name one thing you left out or assumed, and one case that would break it.

That single habit turns every response into a small self-audit. It pairs directly with the manual evaluation guide, where the whole skill is reading for what is missing instead of what is merely wrong. A Rule that forces Zo to name the gap does half that reading for you.

## Build a persona that argues for a living

Rules set a baseline. A persona changes the whole posture. A persona is a prompt plus a personality plus a tool set, and you can make one whose entire reason to exist is to disagree with you well.

Drop something like this into the persona prompt:

> You are a skeptical senior reviewer. Your job is to find what is wrong before it costs me. Lead with the biggest risk. Argue the other side of any decision I bring you. If my idea is good, say so in one line and move on. If it is weak, take it apart and propose something better. Never flatter. Treat agreement as the last resort, not the first.

Give it the Read only preset for pure critique. If it also needs to see your files and search the web, use Workspace, but know that Workspace can still edit files; it only blocks shell and messaging. Then when you have a plan you are too excited about, switch to that persona and let it knock holes in it. The personas guide walks through creating and scoping one if you have not built one yet.

Two personas, used in sequence, is the strongest version of this. One builds. One reviews. You stop being the only critic in the room.

## When you just want it now, ask in the chat

You don't need setup for one-off pushback. You need the right question. The phrasing changes the answer, because a question that assumes the idea is good gets a defense, and a question that assumes it is flawed gets a critique.

| Instead of asking | Ask this |
| --- | --- |
| "Is this plan good?" | "What is the strongest objection to this plan?" |
| "Can you build X?" | "What am I not seeing here? Argue the other side." |
| "Does this look right?" | "Where does this break, and what did I assume that might be wrong?" |
| "Any feedback?" | "If you had to kill one part of this, which part and why?" |

"Is this good" is a trap. It invites yes. "What is wrong with this" gives Zo permission to do the thing it was avoiding to keep you happy.

A move I lean on: after Zo critiques something, make it critique its own critique. "Now argue against what you just said." You are not looking for a winner. You are looking for the map of where the real uncertainty lives, and disagreement between two confident answers is exactly that map.

## The limit nobody admits

None of this works if you don't want it to. That is the honest catch. You can write the perfect Rule and build the perfect skeptic persona and then override every objection it raises because you already decided. The mechanism makes pushback show up on time. It cannot make you listen.

So the standard I hold, and the one worth holding yourself to: silence is not loyalty, it is negligence. A tool that only ever agrees with you is not protecting your work. It is rubber-stamping it. The whole point of teaching Zo to push back is to have one voice in the loop that is not invested in your being right, so you can be the one who decides which objections to take and which to overrule on purpose.

Set the Rule today. Build the persona this week. Then the next time Zo tells you the plan is wrong, sit with it for a second before you argue back.

If this got you one good objection you would have missed, the rest of Zo Computer 101 runs on the same wiring. It lives at jeffkazzee.zo.space/writing.
