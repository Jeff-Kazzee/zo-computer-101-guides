---
title: "Bring your own key: run Zo on your own model provider"
id: byok-setup
category: working-with-ai
kind: how-to
date: 2026-06-18
updated: 2026-06-18
excerpt: Already paying for Claude, OpenAI, or Gemini? You can point Zo at your own API key on any plan and skip Zo-billed model usage for that provider. Here's the setup and the gotchas.
tags: [zo, byok, models, api-keys, working-with-ai, beginner]
related: [picking-a-model, secrets-and-keys, prompting-zo]
difficulty: beginner
reading_time: 6
---

If you already pay OpenAI, Anthropic, or Google for model access, you are sitting on capacity you can route straight into Zo. Bring your own key lets you plug your provider API key into Zo and run chat on that key instead of Zo-billed usage, and it works on every plan, the free one included. The setup takes about three minutes. The part that wastes an afternoon is one wrong character in a base URL, so most of this guide is about getting that right the first time.

> Bring your own key is the cheapest config change in Zo. A wrong base URL is the most expensive typo.

## What you can connect

The Bring Your Own Key area takes keys from the providers you already use. OpenAI, Anthropic, OpenRouter, Azure Foundry, Groq, Cerebras, and Google all work, plus any custom endpoint that speaks the OpenAI or Anthropic API shape. That last one matters more than it looks, because a huge number of hosts (gateways, self-run inference, smaller labs) expose an OpenAI-compatible endpoint, which means they drop into Zo even though they are not on the list by name.

If you are on a paid plan, there is a second path worth knowing: you can connect a coding-agent subscription like Claude Code, Codex, or Gemini CLI and use that allotment from inside Zo. That is a different lane from a raw API key. This guide is about the raw key.

One thing to be clear about up front. A custom model on your own key does not fall back to Zo's built-in models if it fails. If your key is dead or out of credits, that model just errors. There is no safety net behind it, which is the tradeoff for not paying Zo-billed usage.

## Add the key

Open Settings and go to the AI providers area, then the Bring Your Own Key form. You are filling in five fields:

| Field | What it wants |
| --- | --- |
| Name | Whatever you want to see in the model picker, like `my-openrouter-sonnet` |
| Base URL | The provider's API endpoint root |
| API Key | The key you generated in the provider's dashboard |
| Format | OpenAI, Anthropic, or Groq, depending on the API shape |
| Model ID | The exact model identifier the provider expects |

Save the provider, then run Zo's connection test. Do not skip the test. The test is the whole point of the test, because it tells you in two seconds whether the key, the URL, and the model ID actually agree with each other, instead of you discovering the mismatch three messages into real work.

Once it passes, the model shows up in the picker in chat. Select it the way you would pick any other model.

## The base URL and model ID gotchas

This is where people lose time, so read it slowly.

The base URL is not the provider's homepage. It is the API root, and providers differ on whether the version path is included. OpenAI-style endpoints usually end in `/v1`. A trailing slash, a missing `/v1`, or pasting a docs page URL instead of the API root all produce the same symptom: errors that look like the key is broken when the key is fine.

The model ID has to match the provider's identifier exactly, character for character. Some providers namespace the model with a prefix, so the same underlying model reads differently depending on who is hosting it. Copy the ID from the provider's model list rather than typing it from memory, because a model name that "should obviously work" is exactly the kind of thing that returns a 404.

Here is the decoder for what you will see if something is off:

- **400** usually means the request shape is wrong for that format. Check the Format field matches the endpoint (OpenAI format pointed at an Anthropic endpoint throws this).
- **401** is auth. The key is missing, pasted with a stray space, or revoked. Regenerate it and paste clean.
- **404** is the model ID or the path. Either the base URL is missing the version segment, or the Model ID does not exist on that provider.

If you want the longer version of every status code Zo can surface from a model, the model error codes card breaks them down. For finding good cheap or free model IDs to drop into the form, the free models guide is the one to read, because OpenRouter in particular has a rotating set worth knowing.

## A working example shape

Without inventing anyone's exact strings, the pattern for an OpenAI-compatible provider looks like this:

1. **Base URL**: the API root ending in `/v1` (for example, an OpenAI-style host).
2. **Format**: OpenAI.
3. **API Key**: the key from that provider's dashboard.
4. **Model ID**: copied verbatim from the provider's model list, including any prefix.

Anthropic-format endpoints follow the same idea with the Anthropic base URL and Format set to Anthropic. Groq has its own Format option. The fields do not change. Only the three values you paste into them do.

## A note on keys and safety

Your provider key is a credential with real spending attached. Treat it like one. Zo stores it for the model config, and you should never paste it into a chat message, a file you might publish, or anywhere it could end up in version control. If you want the full discipline on this, the secrets and keys guide covers where credentials belong and where they do not.

## Why bother

Two honest reasons. If you already have a subscription with headroom, routing it through your own key means you stop paying twice for the same tokens. And if you have a specific model you trust for a specific job, bring your own key is how you pin Zo to it instead of taking whatever the default picker offers. Which model to actually pick for which task is its own question, and the picking a model guide is where that lives.

Set it up once, run the test, and you are done until the key expires. If this got you off Zo-billed usage and onto capacity you already pay for, the rest of Zo Computer 101 is written to the same standard: specific, tested, no hand-waving. It lives at jeffkazzee.zo.space/writing.
