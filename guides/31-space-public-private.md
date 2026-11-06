---
title: "Public or private? The Space default that trips up every beginner"
id: space-public-private
category: hosting
kind: troubleshooting
date: 2026-06-18
updated: 2026-06-18
excerpt: You built a page on your Space, sent the link to a friend, and they got a login wall. That's not a bug. Here's the rule for what's public, what's private, and how to flip it.
tags: [zo, space, hosting, public, private, troubleshooting, beginner]
related: [first-space-page, zo-hosting-explained, secrets-and-keys]
difficulty: beginner
reading_time: 5
---

You spun up a page on your Space, the URL worked great while you were signed in, you fired it off to a friend, and they hit a login wall. Nothing broke. Your page is doing exactly what Zo Space tells every new page to do, which is stay private until you say otherwise. The confusing part is that "private" looks identical to "public" when you're the one logged in, so you have no way to tell from your own browser that anyone else is locked out.

> A Space page that works for you and 403s everyone else isn't broken. It's a default doing its job.

## The actual rule, in one table

Space has three kinds of things you can put on it, and they each have a different visibility default. This is the whole source of the confusion, because people assume one rule covers all three. It doesn't.

| Thing | Default visibility | Can you change it? |
| --- | --- | --- |
| Pages (React components) | Private. Only you, signed in, can see them. | Yes, you can make a page public. |
| APIs (backend endpoints) | Always public at the network level. | No. An API is reachable by anyone with the URL. |
| Assets (images, files you upload) | Always public. | No. |

The homepage at `yourhandle.zo.space` is the one page that's usually public out of the gate, because a homepage that only you can read is a strange thing to have. Every other page you make starts private.

## The login-wall symptom, decoded

Here's what's happening when your friend gets bounced. The page is still set to private, which means Zo checks for your signed-in session before it renders anything. Your friend has no session, so they get the login screen instead of your content. You never see this because your browser is carrying your session everywhere you go.

| Symptom | What it means | Fix |
| --- | --- | --- |
| Friend sees a login page, you see the real page | The page is still private | Make the page public |
| Page works in your normal browser, dead in incognito | Same thing, your incognito window has no session | Make the page public |
| API route returns data to a stranger you didn't expect | Working as designed, APIs are always public | Add token auth, don't rely on privacy |
| Image you uploaded shows up in a Google search | Assets are always public | Don't upload anything sensitive as an asset |

The fix for the first two is one sentence to Zo: make `[your-page-path]` public. That's it. Ask, and the visibility flips. Send the link again and it loads for everyone.

## Test it the right way before you trust it

The mistake almost everyone makes is checking their own work while logged in, seeing it render, and calling it done. That tells you nothing about what a stranger sees. Two ways to actually verify:

1. Open the page in an incognito or private window. No session, no special treatment. If it loads there, it's public. If it shows a login wall, it's still private.
2. Send it to one person and ask if it opened, before you send it to fifty.

Incognito is the cheaper of the two and it takes ten seconds. Do it every time you intend something to be public.

## The part that can actually hurt you: APIs are never private

Pages have a private default and a public switch. APIs have neither. Every API route on your Space answers to anyone who knows the URL, full stop. There is no owner-only mode for an API, and there's no setting to add one. If your API reads a database, calls a paid service, or returns anything you'd rather a stranger not have, you have to defend it yourself.

The way you defend it is a bearer token. You store a secret in Settings, your API route checks for it in the request header, and it refuses anything that doesn't carry the right token. The endpoint stays publicly reachable, but it returns nothing useful without the key. Two rules that follow from this:

- Never paste an API key, password, or private credential directly into API route code as if the route were a safe hiding spot. It isn't. The route is public and the code runs on a public endpoint.
- Anything genuinely secret goes in Settings as an environment variable, and your code reads it from there. The secret never lives in the route itself, so a curious visitor poking at your URL gets a 401 instead of your credentials.

If you've never set one up, the secrets-and-keys guide walks through where Zo stores environment variables and how a route reads them. Do that before you wire an API to anything that costs money or touches private data.

## Assets are public too, and people forget this

When you upload an image or a file to your Space so a page can use it, that file is public the moment it exists. There's no private asset. If you drop a PDF in there that has a home address or an unredacted invoice on it, the URL to that file works for anyone who finds it, whether or not the page using it is public. Treat the asset bucket like a public folder, because that's what it is. Sensitive files belong in your Files workspace, not uploaded as a Space asset.

## The short version

Pages start private and you can make them public. APIs and assets are always public and you can't change that, so protect API secrets with a token and keep sensitive files out of assets entirely. The login wall your friend hit is the system working, and the fix is one request to Zo away.

If this cleared up the public/private thing for you, the rest of Zo Computer 101 is written the same way, plain about what trips beginners and exactly how to get unstuck. It lives at jeffkazzee.zo.space/writing.
