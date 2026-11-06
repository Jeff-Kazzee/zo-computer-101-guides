---
title: "The four web search tools, ranked by when to use each"
id: search-tools-card
category: reference
kind: reference
date: 2026-06-18
updated: 2026-06-18
excerpt: Zo doesn't have one way to hit the web, it has several, and it picks between them. Here's the card: what each search-and-read tool is best at, so you can point Zo at the right one.
tags: [zo, web-search, browser, research, reference]
related: [how-zo-searches-web, read-vs-browse, zo-browser-explained]
difficulty: beginner
reading_time: 4
---

Zo has more than one way to reach the internet, and when you say "look this up," it picks one. Most of the time the pick is right and you never think about it. But when an answer comes back thin, stale, or blocked, knowing the menu lets you say "use the deeper research search" or "just read the page" instead of shrugging. This is that menu.

The thing to hold in your head is a hierarchy by cost and weight. Reading a known page and running a plain web search are cheap and fast. The full browser is the heavy machinery you only roll out when a page hides behind a login or needs a click to load. Zo defaults to the lightest tool that can do the job, and you should too.

> Reach for the browser last. Most of the web is readable without it, and the lightweight tools are faster, cheaper, and harder to get blocked.

## The card

| Tool | Best for | Don't use it when |
| --- | --- | --- |
| General web search | Broad discovery, "what's out there," current events and breaking news | You already have the exact URL, or you need depth on one niche topic |
| Deeper research search | Higher-quality results with category filters (company, research paper, GitHub, LinkedIn profile, PDF) | You just need a quick answer or today's headlines |
| Read a specific webpage | Pulling the text off one public page you already know | The page needs a login or builds its content with JavaScript after load |
| The full browser | Logged-in sites, dynamic pages, anything that needs clicks, scrolls, or a screenshot | The page is public and static, because this is the slowest option |

Two more live alongside these and matter when the question fits them exactly: maps search for real places (restaurants, stores, anything with an address and hours), and X/Twitter search for social discourse, the live sentiment and breaking chatter you won't find cleanly anywhere else. Reach for those by name when that's what you actually want.

## How to read the ranking

The four core tools split into two jobs. Searching, which is finding pages you don't have yet. Reading, which is getting the content out of a page you do have. Plain web search and deeper research search are both search. Reading a page and the browser are both read. Knowing which job you're in tells you which half of the table to look at.

### When to search vs. when to read

If you have the link, don't search. Tell Zo to read the page. Searching for a URL you already hold wastes a step and sometimes lands you on a worse copy of the thing you were pointing at.

If you don't have the link, search first, then let Zo read the good result. For most questions, plain web search is the right opening move. It's built for breadth: surveying what exists, catching current events, getting oriented fast. For news specifically, it can lean on recency so you're not reading a year-old take dressed up as today's.

### When the plain search isn't enough

Switch to the deeper research search when breadth fails you and you need the right results instead of merely many. It carries category filters that change everything for certain hunts:

1. **Company** for a real homepage instead of ten aggregator listings.
2. **Research paper** or **PDF** when you want the source document, not someone's summary of it.
3. **GitHub** for the actual repo.
4. **LinkedIn profile** or **people** for a specific human, especially with a name plus a disambiguating detail like their role or employer.

A good pattern, and the one Zo tends to run on harder questions: start with a plain web search to map the terrain, then follow up with the deeper search to drill into the one vein worth mining.

## The browser is the fallback, not the default

The full browser is the most capable tool here and the one to reach for last. It can log into sites where you already have a session, click through dynamic pages, fill forms, and take screenshots. That power costs speed, and it can trip anti-bot blocks that the lighter tools sail past.

So the rule is simple. If reading the page returns clean text, you're done, no browser needed. Use the browser when the content lives behind a login, when the page renders its real content with JavaScript only after you interact with it, or when you genuinely need to watch the page render, screenshots and all. Asking Zo to drive the browser for a plain public article is like renting a forklift to carry a grocery bag.

## The one move that fixes most bad lookups

When an answer comes back wrong-feeling, name the tool. "That looks stale, search the news from this week." "You have the URL, just read it." "That's a niche paper, use the research search with the PDF filter." "It's behind a login, use the browser, I'm signed in." All you're doing is handing Zo the one piece of context it couldn't infer: which of these tools you'd have reached for.

If you want the why behind the picks, the [how Zo searches the web](#) explainer covers the decision Zo makes on its own, and the [read vs. browse](#) guide goes deeper on that last column of the table, the line between pulling text off a page and actually driving a browser through it. They live with the rest of Zo Computer 101 at jeffkazzee.zo.space/writing.
