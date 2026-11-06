---
title: "Credits, plans, and not getting a surprise bill"
id: credits-and-plans
category: orientation
kind: explainer
date: 2026-06-18
updated: 2026-06-18
excerpt: Zo bills for two things: the computer and the AI that drives it. Here's how the plans and credits actually work, and how to use premium models without a surprise charge.
tags: [zo, billing, credits, plans, orientation, beginner]
related: [what-zo-actually-is, byok-setup, first-hour-in-zo]
difficulty: beginner
reading_time: 6
---

Most people who get surprised by a Zo bill made the same mistake: they put a card on file, switched to a premium model, and forgot that premium AI is metered. The good news is that the whole billing system has exactly two moving parts, and once you see them you can run premium models all day and still know what you'll owe. Here's how the money actually works.

Zo charges for two separate things. One is the cloud computer itself, the CPU, memory, storage, and any services you keep running. The other is the AI you use to drive it. Those are priced differently and behave differently, and conflating them is where the confusion starts.

> The computer has a flat monthly price. The AI is metered. Keep those two ideas apart and billing stops being scary.

## The two things you pay for

The plan you pick sets your computer: how much compute you get, how many services stay running, whether the machine sleeps when idle. The AI is the part that meters. Premium built-in models bill at-cost, meaning Zo charges you the same rate it pays the provider, so there's no markup hiding in the number. Free models cost nothing up to a daily allowance.

Every plan, including Free, gets 100GB of storage, MCP server access, and the ability to bring your own LLM keys. Here's how the four tiers compare:

| Plan  | Price    | AI credits included | Hosted services | Compute            |
| ----- | -------- | ------------------- | --------------- | ------------------ |
| Free  | $0       | none (daily free-model allowance) | 1   | limited, sleeps when idle |
| Basic | $18/mo   | $10/mo              | 5               | always-on, 4 CPU / 32GB |
| Pro   | $64/mo   | $40/mo              | 10              | 16 CPU / 128GB     |
| Ultra | $200/mo  | $100/mo             | 50              | 64 CPU / 512GB     |

The included credits on a paid plan are AI credits, not a discount on the computer. Basic gives you $10/mo of premium AI usage baked in. Burn through that and you keep going on your payment method at the same at-cost rate.

## Free has two completely different modes

This is the part that trips up new users, because "Free" describes two states depending on whether you've added a payment method.

Without a card on file, you're capped at free models, used up to a daily allowance. You can do real work this way. The computer still sleeps when idle and the compute is limited, but it costs nothing and nothing can charge you.

Add a working payment method and your monthly price is still $0, except now the premium built-in models run pay-as-you-go. Same resource limits, same sleep-when-idle behavior, but the AI side is now metered against your card. That switch, from free-models-only to a live metered card, is the exact moment a surprise bill becomes possible.

## How a charge actually gets paid

When you run a premium model, Zo draws down in a fixed order:

1. **Free allowance first.** Anything covered by your daily free-model usage costs nothing.
2. **AI credits next.** If you're on a paid plan, the included monthly credits get spent before anything hits your card.
3. **Your payment method last.** Once the allowance and credits are gone, premium usage bills to your card at-cost.

So a Basic user has $10/mo of cushion before a single cent touches their payment method. A Free user with a card on file has no credit cushion at all, which is why the metered charges start sooner there.

## How to use premium models without the surprise

The thing to actually watch is premium-model usage on a metered payment method. That's the only line that can grow without you noticing. Three ways to keep it in check:

- **Lean on the free allowance for routine work.** Drafting, quick questions, file edits, the stuff that doesn't need a frontier model. Save the premium model for when the quality difference matters.
- **Bring your own key.** BYOK works on every plan, including Free. Point Zo at your own OpenAI, Anthropic, or Gemini API key and that usage bills to the provider directly, skipping Zo's metered billing entirely. If you already pay for an API account, this is the cleanest way to run premium models with zero Zo-side AI charges.
- **Let the included credits do the work.** On a paid plan, the monthly credits absorb a real amount of premium usage before your card sees anything. For a lot of people, Basic's $10/mo covers a normal month without ever touching the payment method.

BYOK is the lever I'd reach for if the metered number ever made me nervous. The setup is straightforward, and the BYOK setup guide walks through connecting an OpenAI-compatible, Anthropic-compatible, or Groq endpoint. One caveat worth knowing up front: a custom model won't fall back to Zo's built-in models if your key fails or runs out of credit, so keep that account funded.

## Changing plans

Plans change in Settings, under Billing. Changes are immediate and prorated, so upgrading mid-month to get more credits or always-on compute doesn't cost you a clean month, and downgrading refunds the unused portion. If you spun up Zo on Free to kick the tires and want the machine to stop sleeping, Basic is the jump that gets you always-on compute plus that $10 credit cushion.

The honest summary: paid plans are the simplest way to use premium AI because the credits come up front and the limits are higher, but they aren't the only way. A funded Free account with BYOK can run frontier models all day for whatever your own provider charges. Pick the shape that matches how you actually work.

If you're still figuring out what this machine even is before you worry about paying for it, the what Zo actually is guide is the better starting point, and the first hour in Zo guide gets you doing real work fast. The rest of Zo Computer 101 is written the same way, specific and tested, at jeffkazzee.zo.space/writing.
