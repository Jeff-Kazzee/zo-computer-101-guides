---
title: "When to graduate from a Space route to a real Site"
id: space-to-site
category: hosting
kind: explainer
date: 2026-06-18
updated: 2026-06-18
excerpt: Space is great until your one little page becomes four pages, a database, and a build step. Here's the exact line where you should stop adding Space routes and move to a Site.
tags: [zo, space, sites, hosting, explainer, beginner]
related: [first-space-page, first-zo-site, zo-hosting-explained]
difficulty: beginner
reading_time: 6
---

You built one page on your zo.space and it worked, so you built another, and now you have five routes that all kind of belong to the same thing and you are starting to feel the friction. That friction is real, and it has a name. You have outgrown Space. The good news is that the move to a Site is a button, and the hard part is just knowing when to press it.

Space is for one small thing at `yourhandle.zo.space`. A landing page. An API at `/api/data`. A tip calculator widget. No folder, no framework, no deploy step. You ask Zo for it and it is live. That is the entire pitch, and for a single focused creation it is the right call almost every time.

> The signal isn't that Space stopped working. It's that you keep wishing it did one more thing it was never built to do.

## What Space genuinely can't do

Space and Sites are close cousins. Both run on Bun and Hono. The difference is ownership and scope. A Site is a real project that lives as a folder on your Zo, and that folder is the thing that changes everything.

Here is the honest split:

| You want                               | Space | Site |
| -------------------------------------- | ----- | ---- |
| One page, API, or widget, zero setup   | yes   | overkill |
| Source files you can open and edit     | no    | yes  |
| A real database (SQLite, by default)   | no    | yes  |
| Your own dependencies and build config | no    | yes  |
| A custom domain on the URL             | no    | yes  |

Space pages are private by default and you can flip them public. APIs are always public. Assets are always public. None of that changes the ceiling. The ceiling is that Space has a fixed set of dependencies and no project folder, so the second you need a package that isn't there or a database that isn't a workaround, you are pushing against a wall that was put there on purpose.

## The five signals to graduate

You do not need all five. Any one of these is enough to stop adding Space routes.

1. **You're writing your fourth or fifth related route.** A login page, a dashboard, a settings page, an export endpoint, and a webhook handler are not five small things. They are one project wearing a trench coat. When the routes start referencing each other and sharing shape, they want to live in one folder.
2. **You want a database.** Sites use SQLite by default, sitting next to your other files. Space has no real database. You can fake state for a bit, but the first time you want to save form responses and read them back later, that's the signal.
3. **You need a dependency Space doesn't have.** Space ships a fixed dependency set you can't add to. A Site is your project, so you install what you want.
4. **You want a custom domain.** A published Site becomes a public service at `sitename-yourhandle.zocomputer.io`, and you can point a custom domain like `app.example.com` at it. Custom domains attach to public services on paid plans, and Space doesn't get you there.
5. **You want to own the source.** On Space the routes are managed for you. In a Site, the files are yours to read, edit, version, and reason about. If you find yourself wanting to see the whole thing laid out as files, that's not a Space anymore.

## The decision rule

Strip it down to one line you can apply without thinking:

**If the thing is one small creation, use Space. The moment it becomes a project, move to a Site.**

A project is anything with multiple related routes, a database, its own dependencies, a custom domain, or source files you want to own. A creation is a page, an API, or a widget that stands by itself. Most people's instinct is to keep bolting routes onto Space because it is easy, and that instinct is how you end up with a sprawl of loosely related endpoints and no folder to hold them. Pay the small cost early. It is cheaper than untangling it later.

## How the move actually works

You don't rebuild from scratch. The Space tab has an Export button that copies selected Space routes into a new standalone Site. Same Bun, Hono, and Vite shape you already had, except now it is a folder you own. Open the **Sites** page, go to the **Space** tab, pick the routes you want to carry over, and export them into a Site.

After that, the new project behaves like any Site:

- It's private by default, visible only to you while signed in.
- When you hit **Publish**, it becomes a public service at `sitename-yourhandle.zocomputer.io`.
- You can add a database, add dependencies, and attach a custom domain.

Your old Space routes don't vanish because you exported. If you want a clean break, delete the routes you migrated so you're not maintaining two copies of the same logic. Decide that on purpose, because running the same page in two places is exactly the kind of quiet mess that costs you a confusing afternoon three weeks from now.

If you genuinely aren't sure which one fits, describe what you're building to Zo and ask. The push to over-engineer is real, and most things really are a single Space page. The skill is catching the moment they stop being one.

If this helped you see the line before you tripped over it, the rest of Zo Computer 101 is built the same way, including the guides on building your first Space page and your first real Site. They live at jeffkazzee.zo.space/writing.
