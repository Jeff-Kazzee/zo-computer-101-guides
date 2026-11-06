---
title: "Status codes when a model breaks in Zo (400 / 401 / 404 / 429)"
id: model-error-codes-card
category: reference
kind: reference
date: 2026-06-18
updated: 2026-06-18
excerpt: A custom model endpoint fails and spits a number at you. Here's what 400, 401, 404, and 429 actually mean in Zo, and the exact thing to check for each before you waste an hour.
tags: [zo, models, byok, troubleshooting, reference, error-codes]
related: [byok-setup, picking-a-model, secrets-and-keys]
difficulty: beginner
reading_time: 4
---

You added a custom model in Zo under Settings, AI, Providers, Bring Your Own Key, and the request came back as a bare number instead of a reply. That status code is the whole message. Once you can read it, most of these break in under a minute, because each code points at exactly one part of the config you filled in: the model ID, the key, the base URL, or the provider's rate limit. This card maps the four you'll actually hit to the one thing to check first.

The reason this matters with bring-your-own-key models specifically: Zo's built-in models can't throw these at you. Custom models don't fall back to Zo's models when they fail, so a broken endpoint stays broken until you fix the config. The error code is your fastest path to which field you got wrong.

> The number is the provider pointing at the one box you filled in wrong. Read it before you touch anything else.

## The table

| Code | What it usually means | First thing to check |
| ---- | --------------------- | -------------------- |
| 400 | Wrong model ID | The slash convention for your provider |
| 401 | Bad or missing API key | The key is in the API Key field, not pasted into the Base URL |
| 404 | Wrong base URL | Trailing slash, and `/v1` vs `/v1beta` |
| 429 | Rate limited | You're on a free tier that's tapped out |
| (hangs) | Provider problem, not yours | Try a different model or provider |

## 400, the model ID is in the wrong shape

A 400 almost always means the Model ID field is formatted in a way the provider doesn't recognize. The trap is the prefix convention, and it differs by provider.

OpenRouter wants `provider/model`, like `mistralai/ministral-14b-2512` or `moonshotai/kimi-k2-instruct-0905`. Drop the `mistralai/` part and you get a 400, because OpenRouter has no idea which `ministral` you mean. Talk to OpenAI's own endpoint and it wants the bare ID, `gpt-4o`, no prefix at all. Paste an OpenRouter-style slug into a provider that wants the bare name and the same 400 comes back.

The fix:

1. Open the model's page on your provider and copy the exact ID string they show.
2. Match the slash convention. Slug-with-slash for aggregators like OpenRouter, bare name for the provider's own API.
3. Re-test before changing anything else.

## 401, the key is wrong, missing, or in the wrong field

401 is authentication. Either the key is bad, or it never reached the request. The easiest way to land here is pasting the key into the Base URL field by accident, which empties the API Key field and malforms the URL in one move.

Check, in this order:

1. The key sits in the **API Key** field, by itself, nothing else in it.
2. The **Base URL** field has only a URL, no `Bearer`, no key fragment trailing on the end.
3. The key is still live. Free keys get rotated or revoked, and a dead key returns 401, not a friendly "expired" message.

Anthropic-format and OpenAI-format keys look different and aren't interchangeable. If you switched the Format dropdown but kept the old key, that's a 401 too.

## 404, the base URL is pointing at nothing

404 means Zo reached a server and that server has no endpoint at the path you gave. This is a Base URL problem nine times out of ten.

The usual offenders:

- **Trailing slash.** Some providers choke on `https://api.openai.com/v1/`, some require it. If one form 404s, try the other.
- **Wrong path version.** OpenAI-compatible endpoints live under `/v1`. Some Google-flavored endpoints use `/v1beta`. Send a `/v1` request to a `/v1beta`-only path and you get a 404 even though the host is correct.
- **Right host, no path.** `https://openrouter.ai` alone is not the endpoint. It's `https://openrouter.ai/api/v1`.

Reference values that work: OpenRouter is `https://openrouter.ai/api/v1`, OpenAI is `https://api.openai.com/v1`, Anthropic is `https://api.anthropic.com`. Copy the one for your provider and stop guessing.

## 429, you got rate limited

429 means too many requests in too short a window. Your config is fine. The provider is throttling you.

Free tiers hit this first and hardest. A free OpenRouter key or a free-tier provider slot will 429 after a handful of calls, sometimes mid-conversation, because the per-minute or per-day ceiling is low by design. Two ways out:

1. **Wait.** The window resets. A minute is usually enough for a per-minute cap, longer for a daily one.
2. **Switch to a paid path.** Point the same Model ID at the provider's direct paid endpoint, or move to a model that isn't on the saturated free tier. The free-models route is great for tinkering and bad for anything you need to finish on a deadline.

## When it just hangs

No code, no response, the request sits there. That's usually the provider having a bad day, not your setup. Endpoints go down, free pools get congested, a specific model gets pulled. Don't burn an hour rechecking a config that's correct. Swap in a different model or a different provider and see if the request completes. If a known-good model works and the original still hangs, the problem is upstream and waiting is your only move.

## The two-minute triage

Before you change a single field, read the number and go straight to its row:

- **400**, fix the Model ID prefix.
- **401**, the key field.
- **404**, the Base URL path.
- **429**, wait or leave the free tier.
- **Hangs**, try another model.

Setting these up the first time is the part that trips people, and it's covered in the bring-your-own-key guide. If you're still deciding which model to point at in the first place, the picking-a-model guide walks through the tradeoffs. The rest of Zo Computer 101 is built the same way as this card, specific and tested with nothing hand-waved, and it lives at jeffkazzee.zo.space/writing.
