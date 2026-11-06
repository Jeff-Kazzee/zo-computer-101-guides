---
title: "Your first Zo Space page in ten minutes"
id: first-space-page
category: hosting
kind: how-to
date: 2026-06-18
updated: 2026-06-18
excerpt: Every Zo account comes with a personal site at yourhandle.zo.space. Here's how to put a real page on it in ten minutes by asking, plus the public/private gotcha nobody warns you about.
tags: [zo, space, hosting, beginner, web]
related: [zo-hosting-explained, space-public-private, space-to-site]
difficulty: beginner
reading_time: 6
---

You already own a website and you probably don't know it. Every Zo account ships with a personal domain at `yourhandle.zo.space`, sitting there empty, no project to create and no deploy step to learn. This guide takes you from empty to a real live page in about ten minutes, and it warns you about the one setting that traps almost everyone the first time.

> The page goes live the second Zo finishes writing it. Whether anyone but you can see it is a different question, and that question is where beginners lose an afternoon.

## What Space actually is

Space is the lightweight end of Zo hosting. No folder to scaffold, no framework to pick, no build to wait on. You ask for a page in plain English and Zo writes it, styles it, and serves it at your handle. Under the hood the pages are React components styled with Tailwind, with icons from Lucide if you want them, but you do not touch any of that unless you feel like it. The whole point is that you describe the thing and it exists.

If you want the bigger picture of where Space sits next to Sites, Services, and zo.pub, the hosting overview guide lays out the whole map. For now, Space is the right tool when you have one page in mind and zero patience for setup.

## Step one: decide what the page is

Ten minutes is plenty, but only if you know what you're asking for before you ask. Spend the first two deciding. A few honest options:

| What you want | What to ask for |
| --- | --- |
| A landing page | Your name, a one-line bio, links to your work and socials |
| A link hub | A clean stack of buttons pointing wherever you send people |
| A small tool | A calculator, converter, or countdown that does one job |

Pick one. The fastest way to waste your ten minutes is to ask for "a website" and then negotiate scope with Zo line by line. Bring a sentence you could say out loud to a person.

## Step two: ask Zo

Open a chat and describe the page. Be specific about content, loose about design unless you have a strong opinion.

```text
Make my zo.space home page a personal landing page. Headline with my name [Your Name], a one-line bio that says [your bio], and three links: [GitHub], [your writing], [email]. Keep it dark, clean, not a template.
```

Zo writes the code and puts it live. You did not open an editor. The home page lives at the root of your handle, so this lands at `yourhandle.zo.space` directly. If you'd rather keep the root for something else, ask for it at a path instead, like `/links` or `/about`, and it lives at `yourhandle.zo.space/links`.

## Step three: look at it, then push back

Open the URL. Read it like a stranger would. The first draft is a draft, and the fast loop is the reason Space is worth using at all. Don't accept "fine." If the spacing is cramped, say so. If the bio reads like a LinkedIn summary, tell Zo to make it sound like you. Concrete feedback gets concrete fixes:

- "The headline is too small, make it the loudest thing on the page."
- "Swap the link buttons for plain underlined text, the buttons feel heavy."
- "Add a Lucide github icon next to the GitHub link."

Two or three rounds of this and you have something you'd actually put your name on.

## The gotcha nobody warns you about

Here is where the afternoon disappears. You finish the page, send the link to a friend, and they get a sign-in screen instead of your work. You assume it's broken. It isn't.

New Space pages are private by default. Private means only you, signed in to your Zo, can see them. Your friend hits the door and gets asked to log in to an account they don't have. This is the single most common beginner confusion with Space, and it is one sentence to fix.

Tell Zo to make the page public:

```text
Make my zo.space home page public.
```

Now anyone with the link sees it, no account needed. Worth knowing how the defaults shake out, because they aren't uniform:

| Thing | Default visibility |
| --- | --- |
| Pages | Private, until you make them public |
| APIs | Always public |
| Assets (images, files) | Always public |

So a page stays yours until you flip it, but an API route you create is reachable by anyone the moment it exists, and any image you upload is fetchable by URL. If you build an API that returns something sensitive, that's on you to gate inside the code, because there's no private toggle on the route itself. The public and private pages guide goes deeper on what that means and when to keep a page locked.

## What ten minutes buys you

Two minutes deciding, three minutes describing, three or four minutes pushing back on the draft, one minute making it public. You end with a real page at a real URL that you can hand to anyone. No `git push`, no Vercel dashboard, no DNS.

When the one page grows into something you keep editing every week, that's the signal it wants to be a full project instead, and the guide on graduating a Space into a Site covers that jump without losing your work.

If this got your first page live, the rest of Zo Computer 101 runs the same way: short, specific, tested against the actual product. It lives at jeffkazzee.zo.space/writing.
