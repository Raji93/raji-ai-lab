# Get Set Up

**Do this now, while we review the opening slides.** Creating a free Azure account is
the one prerequisite for following along — we'll start building the lab in a few
minutes, and you'll need this ready to go.

The whole lab runs **in your browser** in the Microsoft Foundry portal. There's no
code to write and nothing to install. Just two things to get in place:

---

## 1. A laptop

A **laptop is strongly preferred** — the Microsoft Foundry portal is hard to work in
on a phone or tablet. Any laptop with a modern browser (Chrome, Edge, or Firefox) and
reliable Wi-Fi will do.

## 2. Create a free Azure account

You'll sign in to the Microsoft Foundry portal at **[ai.azure.com](https://ai.azure.com)**
with a free Azure account. Create one now:

👉 **[Create your free Azure account](https://azure.microsoft.com/en-us/pricing/purchase-options/azure-account?icid=azurefreeaccount)**

- Select **"Try Azure for free"** and follow the prompts.
- You'll get a **$200 credit** (valid 30 days) plus free monthly amounts of 20+
  services — far more than this lab needs.
- **Sign in with a personal Microsoft account or GitHub account.**
- Have a **phone number** and a **non-prepaid credit or debit card** ready for
  identity verification.
- **You won't be charged.** The free account has spending protection, and any $1
  authorization hold you see during signup is temporary and gets reversed.
- Budget about **15 minutes** to complete it.

> **Please use a personal free account, not your work/corporate account.** Company
> tenants often block the resource creation this lab needs, and you don't want to hit
> a permissions wall while we're building. A fresh free account avoids all of that.
>
> The free account with $200 credit is for **new** Azure customers, one per person.

---

## What we'll do together (so you know what's coming)

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
