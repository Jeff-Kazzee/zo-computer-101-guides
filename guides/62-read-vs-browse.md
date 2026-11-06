---
title: "Read a page or drive the browser? Why some requests are instant and some crawl"
id: read-vs-browse
category: browser
kind: explainer
date: 2026-06-18
updated: 2026-06-18
excerpt: Ask Zo to read a public article and it's instant. Ask it to pull a number from a dashboard you log into and it's slow. Same web, different tool, and knowing which is which explains the wait.
tags: [zo, browser, web-search, performance, beginner]
related: [zo-browser-explained, how-zo-searches-web, search-tools-card]
difficulty: beginner
reading_time: 6
---

Ask Zo to summarize a public blog post and the answer comes back before you've finished reading your own message. Ask it to grab this month's number from a dashboard you have to log into, and you sit there watching it work for a while. Same internet, same Zo, wildly different wait. The reason is that Zo has two completely different ways of getting at the web, and it picks between them based on one question you can learn to predict.

> If a logged-out stranger could see it at that URL, Zo reads it. If it needs your session or a click, Zo drives the browser. That single line explains almost every wait.

## Two tools wearing the same coat

When you say "look at this URL," it feels like one action. Under the hood it's a fork.

The lightweight path is text extraction. Zo fetches the page, pulls the readable content out of the HTML, and hands back the text. No screen, no rendering, no JavaScript running. It's closer to `curl` piped through a readability cleaner than to a browser. That's why it's quick. There's barely anything to do.

The heavy path is the actual browser. Zo loads the page the way Chrome would: it renders layout, runs the page's JavaScript, waits for dynamic content to settle, and uses your live signed-in session for sites where you're already logged in. A real machine spins up the full page and waiting for it to finish rendering. It's the difference between reading a printed-out copy of a document and opening the app the document lives in.

## Why one is fast and one isn't

The speed gap isn't arbitrary. Each step the browser does is a step the reader skips.

| | Read the page | Drive the browser |
|---|---|---|
| Runs the page's JavaScript | No | Yes |
| Needs your login session | No | Yes, that's the point |
| Can click, scroll, fill forms | No | Yes |
| Sees content that loads after the page does | Often no | Yes |
| Speed | Near-instant | Seconds, sometimes many |

A static article is mostly there in the raw HTML, so extraction grabs it whole and you're done. A dashboard behind a login is the opposite. The page shell loads empty, then JavaScript calls an API, then numbers fill in, and none of that is visible until a real browser has run all of it while signed in as you. A slow private pull isn't Zo stalling. It's a real browser rendering the page, running its scripts, and waiting for the numbers to land as you, which a static read never has to do.

## The rule, and how to predict it

Before you ask, run this test in your head: could someone who has never heard of you open that exact URL in a fresh incognito window and see the thing you want?

- **Yes** → it's publicly readable, and Zo will use the fast read.
- **No, it needs me logged in** → it's behind your session, and Zo has to use the browser.
- **It's public but the content appears after the page loads, or I need to click something** → still the browser, because extraction reads the first version of the page and stops.

Public news article, documentation, a GitHub README, a product page: read. Your email, your analytics, your bank, an internal tool, anything gated by a password: browser. A public page where the data only shows up after you click a tab or scroll to trigger a load: browser, because the lightweight read sees the page before that content exists.

## Steering it on purpose

You usually don't have to think about this. Zo makes the call. But when you want to nudge it, the phrasing does the steering.

1. **For public pages, name the read.** "Just read this URL and pull the three main points." You're telling Zo the content is sitting there in plain HTML, so don't bother spinning up a browser.
2. **For anything behind a login, name the browser.** "Open my [analytics dashboard] in the browser and read the visitor count for this month." This tells Zo to use your signed-in session instead of fetching a logged-out version that'll just show a sign-in wall.
3. **For interaction, describe the click.** "Open the page, click the 'Last 30 days' tab, then read the total." Extraction can't click. If the number only appears after an action, the browser is the only tool that reaches it.

The failure mode to recognize: you ask Zo to "read" a page that needs your login, and it comes back with the contents of a sign-in screen instead of your data. That's not a bug. The lightweight reader fetched the page as a stranger would, and to a stranger that page is a login form. The fix is one word: tell it to open the page in the browser so your session comes along.

There's one setup cost worth knowing. For the browser to use your session on a site, you have to have signed into that site through Zo's browser at least once, the same way you'd log into anything. After that the session sticks and Zo reuses it.

If you want how the browser holds those logged-in sessions, that’s the next guide. The rest of Zo Computer 101 lives at jeffkazzee.zo.space/writing.
