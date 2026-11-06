---
title: "Connect Zo to GitHub and push your first repo"
id: github-first-push
category: building
kind: how-to
date: 2026-06-18
updated: 2026-06-18
excerpt: Zo ships with the GitHub CLI already installed. The only thing between you and pushing a repo is a one-time token, and one command people get wrong. Here's the clean path.
tags: [zo, github, git, building, beginner]
related: [get-your-work-out-of-zo, move-an-app-into-zo, secrets-and-keys]
difficulty: beginner
reading_time: 6
---

You built something in Zo and now it lives in one place, on one server, with no version history you can browse and no copy anywhere else. That's a problem the moment you want a collaborator, a backup, or a deploy target. GitHub fixes all three at once, and the connection takes about five minutes because the hard part is already done for you. The GitHub CLI, `gh`, comes pre-installed on every Zo. You are not setting up tooling. You are handing it one token and then talking to it in plain English.

> GitHub is both the exit and the entrance. Once it's wired up, your code can leave Zo and come back without you ever touching a tarball.

## The two paths, and which one to take

There are two ways to authenticate, and one is strictly easier.

The first is to just ask Zo. Say "connect my GitHub" in chat and Zo surfaces a Connect button that runs a device-code flow. You click through, authorize once, and the workspace's `gh` is signed in. No token to copy, no scopes to memorize. If you have no strong reason to do it by hand, do it this way and skip the next section.

The second path is the terminal, by hand. Use it if you want control over the exact token and its scopes, or if you're the type who wants to know what the button did. It works, and it has exactly one trap that catches almost everyone the first time.

## Doing it by hand: make a token

Go to `github.com/settings/tokens/new`. That URL opens the classic personal access token form directly. You want the **classic** token, not the fine-grained one, because fine-grained tokens scope to specific repos and need contents and metadata permissions set per repo, which is more setup than you want on the first try. Classic is the shortest path here.

Give it these three scopes and nothing extra:

| Scope | Why you need it |
| --- | --- |
| `repo` | Create, read, and push to your repositories. This is the core one. |
| `read:org` | Lets `gh` see organizations you belong to, so it can push to org repos. |
| `gist` | Required by `gh` for a few operations. Cheap to include, annoying to be missing. |

Set an expiration you can live with, generate it, and copy the token. It starts with `ghp_`. You see it once. Copy it now, because GitHub will never show it to you again.

## The one command people get wrong

Here is the trap. The reliable way to authenticate `gh` with a token is:

```bash
echo YOUR_TOKEN | gh auth login --with-token
```

You **pipe** the token in. `gh auth login --with-token` reads the token from standard input, not from an argument. The flag takes no value of its own. `gh auth login --with-token ghp_xxxx` fails, because the flag only reads the token from standard input. People try the inline version because it looks obvious, then watch it error out. Don't. Echo the token and pipe it through, every time. Replace `YOUR_TOKEN` with the `ghp_` string you just copied.

A cleaner variant that keeps the token out of your shell history:

```bash
gh auth login --with-token < token.txt
```

where `token.txt` holds the token on one line. Delete the file afterward. If you'd rather keep the token around for scripts, save it as a secret in Settings instead of leaving it in a workspace file, and read it from the environment. There's a separate guide on that, the secrets and keys one, worth reading if you're going to do anything automated.

Confirm it took:

```bash
gh auth status
```

You want to see your username and "Logged in to github.com." If it complains about a missing scope, the token is missing one of the three above. Regenerate with all three and pipe it again.

## Push your first repo

Now the part that makes the setup worth it. Once `gh` is authenticated, you stop typing git incantations and start describing what you want. Zo runs the `gh` and `git` commands for you.

A few phrasings that work cold:

1. "Create a GitHub repo for this project and push it." Zo runs `gh repo create`, sets the remote, and pushes the current state in one go.
2. "Commit my changes and push." For when the repo already exists and you've been working in the workspace.
3. "Pull my repo `[username]/[repo]` into Zo." This is the entrance direction. It clones an existing repo into your workspace so you can keep building on it here.

That third one is the move people underrate. You can start a project on your laptop, push it to GitHub, then pull it into Zo and have your AI work on it on a real Linux server with all of Zo's tools attached. The repo is the shared spine. Both ends sync through it.

## Public or private, decide on purpose

When Zo creates the repo, tell it which you want. "Create a private repo" keeps it to you. "Create a public repo" puts it on your profile for the world. Default to private unless you specifically want the code seen, because flipping a repo from public to private later doesn't un-leak anything someone already cloned. Decide before the first push, not after.

 Token once, pipe don't paste, then talk to it. If you want the other direction covered, getting finished work and files out of Zo cleanly, the guide on getting your work out of Zo pairs with this one, and moving an app into Zo picks up where the `gh repo clone` leaves off. The rest of Zo Computer 101 is built the same way, specific and tested with no hand-waving, and it lives at jeffkazzee.zo.space/writing.
