---
title: "Put your Site on your own domain"
id: custom-domain-setup
category: hosting
kind: how-to
date: 2026-06-18
updated: 2026-06-18
excerpt: A published Site lives at a zocomputer.io URL by default. Here's how to put your own domain in front of it, the CNAME you need, and the one limitation worth knowing first.
tags: [zo, custom-domain, sites, hosting, dns, beginner]
related: [first-zo-site, space-to-site, zo-hosting-explained]
difficulty: beginner
reading_time: 6
---

You published a Site and Zo handed you a URL like `myapp-yourhandle.zocomputer.io`. It works, it's fast, and it looks like a staging link nobody asked for. If you're sending that to a client or putting it on a business card, you want `app.yourbrand.com` instead. The good news: wiring your own domain to a Zo Site or service takes one CNAME record and about ten minutes of waiting. The catch is a DNS quirk that bites people at the root domain, and I'll get to it before you hit it.

> A custom domain is one CNAME record and a TLS certificate you never have to think about. The only thing that trips people up is the root domain, and that's DNS being DNS, not Zo.

First, two requirements before any of this works. The service has to be **public**. A private site at `*.zo.computer` that asks you to sign in can't take a custom domain, because the whole point of the domain is that strangers can reach it. Second, custom domains are a paid-plan feature. Here's how the limits break down:

| Plan  | Custom domains |
| ----- | -------------- |
| Free  | 0              |
| Basic | 3              |
| Pro   | 5              |
| Ultra | 10            |

If you're on Free, this guide is a preview. Everyone else, keep going.

## Add the domain in Zo

This part lives in the Sites page, under the Services tab. When you publish a Site, Zo runs it as a backing service, so that's where the domain controls are.

1. Open **Sites**, go to the **Services** tab, and find the service for your published site.
2. Click it to expand the details panel.
3. In the **Custom Domains** section, click **Add**.
4. Type the domain you want, like `app.yourbrand.com`, and save.

Zo now expects to see a matching DNS record on your end. It won't go Active until it does. Until then the domain sits in a **Pending CNAME** state, which is Zo politely telling you the ball is in your court.

## Add the CNAME at your DNS provider

Go to wherever your domain's DNS lives. Could be Cloudflare, Namecheap, Porkbun, your registrar's dashboard, wherever you bought the name. Add one record:

| Type  | Name  | Target                |
| ----- | ----- | --------------------- |
| CNAME | `app` | `cname.zocomputer.io` |

The **Name** is just the subdomain part. If your domain is `app.yourbrand.com`, the name is `app`. If it's `blog.yourbrand.com`, the name is `blog`. The target is always `cname.zocomputer.io`, the same for everyone.

One Cloudflare-specific gotcha, because a lot of people park their DNS there. When you add the CNAME, set the proxy status to **DNS only**, the gray cloud icon, not the orange one. If you leave Cloudflare's proxy on, it tries to sit in front of Zo's edge and the certificate handshake fails in a way that's annoying to diagnose. Gray cloud. Write it down.

## Wait for the green light

Once the CNAME is out there, Zo's job is automatic. It registers the domain with Cloudflare's edge network, provisions a TLS certificate so you get HTTPS without touching anything, and routes traffic from your domain to your service. The whole thing usually finishes in 1 to 15 minutes after DNS propagates.

You'll watch it move through a few states:

| Status        | What it means                                       |
| ------------- | --------------------------------------------------- |
| Pending CNAME | Zo hasn't seen your record yet                      |
| Pending SSL   | Record found, certificate being issued              |
| Active        | Live and serving traffic over HTTPS                 |
| Error         | DNS is misconfigured, go back and check the record  |

If it's stuck on Pending CNAME longer than feels reasonable, DNS propagation is the usual culprit. Use the recheck control in the Custom Domains panel to force a re-verify instead of waiting for Zo to poll on its own. You can also confirm your record resolves from the command line:

```bash
dig CNAME app.yourbrand.com
```

That should print `cname.zocomputer.io` as the answer. If it prints nothing or the wrong target, the record didn't save the way you think it did.

## The apex domain catch

The apex is where this gets fiddly, and it's worth understanding instead of fighting. Zo's custom domains are CNAME-based. CNAME records work great for subdomains. They do not work for the apex, the bare root of your domain, `yourbrand.com` with nothing in front. That's not a Zo limitation specifically; the DNS spec itself forbids a CNAME on the apex because the root already has other records (like the SOA and NS records) that a CNAME isn't allowed to coexist with.

So `app.yourbrand.com` and `www.yourbrand.com` are fine. `yourbrand.com` on its own is not.

The standard fix: pick a subdomain as your real home, usually `www`, point it at Zo with the CNAME above, then set up a redirect at your registrar that forwards the bare `yourbrand.com` to `www.yourbrand.com`. Most registrars have a one-line forwarding rule for exactly this. Cloudflare does it with a redirect rule. The result is that someone typing the naked domain lands on your www subdomain, which is the one actually wired to your Site. Visitors never notice. You just have to set it up on purpose.

One more practical note while you're in here: each custom domain points to one service at a time, and if you delete the service, the domain comes off with it. So pick the service you actually want this name on before you wire DNS.

That's the full path. Public service, paid plan, one CNAME to `cname.zocomputer.io`, gray cloud if you're on Cloudflare, and a registrar redirect if you care about the bare root. Ten minutes of clicking and a few minutes of waiting, and the staging-looking URL is gone.

If you haven't published the Site yet, the hosting overview guide covers when to use a Site versus a Space versus a plain service, and the building your first Zo Site guide walks the publish step itself. The rest of Zo Computer 101 is built the same way, specific and tested, over at jeffkazzee.zo.space/writing.
