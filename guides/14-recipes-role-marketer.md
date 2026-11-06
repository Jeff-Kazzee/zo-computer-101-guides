---
title: "The marketer's automation pack: 11 things Zo does so you don't"
id: recipes-role-marketer
category: recipes
kind: recipe-pack
audience: role
order: 2
date: 2026-06-18
updated: 2026-06-18
excerpt: Content calendars, competitor watches, campaign reporting, and the busywork between. 11 marketing automations you can paste into Zo today, each with the plugins it needs and the failure to watch for.
tags: [automations, recipes, marketer, content, reporting, web-search, notion, email, scheduling, conditional-alerts]
related: [zo-automations-101, plugin-inside-automation, zo-plugins-integrations]
difficulty: beginner
reading_time: 9
---

Marketing at a small company means the calendar never stops asking for the next thing. A blog post is due, three competitors just changed their pricing page, a customer tagged you on social an hour ago, and the monthly recap is somehow due Friday again. None of that is hard. It's just constant, and it lands on one person who is also supposed to be doing the actual creative work. That constant layer of checking and drafting and chasing is what an automation handles well, because most of it is "watch this thing on a schedule and only draft or ping when there's something real."

Each recipe below follows one shape: what it does, what you need connected, the exact prompt to give Zo, the tweak that keeps it quiet, and the failure to watch for. Connect your plugins first (the integrations guide walks through that), then talk to Zo in plain English. The times and thresholds are starting points. Change them to fit your week.

> The fastest way to kill a marketing automation is to let it publish. Make every drafting recipe stop at the draft, every time, and keep the publish button in a human hand. A queue you review beats a feed you have to apologize for.

## 1. The content calendar that drafts the empty slots

**What it does:** Looks at your content plan and writes a first draft for anything due soon that's still blank.
**You need:** Notion connected (or just your files).
**The prompt:**
```
Every Sunday at 5:00pm Mountain, open my content plan in Notion. For any
slot scheduled in the next 7 days that has no draft yet, write a first
version and save it as a draft in that slot. Email me a list of what you
drafted with a one-line summary of each. Do not publish anything.
```
**Make it quieter:** Add "only email me if you drafted at least one piece. If everything's already covered, stay silent."
**Watch out for:** A first draft is a first draft. It writes from what's in the plan, so a slot that just says "newsletter" gets a generic newsletter. The more your calendar says, the less you rewrite.

## 2. Competitor and SERP watch

**What it does:** Checks the pages and search results you care about and tells you only what moved.
**You need:** Nothing connected; Zo reads public pages.
**The prompt:**
```
Every Monday at 9:00am Mountain, check [competitor pricing URL],
[competitor blog URL], and the Google results for "[your main keyword]".
Compare to what you saw last week. Email me only what changed: new pricing,
new posts, anyone new ranking on page one for my keyword. If nothing moved,
send one line saying so.
```
**Make it quieter:** Already change-gated. The "if nothing moved" line is what keeps it from becoming a Monday chore you ignore.
**Watch out for:** Some sites block automated reads, and search results shift for reasons that aren't real movement. Tell Zo to flag a page it couldn't load instead of pretending nothing changed there.

## 3. Brand-mention and social monitoring

**What it does:** Scans for new public mentions of your brand and surfaces the ones worth a reply.
**You need:** Nothing connected for public web mentions; Zo reads public pages and search.
**The prompt:**
```
Twice a day at 8:00am and 4:00pm Mountain on weekdays, search the public
web for new mentions of "[your brand name]" and "[your product name]" from
the last 12 hours. Email me only the ones that look like a customer
question, a complaint, or press. Skip our own posts and obvious spam.
```
**Make it quieter:** Add "if there's nothing in those three buckets, don't email." A monitor that pings you about your own blog post is noise.
**Watch out for:** Public search doesn't see inside private or logged-in platforms, so it catches a slice, not everything. For full coverage of a specific network you'd want that platform's own tooling. This is the cheap 80%.

## 4. The weekly campaign performance report

**What it does:** Pulls this week's campaign numbers and tells you which way each one moved.
**You need:** Your analytics export or data file (and whatever analytics integration you've connected, if any).
**The prompt:**
```
Every Friday at 3:00pm Mountain, read my campaign data from [file or
connected source]. Summarize this week's clicks, signups, and spend per
campaign, and compare each number to last week. Email me a short report
with the direction each number moved and the one campaign that changed
most. If a metric isn't in the data, say so instead of guessing.
```
**Make it quieter:** You want this every week, so keep it scheduled, not conditional.
**Watch out for:** Define your week (Mon to Sun, say) in the prompt so the comparison is honest. And don't trust a number Zo can't trace back to your file. The "say so instead of guessing" line matters because a made-up conversion rate is worse than a blank.

## 5. Newsletter prep from the week's activity

**What it does:** Assembles the raw material for your next send so you start from a draft, not a blank page.
**You need:** Notion or your files, plus Gmail if you pull from email threads.
**The prompt:**
```
Every Thursday at 10:00am Mountain, gather what we published this week from
my content plan and any links I saved in [Notion page or file]. Draft a
newsletter: a short intro, three to five items with a sentence each, and one
clear call to action. Save it as a draft and email me the draft to review.
```
**Make it quieter:** Add "only run if we published or saved at least one thing this week. A newsletter with nothing in it isn't worth sending."
**Watch out for:** It writes the call to action from what it can infer, which is usually generic. Rewrite that line yourself every time. The CTA is the part that does the work.

## 6. One post into many

**What it does:** Takes a piece you already published and drafts the social and email versions.
**You need:** Notion or your files where the source post lives.
**The prompt:**
```
When I add a post to the "repurpose" list in [Notion or file], draft three
things from it: a short post for X, a longer one for LinkedIn, and a
two-line email teaser. Keep my voice, don't add claims that aren't in the
original, and save all three as drafts. Email me when they're ready.
```
**Make it quieter:** Trigger it off the list instead of a clock, so it only runs when you actually drop a post in. No empty runs.
**Watch out for:** Repurposing drifts. A model paraphrasing your post can quietly invent a stat or soften your point. Read each draft against the original before it goes out, especially the numbers.

## 7. The brand-mention instant alert

**What it does:** A faster ping for the mentions you genuinely can't sit on, like press or an angry customer.
**You need:** Nothing connected for public mentions; Gmail if you also want to catch press emails.
**The prompt:**
```
Every hour between 8am and 6pm Mountain on weekdays, check the public web
for new mentions of "[your brand name]" that read as press, a journalist
request, or a public complaint. Text me only if one shows up, with the
source and a one-line summary.
```
**Make it quieter:** This is already the quiet version. It stays silent unless something in those three categories lands.
**Watch out for:** Every run spends credits. Hourly across a workday is reasonable for something this narrow. Don't widen it to "any mention every 15 minutes" or you'll pay to be told about your own retweets.

## 8. Scheduled blog draft with a human gate

**What it does:** Turns a topic from your idea list into a full first draft, then stops.
**You need:** Notion or your files for the idea list.
**The prompt:**
```
Every Tuesday at 9:00am Mountain, take the top unwritten topic from my blog
idea list in [Notion or file]. Write a full first draft with a working
title, an intro, sections, and a close. Save it as a draft and email it to
me. Do not publish, and do not post it anywhere.
```
**Make it quieter:** Add "skip the run and stay silent if the idea list is empty." No topic, no draft, no email.
**Watch out for:** A weekly draft generator with no human reading it is how a site fills up with mediocre AI posts that nobody asked for. The gate is the point. If you're not going to edit the draft, don't run the recipe.

## 9. Link-rot checker on your owned pages

**What it does:** Crawls your key pages for dead links and broken redirects before a reader finds them.
**You need:** Nothing connected; Zo reads public pages.
**The prompt:**
```
Every Monday at 7:00am Mountain, check the links on [your homepage URL],
[your pricing URL], and [your top blog post URL]. Email me only the links
that return an error or a redirect to somewhere unexpected, with the page
they're on. If everything resolves, send one line saying so.
```
**Make it quieter:** Already error-gated. Add the URLs that actually matter for revenue first; you don't need every page on day one.
**Watch out for:** A link can 200 and still be wrong, like a product page that quietly went out of stock. This catches dead links, not stale content. For "is this still accurate," you still have to look.

## 10. Weekly content-idea generator from research

**What it does:** Reads what's happening in your space and hands you a short list of angles worth writing.
**You need:** Nothing connected; Zo reads public pages and search.
**The prompt:**
```
Every Wednesday at 8:00am Mountain, look at what's being published and
discussed this week around [your topic or industry]. Email me five content
ideas, each with a one-line angle and why it's timely. Skip anything we've
already covered in my content plan.
```
**Make it quieter:** Five is plenty. If you ask for twenty you'll skim and use none. Keep the number small enough that you'll actually read them.
**Watch out for:** Ideas pulled from "what's trending" skew toward what everyone else is also writing. Treat the list as raw input, not a plan. Your best angle is usually the one only you can write.

## 11. End-of-month marketing recap

**What it does:** One report on the month's numbers and output, written the way you'd brief your boss or yourself.
**You need:** Your analytics file or connected source, plus Notion or files for what you shipped.
**The prompt:**
```
On the first weekday of each month at 9:00am Mountain, build a recap of last
month. Pull traffic, signups, and spend from [file or connected source],
compare to the month before, and list what we published from my content
plan. Email me a one-page summary: the numbers and their direction, the
three things that worked, and one thing to try next month. Flag any metric
that isn't in the data.
```
**Make it quieter:** Keep this one scheduled. A monthly recap is the kind of thing you skip forever if it isn't automatic.
**Watch out for:** "What worked" is Zo reading correlation off your data, not proof of cause. Use it to decide what to look at closer, not as the final word on why a number moved.

## Before you paste all eleven

Two rules keep this from turning into a feed you mute and a mess you have to clean up.

First, build them one at a time. Get the content calendar drafting the way you want, tune the email it sends you, then add the competitor watch. Eleven automations stood up in one afternoon and never adjusted is eleven things you'll be ignoring by next Friday. The ones that earn trust are the ones you shaped over a couple of weeks.

Second, anything that can draft in your voice or reach a connected account should run under a scoped persona that can read and draft but cannot send, post, or charge on its own. That single boundary is what makes the whole pack safe to leave running, because a drafting recipe that physically cannot publish can't embarrass you while you sleep. The plugin-in-automation guide shows exactly how to box one in.

Start with the content calendar and the brand-mention alert. The first one means you never open Monday to an empty week. The second means you hear about the angry customer before they get louder. Feel those two work for a week and the other nine stop sounding like extra setup and start sounding obvious.

If you're starting cold, read the automations explainer first, because the recipes that use Gmail, Stripe, or Notion need those connected first (the public-web ones don't). Then pick one. This is the kind of guide I write every week. They live at jeffkazzee.zo.space/writing.
