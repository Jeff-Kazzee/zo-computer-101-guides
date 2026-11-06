---
title: "Google Analytics tells Google everything. Here's a 40-line tracker that only tells you."
id: website-analytics-with-automation
category: automations
kind: how-to
order: 6
date: 2026-06-21
updated: 2026-06-21
excerpt: Host your own pageview and click tracking with one append-only endpoint and a weekly automation, then layer GA4 or an ad stack on top when you want Google reporting or revenue. Two paths, no cookie banner required for the one you own.
tags: [zo, automations, hosting, sites, space, reporting, scheduling, conditional-alerts, beginner]
related: [zo-automations-101, conditional-automations, first-zo-site, first-space-page]
difficulty: intermediate
reading_time: 9
---
You want to know which pages people read and which buttons they click. The default answer is Google Analytics because people want numbers, and sometimes because they want ads or the Google reporting that goes with them. That's fine. The smaller answer is the one I use here: keep a tiny tracker on your own server, then layer GA4 or an ad stack on top if your money model needs it. One endpoint that writes a line to a file when something happens, and one automation that reads the file on a schedule and tells you what changed.

> Analytics you host is the only analytics where the product isn't your visitors.

This is the exact pattern running on my own sites. A guide gets opened, a line gets appended. A weekly automation reads the file and sends me the counts. It is maybe forty lines of code and it answers the only question most sites actually have: is anyone reading this, and what are they clicking.

## What you're building

Three pieces, and each one is small on purpose.

1. **A tracking endpoint.** An API route that takes an event (a page slug, a click name) and appends one line to a file. It does no math, holds nothing in memory, and never blocks the visitor.
2. **A beacon on the page.** Two or three lines of frontend code that fire the event when a page loads or a button gets clicked.
3. **A digest automation.** A scheduled prompt that reads the file, counts the events, and sends you a summary with a conditional clause so it only pings when there's something worth seeing.

The storage is a JSONL file. One JSON object per line, append-only. It is the right shape here because appending a line is atomic enough for this, it never needs a migration, and Zo can read it at the end of the week without you standing up a database. If you outgrow it, the SQLite guide is the next step, but most sites never do.

## Step 1: the tracking endpoint

This works on both a Zo Site (a route in your `server.ts`) and a Zo Space (an API route). Here it is for a Zo Site using Hono and Bun. It appends one event per request and returns immediately.

```ts
import { appendFile, mkdir } from "node:fs/promises";

const EVENTS_PATH = "/home/workspace/Projects/your-site/data/events.jsonl";

app.post("/api/track", async (c) => {
  let body: { type?: string; id?: string } = {};
  try {
    body = await c.req.json();
  } catch {
    return c.json({ ok: false }, 400);
  }

  const type = String(body.type || "").slice(0, 32);
  const id = String(body.id || "").slice(0, 120);
  if (!type || !id) return c.json({ ok: false }, 400);

  const event = {
    t: new Date().toISOString(),
    type,            // "view" or "click"
    id,              // page slug or button name
    ref: c.req.header("referer")?.slice(0, 200) || null,
  };

  try {
    await mkdir("/home/workspace/Projects/your-site/data", { recursive: true });
    await appendFile(EVENTS_PATH, JSON.stringify(event) + "\n");
  } catch (err) {
    console.error("track failed", err);
    return c.json({ ok: false }, 500);
  }

  return c.json({ ok: true });
});
```

Three things make this safe to leave running. It caps the field lengths, so a bad actor can't write a megabyte per request into your file. It swallows its own errors, so a failed write returns a 500 to nobody important and never crashes the page. And it stores no IP, no cookie, no fingerprint, which means there's nothing to put in a privacy policy and nothing to leak. You're counting events, not people.

On a Zo Space the only change is the file shape: a Space API route exports a default `(c) => Response` handler instead of registering on an `app`, and you'd write to an absolute workspace path the same way. The logic is identical.

## Step 2: fire the event from the page

A pageview goes in a `useEffect` so it runs once when the page mounts. A click goes in the handler you already have.

```ts
// Pageview, on mount
useEffect(() => {
  fetch("/api/track", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ type: "view", id: "homepage" }),
  }).catch(() => {});
}, []);

// Click, on a button or link you care about
function trackClick(name: string) {
  fetch("/api/track", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ type: "click", id: name }),
  }).catch(() => {});
}
```

The `.catch(() => {})` is load-bearing. It means a tracking failure is invisible to the visitor. The fetch fires, you don't await it, and if it dies the page doesn't notice. Analytics should never be in the critical path of someone reading your work.

Be deliberate about what you name. `type: "click", id: "signup-cta"` and `id: "pricing-link"` will tell you something in a week. Tracking every link on the page will give you a file full of noise you have to dig through. Pick the five clicks that would actually change a decision and track those. This is the single biggest mistake people make with analytics: they collect everything and learn nothing, because the signal drowns. Track for the decision you'll make, not for the completeness of the record.

One caveat on counts. A raw view line per mount counts double in React's dev strict mode and counts bots and reloads in production. This is a directional counter, not an audited billing system. If you need deduped uniques, you'd hash the day plus a coarse signal server-side, but for "which page is pulling" the raw count is honest enough and you should resist gold-plating it.

## Step 3: the automation that reads it

Here's where Zo does the part a static script can't. You don't write a parser and a cron job and a mailer. You point an automation at the file and tell it what you want to know. Go to the [Automations](/?t=automations) tab, create one, and give it this prompt.

**What it does:** reads a week of tracked events and sends you a ranked digest, only if there was traffic.

**You need:** the tracking endpoint above live and collecting, and a delivery channel connected (email, SMS, Telegram, Discord, or Slack).

**The prompt:**

```
Read the file at /home/workspace/Projects/your-site/data/events.jsonl.
Each line is a JSON event with t (ISO timestamp), type ("view" or
"click"), and id (page slug or button name).

Look at only the events from the last 7 days.

Send me a digest ONLY IF there were at least 10 events in that window.
If there were fewer than 10, stay silent and do nothing.

The digest should have:
- total views and total clicks for the week
- the top 5 most-viewed page ids, with counts
- the top 5 most-clicked button ids, with counts
- how each of those compares to the previous 7 days (up, down, flat)

Keep it short. Plain text, no preamble. Lead with the headline number.
```

**Make it quieter:** the `ONLY IF there were at least 10 events` clause is the whole game. A new site with three visitors a week should not generate a weekly email that trains you to ignore it. Raise the threshold as your traffic grows. The conditional-automations guide goes deep on why an alert you ignore is worse than no alert.

**Watch out for:** the file path has to be exact and absolute. A relative path resolves against wherever the automation runs, not your project, and you'll get a confusing "file not found" with the automation reporting success because it has nothing to read. Paste the path you actually used in step 1, character for character.

Set the schedule to weekly, pick your day, and you're done. Every run is saved as a real conversation, so if a digest looks wrong you open the run and see exactly what Zo read and counted. The debug-a-run guide covers reading those.

## If you want ads and a Google stack too

The self-hosted tracker does not fight ads. It just keeps your own measurement separate from the money layer.

If you want Google reporting, drop GA4 into the site head and keep the local tracker anyway. If you want ad revenue, add AdSense or sponsor slots and track the conversion events that matter to you. The two systems can sit side by side without one owning the other.

For a Zo Site, put this in `index.html`. For a Zo Space, put the same snippet in the page's custom head HTML.

```html
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){window.dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXX', { anonymize_ip: true });
</script>
```

Then fire the events you actually care about. Not every click. The ones that tell you whether the site is earning.

```ts
gtag("event", "signup_click", {
  location: "hero",
  label: "try_zo",
});

gtag("event", "affiliate_click", {
  location: "footer",
  label: "writing_link",
});
```

If you sell ads, sponsor slots, or affiliate placements, GA4 gives you the reporting layer that ad networks expect. Your own endpoint gives you the part they never will. Both matter.

## Why this beats the script-tag version

A hosted analytics tag gives you a prettier dashboard. This gives you four things it can't.

The data is yours, in a file you can `cat`, grep, back up, or feed to any other automation. There's no cookie banner because you're not setting a cookie. There's no third party, so nothing about your visitors leaves your server. And the summarizer is an agent, not a fixed report, which means when you want a different cut ("which pages did people read before they clicked signup") you change the prompt, not the schema.

The tradeoff is real and worth saying plainly. You don't get real-time charts, session replay, or funnels out of the box. If you're running paid acquisition and optimizing a checkout, you want the heavy tool. If you have a site, a blog, or a portfolio and you want to know what's landing without surveilling anyone, this is the whole job in forty lines.

## Make it a daily activity log too

The same endpoint, pointed at a different file, becomes a personal logger. Append a line every time an automation runs, every time a deploy finishes, every time you ship. Then a second digest automation reads that file and gives you a weekly record of what actually happened, built from events instead of memory. The pattern is the same every time: something appends a line, an automation reads the lines on a schedule and tells you the story. Once you see it, you start putting a `/api/track` on everything.

Start with the [automations basics](/?t=automations) if you haven't built one, wire the endpoint into your first site, and let the first weekly digest land. The rest of Zo Computer 101 is written to the same standard, specific and tested with no filler, and it lives at jeffkazzee.zo.space/writing.
