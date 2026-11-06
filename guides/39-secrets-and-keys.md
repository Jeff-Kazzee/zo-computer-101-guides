---
title: "Secrets and API keys: where they go so they don't leak"
id: secrets-and-keys
category: integrations
kind: how-to
date: 2026-06-18
updated: 2026-06-18
excerpt: Hardcode an API key in a route and you just published it to anyone who views your site. Here's where keys actually belong on Zo, and the public-API-route trap that leaks them.
tags: [zo, secrets, api-keys, security, beginner]
related: [connect-a-plugin, space-public-private, zo-plugins-integrations]
difficulty: beginner
reading_time: 6
---

Paste an API key straight into a Space API route and you didn't store a secret. You published one. API routes on Zo are public at the network level, so the moment that code is live, the key inside it is readable by anyone who thinks to look. The fix is boring and takes about thirty seconds, and almost nobody does it the first time because the broken way works fine right up until it doesn't.

> A secret in your code isn't hidden. It's shipped. The only question is who reads it first, you or someone else.

## Where a key actually goes

Third-party keys, tokens, and credentials live in one place: **Settings > Advanced**, in the **Secrets** area. You give it a name and a value, Zo stores it as an environment variable, and your code reads it at runtime instead of carrying it around in plain text.

Name them like environment variables, because that's what they become:

| You're connecting | Secret name | Read it as |
| --- | --- | --- |
| OpenAI | `OPENAI_API_KEY` | `process.env.OPENAI_API_KEY` |
| Stripe | `STRIPE_SECRET_KEY` | `process.env.STRIPE_SECRET_KEY` |
| Some random API | `WEATHER_API_KEY` | `process.env.WEATHER_API_KEY` |

In a Space or Site route written in TypeScript, you reach for it like this:

```typescript
const key = process.env.OPENAI_API_KEY;
if (!key) return c.json({ error: "missing key" }, 500);
```

Python is the same idea with `os.environ["OPENAI_API_KEY"]`. The value never appears in the file. It's pulled from the environment when the route runs, which means the code you can see and the secret it uses are two separate things. That separation is the whole point.

There's a second bin in the same Settings > Advanced screen called **Access Tokens**. Different job. Those are for letting external tools reach into your Zo, like wiring up the MCP server so Claude Code or Cursor can hit your files and tools. A weather API key is a Secret. A token that lets your laptop's editor talk to your Zo is an Access Token. Don't cross the wires.

## The trap that leaks keys anyway

Putting the key in Secrets fixes storage. It does not fix a route that hands the key back out. This is the part that bites people who did everything else right.

Every API route on your Space is public at the network level by default. No login wall sits in front of it by default. So both of these are live exposures:

1. **The key is hardcoded in the route.** Even reading it from `process.env` doesn't help if you also left the literal string in a comment, a fallback, or a debug line. `const key = process.env.STRIPE_SECRET_KEY || "sk_live_abc123"` ships that fallback to the world.
2. **The route returns sensitive data with no auth.** You build `/api/orders` that dumps your Stripe order list as JSON. It works. It's also a URL anyone can curl. The key never leaked, but everything the key was protecting just did.

The first one is a fluency problem, the kind of line that looks fine in the editor and is a disaster in production. The second is sneakier, because the code is clean and the leak is the design.

## How to lock a route down

If a route touches money, private data, or a write action, gate it with a bearer token. Make a long random string, save it as a Secret like `MY_API_SECRET`, and check it on every request:

```typescript
const auth = c.req.header("authorization");
if (auth !== `Bearer ${process.env.MY_API_SECRET}`) {
  return c.json({ error: "unauthorized" }, 401);
}
```

Now the route answers only to callers who send `Authorization: Bearer <your-secret>`. Everyone else gets a 401. For real production code you'd want a constant-time comparison so you're not leaking timing information, but the shape above is the idea: nothing sensitive happens until the caller proves they're allowed.

If a page just shows public content, leave it public. Don't bolt auth onto things that don't need it. The rule is narrow: secrets and side effects get a gate, brochure pages don't. The public vs private pages guide walks the visibility side of this in more depth.

## The three things to never do

Short list, because it's the list that actually causes incidents.

- **Never paste a key into code that ships.** Not in a route, not in a Site source file, not in a frontend component where it ends up in the browser bundle. If a user can view-source their way to it, it's gone.
- **Never commit a key to git.** Once it's in history, deleting the line doesn't remove it, the old commit still has it. Rotate the key and assume it's burned.
- **Never echo a key into logs.** `console.log(process.env.OPENAI_API_KEY)` writes your secret to a log file in plaintext. Same for `env` and `printenv` dumps. Log that a key exists if you must, never what it is.

If a key does leak, the response is always the same and you should do it fast: go to the provider, revoke the old key, generate a new one, update the Secret in Settings > Advanced. The compromised key keeps working until you kill it, so the clock matters more than the embarrassment.

The honest version of secret management is that the storage part is easy and the public-route part is where people get burned. Get both right and you've closed the gap that leaks most keys. The rest of Zo Computer 101 treats security the same way, concrete rather than scary. It all lives at jeffkazzee.zo.space/writing.
