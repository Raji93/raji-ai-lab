# Before You Arrive — Prerequisites

This lab runs **entirely in your browser** in the Microsoft Foundry portal. There's
no code to write and nothing to install. But a few things need to be set up *before*
the session so we don't lose lab time to account creation.

**Please complete steps 1–2 before you walk in.** Step 3 is a backup.

---

## 1. Bring a laptop

Any laptop with a modern browser (Chrome, Edge, or Firefox) and reliable Wi-Fi.
A tablet will struggle with the portal — a laptop is strongly recommended.

## 2. Get access to Microsoft Foundry

You need an Azure account to sign in to the Microsoft Foundry portal at
**[ai.azure.com](https://ai.azure.com)**.

Pick whichever applies to you:

- **You already have an Azure subscription** (personal or through work where you can
  create resources): you're all set. Just confirm you can sign in at
  [ai.azure.com](https://ai.azure.com).
- **You don't have one:** create a **free Azure account**, which includes credit for
  new users, at [azure.microsoft.com/free](https://azure.microsoft.com/free). This
  takes about 15 minutes and requires a credit card for identity verification (you
  won't be charged on the free tier). **Do this the day before, not in the room.**

> If your employer's Azure tenant blocks resource creation, use a personal free
> account instead — you don't want to discover a permissions block mid-lab.

## 3. Backup: a GitHub account (no Azure needed)

If your Azure account isn't ready in time, you can still follow along using
**GitHub Models**, which gives free access to many of the same models with just a
GitHub login. Have a [github.com](https://github.com) account ready as a fallback.
We'll point you to this only if you get stuck on Azure setup.

---

## What we'll do together (so you know what to expect)

- **Act 1:** Ask a bare AI model some questions about a company it's never heard of,
  and watch it confidently make up the answers.
- **Act 2:** Give that same model the company's actual documents, turn on grounding,
  and watch the answers become correct, cited, and honest.

You'll leave with your own grounded document agent you can point at your own files.

---

## Cost

This lab is designed to cost **almost nothing** — cents at most — because we use a
small model and a managed, auto-expiring document store. We'll walk through deleting
everything at the end so there are no surprises. See
[`04-cost-and-teardown.md`](04-cost-and-teardown.md).
