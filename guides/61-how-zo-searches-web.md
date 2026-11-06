---
title: "How Zo searches the web, and the four search tools it picks between"
id: how-zo-searches-web
category: browser
kind: explainer
date: 2026-06-18
updated: 2026-06-18
excerpt: When you ask Zo to 'look something up,' it's choosing between several web tools with different strengths. Here's how that choice works and how to steer it when the default isn't right.
tags: [zo, web-search, browser, research, beginner]
related: [read-vs-browse, zo-browser-explained, search-tools-card]
difficulty: beginner
reading_time: 6
---

When you tell Zo to "look something up," there is no single search box behind that request. Zo is choosing between a handful of web tools that work in very different ways, and the choice it makes is the difference between an answer in three seconds and a browser session that takes thirty. Once you understand the menu, you can steer it, and most of the time steering it well is the whole game.

The rule Zo follows is simple: pick the lightest tool that can do the job. A quick fact does not need a full browser any more than a grocery run needs a moving truck. The lighter the tool, the faster and cheaper the answer, so Zo reaches up the ladder only when the lighter rung can't reach.

> Search is for finding a page you don't have yet. Reading is for a page you already named. The browser is for a page that won't let you in without logging in.

## The four search tools

When Zo needs to discover something on the web, it picks between four search tools, each tuned for a different kind of result.

| Tool | What it's for | Reach for it when |
| --- | --- | --- |
| General web search | Broad lookups, news, current events | "What happened with [X] this week" |
| Deep research search | Targeted results with category filters | You want a specific kind of source |
| Maps search | Real-world locations | "Coffee near [the venue] open now" |
| X search | Social discourse, live sentiment | "What are people saying about [release]" |

The deep research tool is easy to miss because the filters are the part that matter. It can narrow to a category: a company homepage, a research paper, a PDF, a GitHub repo, a tweet, a personal site, a LinkedIn profile, a financial report, or a person by name. If you ask for "the GitHub repo for [project]," that filter is exactly what makes the result land on the repo instead of ten blog posts about the repo.

The general web search is the default starting point. It's fast, it's broad, and for news it leans on recency. When a question is just "what is the current state of [thing]," this is usually all Zo needs.

## Reading a page you already have

Search finds you a URL. Reading extracts from one you already named. These are different jobs, and conflating them is where people waste time.

If you hand Zo a public link and say "read this," it pulls the text straight off the page and works from that. No search, no browser, no waiting on a full render. This is the fast path, and it's the right one for an article, a docs page, a public blog post, or any page that serves its content without a login. Drop the URL in chat and ask the question you actually have about it.

The companion guide here is the read vs browse guide, which gets into when plain reading is enough and when a page is too dynamic for it. The short version: if the content is already in the page's HTML, reading is the fast path. If the content only appears after JavaScript runs or after you sign in, reading falls short and Zo needs the heavier tool.

## The browser, and why it's slow

The full browser is the truck. It loads a real page, runs the JavaScript, can click and scroll and fill forms, and can use sites you're already logged into. That power is also why it's slow. Every one of those steps is a real browser doing real work, so a browser task that takes Zo thirty seconds is doing thirty seconds of actual clicking, not stalling.

Reach for it in two situations:

1. **The page is behind a login.** Anything that needs your authenticated session, like a dashboard or a private feed, only works through the browser.
2. **The page is dynamic and reading came up empty.** Some sites render nothing until scripts run. If a plain read returns a blank or broken result, the browser is the fallback that actually sees the page.

For a static public article, the browser is overkill. Asking for it anyway just makes you wait.

## How to steer the choice

Zo guesses well, but it's guessing from your words. Name the source or the result type and you remove the guesswork:

- "Search recent news about [topic]" pushes it to the general web search with a recency lean.
- "Find the GitHub repo for [project]" triggers the category filter and lands on the repo.
- "Read this URL: [link]" skips search entirely and goes straight to extraction.
- "Find a [type of place] near [location] that's open now" routes to maps.
- "What are people on X saying about [event]" routes to social search.

The mental model worth keeping: search to discover, read to extract from a page you already have, browser only when the page won't open without a login. Match your phrasing to one of those three and Zo lands on the right tool the first time, instead of starting broad and working its way down while you wait.

If you want the one-page cheat sheet for which phrase triggers which tool, the search tools card lays it out side by side. The rest of Zo Computer 101 lives at jeffkazzee.zo.space/writing.
