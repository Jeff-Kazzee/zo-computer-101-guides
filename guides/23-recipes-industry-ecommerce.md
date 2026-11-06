---
title: "10 automations for an e-commerce store that isn't on Shopify's payroll"
id: recipes-industry-ecommerce
category: recipes
kind: recipe-pack
audience: industry
order: 5
date: 2026-06-18
updated: 2026-06-18
excerpt: Order summaries, low-stock alerts, abandoned-cart follow-up drafts, and the review chase. 10 e-commerce automations you can run in Zo, each with the plugins it needs and the failure mode.
tags: [automations, recipes, ecommerce, stripe, reporting, email, scheduling, conditional-alerts]
related: [zo-automations-101, plugin-inside-automation, zo-plugins-integrations]
difficulty: beginner
reading_time: 9
---

A small store runs on a hundred tiny checks a day. Did anything sell overnight. Is the bestseller about to go out of stock again. Did that customer who emailed at 11pm get an answer. Did Stripe flag a dispute while you were packing boxes. None of it is hard. All of it is constant, and it lives in your head until you forget one and a customer notices before you do. That forgetting is the expensive part. The checking is what an automation is built for, because most of it is "look at one thing on a schedule and only interrupt me when something's actually off."

Each recipe below is the same block: what it does, what you connect, the exact prompt to hand Zo, the tweak that keeps it quiet, and the way it breaks. Connect your plugins first (the integrations guide walks through it), then talk to Zo in plain English. Change every time, threshold, and name to match your store. These are starting points.

> A store owner who gets a "12 orders, $843, nothing weird" text every morning checks Stripe less and sleeps more. A store owner who gets pinged on every single sale mutes the whole thing by Thursday. Build the one that earns the interruption.

## 1. The overnight orders text

**What it does:** One message with last night's order count and revenue, before you touch the laptop.
**You need:** Stripe connected.
**The prompt:**
```
Every morning at 7:30am Mountain, check Stripe for payments received since
8pm yesterday. Text me the order count, the total revenue, and the average
order value. If a single order was over $200, name it. Keep it to three lines.
```
**Make it quieter:** Add "if zero orders came in overnight, just send 'quiet night' and nothing else."
**Watch out for:** Stripe test mode and live mode are separate ledgers. If your numbers look impossibly clean or impossibly empty, you're reading the wrong one. Tell Zo "live mode" in the prompt.

## 2. Low-stock alert from your inventory sheet

**What it does:** Warns you before a product hits zero, while there's still time to reorder.
**You need:** Google Sheets connected (or a stock file in your workspace).
**The prompt:**
```
Every weekday at 8:00am Mountain, read my inventory sheet at [sheet name].
Email me any SKU where the quantity column is at or below its reorder
threshold, with the product name, current count, and threshold. If everything
is above threshold, send one line saying stock is fine.
```
**Make it quieter:** It's already gated to items under threshold. Add "skip the email entirely on days when nothing is low."
**Watch out for:** Zo reads the numbers in the sheet, not the boxes in your storage. If the sheet is two days stale because you sold a case off the shelf and didn't log it, the alert is two days wrong. The automation is only as honest as your sheet.

## 3. Abandoned-cart follow-up, drafted not sent

**What it does:** Turns yesterday's almost-sales into ready-to-edit recovery emails you approve before anything goes out.
**You need:** Stripe connected, plus wherever your abandoned-cart or checkout-started data lives (a sheet or export).
**The prompt:**
```
Every weekday at 10:00am Mountain, look at [abandoned cart source] for
checkouts started yesterday that never completed payment in Stripe. For each
one with an email, draft a short, friendly follow-up that names the product
they left and offers help, no fake discount unless I add one. Email the drafts
to me. Do not send anything to customers.
```
**Make it quieter:** Add "only email me if there's at least one cart to follow up on."
**Watch out for:** This drafts. It never sends. Keep that gate, because a follow-up fired at the wrong person at the wrong time reads as spam, and an apology costs more than the recovered sale. Read every draft before it ships.

## 4. New-review watcher

**What it does:** Tells you when a fresh review lands so you can reply fast, especially the angry ones.
**You need:** Nothing connected; Zo reads public pages.
**The prompt:**
```
Every weekday at 9:00am and 4:00pm Mountain, check [your product review page
URL] and [your Google or marketplace review URL]. Compare to last check and
email me only new reviews since then, with the rating and the text. Flag
anything 3 stars or below at the top.
```
**Make it quieter:** Already change-gated. Tighten it to "only email me if a new review appeared, and put anything 2 stars or below in the subject line."
**Watch out for:** Some review platforms block automated reads or hide reviews behind a login. If a source keeps coming back empty, tell Zo to note "couldn't read [source]" instead of quietly skipping it, or you'll think the silence means no reviews.

## 5. This week versus last week

**What it does:** Your real sales numbers, side by side with the prior week, every Friday.
**You need:** Stripe connected.
**The prompt:**
```
Every Friday at 4:00pm Mountain, pull this week's Stripe payments, refunds,
and net revenue, Monday through Friday. Compare to the same days last week.
Email me a short summary with the direction each number moved and the percent
change. If a number dropped more than 20 percent, say why if you can tell.
```
**Make it quieter:** You want this one every week. Keep it scheduled, not conditional.
**Watch out for:** Define your week in the prompt so the comparison is apples to apples. A "down 30 percent" that's really comparing a four-day week against a five-day week will scare you for no reason. And Zo can guess at a "why," it can't confirm one, so treat that line as a hypothesis.

## 6. Refund and dispute alert

**What it does:** A near-real-time heads up when money goes the wrong direction, so a dispute doesn't expire unnoticed.
**You need:** Stripe connected.
**The prompt:**
```
Every two hours between 8am and 8pm Mountain on weekdays, check Stripe for
new refunds and new disputes since the last check. Text me only if one
appeared, with the amount, the customer, and the reason if Stripe gives one.
```
**Make it quieter:** This is already the quiet kind. It says nothing unless a refund or dispute actually hits.
**Watch out for:** Disputes have a hard response deadline, often around 7 to 21 days depending on the card network, and missing it means you lose by default. This alert tells you fast. It does not respond for you. When one fires, go handle it in Stripe that day.

## 7. Restock reminder for your top sellers

**What it does:** Watches your best products specifically, because those are the ones that hurt to run out of.
**You need:** Google Sheets connected (your inventory sheet) and Stripe connected.
**The prompt:**
```
Every Monday at 8:30am Mountain, find my top 5 selling products from Stripe
over the last 30 days. Cross-check those against my inventory sheet. Email me
any of those top sellers with fewer than [14] days of stock left based on the
last 30 days of sales velocity. If all top sellers are well stocked, say so.
```
**Make it quieter:** Already focused on five products and gated by days-of-cover. Leave it weekly.
**Watch out for:** "Days of stock left" assumes next month sells like last month. A holiday spike or a viral post breaks that math. Treat the number as a floor, not a forecast, and reorder earlier if you know a surge is coming.

## 8. Shipping-delay watcher

**What it does:** Surfaces orders that paid but haven't shipped, before the customer emails asking where their thing is.
**You need:** Stripe connected, plus wherever you track fulfillment (a sheet or your shipping export).
**The prompt:**
```
Every weekday at 11:00am Mountain, find orders in Stripe that were paid more
than [2] business days ago. Cross-check my fulfillment sheet for a tracking
number or a shipped status. Email me any paid order that still has no tracking,
with the order date, customer, and how many days it's been waiting.
```
**Make it quieter:** Add "only email me if there's at least one unshipped order past the window."
**Watch out for:** This depends on your fulfillment sheet being current. If you ship from the warehouse and log it that night, the morning run will flag orders you already mailed. Either log shipments as you go, or run this later in the day after the sheet's updated.

## 9. Customer-question triage from email

**What it does:** Sorts the morning's customer email so you answer the "where's my order" before the newsletter pitch.
**You need:** Gmail connected.
**The prompt:**
```
Every weekday at 9:00am Mountain, read my Gmail from the last 16 hours. Pull
out real customer messages, questions, complaints, order issues, and group
them: needs a reply today, can wait, and just FYI. Skip newsletters, vendor
spam, and automated receipts. Email me the grouped list with sender and the
one-line gist of each.
```
**Make it quieter:** Add "only send if there's at least one message in the needs-a-reply-today group."
**Watch out for:** Zo sorts by what the email looks like, and the line between "complaint" and "can wait" is judgment. Expect a few miscategorized messages the first week. Tell it which words mean urgent for your store, like "broken," "wrong item," or "chargeback," and it gets sharper.

## 10. End-of-month store recap

**What it does:** One clean summary of the month so you're not reconstructing it from memory at tax time or before a slow afternoon of planning.
**You need:** Stripe connected (and your inventory or expenses sheet if you keep one).
**The prompt:**
```
On the last day of each month at 5:00pm Mountain, pull the full month from
Stripe: total revenue, order count, average order value, refunds, and net.
Compare to the prior month. If I have an inventory sheet connected, note which
products sold the most units. Email me a one-page recap with the numbers and
two or three plain-English observations.
```
**Make it quieter:** Monthly is already rare. Keep it on a schedule so you never skip a month.
**Watch out for:** Months have different lengths, and a 28-day February against a 31-day January is not a fair fight on raw totals. Ask for the per-day average alongside the total so the comparison means something. And anything Zo can't pull cleanly, it should flag, not invent.

## Before you paste all ten

Two rules keep this from becoming a folder of muted notifications. First, build them one at a time. Turn on the overnight orders text, live with it for a few days, fix the wording, then add the next. Ten automations switched on in one afternoon and never tuned is ten things you'll be ignoring by next week. Second, the recipes that touch money or customers, the refund alert, the cart follow-up, anything that could email a buyer, are worth running under a scoped persona that can read and draft but cannot send, post, or charge on its own. A drafted apology you approve is fine. An auto-fired discount to the wrong list is a bad afternoon. The plugin-in-automation guide shows exactly how to box one in.

Start with the overnight orders text and the refund alert. The first one makes you check Stripe less. The second one catches the thing that actually costs you money if it slips. Feel those two work for a week, and the other eight stop looking optional.

If you're starting cold, read the automations explainer first, because the recipes that use Gmail, Stripe, or Notion need those connected first (the public-web ones don't). Then pick one. Not ten. This is the kind of guide I write every week. They live at jeffkazzee.zo.space/writing.
