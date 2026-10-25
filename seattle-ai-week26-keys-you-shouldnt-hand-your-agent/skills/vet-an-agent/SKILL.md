---
name: vet-an-agent
description: Check any personal AI agent before signing up — who makes it, what it asks for versus what the task needs, where it runs, how it pays, what approvals and logs it offers, what it keeps, and how to leave. Produces a scored checklist with evidence from official sources, red flags, a verdict (try read-only, try with limits, or walk away), and the first settings to change on day one. Triggers include "should I sign up for", "is this agent safe", "vet this agent", "what does this agent have access to", "compare these agents for privacy", "can I trust", "before I connect my Gmail". This is step 1 of Vet -> Grant -> Audit.
---

# Vet an agent — before you hand over any keys

Step 1 of the safety rhythm: **Vet → Grant → Audit.**
Help a person decide whether to let a personal agent into their accounts, and on what terms.
The person may not be technical. **Write for someone smart and busy, not for a security engineer.**

## When to use / when not to
- **Use** before someone signs up for, connects, or upgrades a personal agent.
- **Don't use** at the consent screen itself (`check-the-consent`) or to review access they've already granted (`audit-your-keys`).

## Input
Any of: the agent's name, its website, its privacy policy or terms, a screenshot of its sign-up flow, and **the task the person wants it for**.

If the task is missing, ask one question: *"What do you want this agent to do for you?"* The task decides what access is reasonable.

## How to work
1. **Find official sources first.** The maker's own site, privacy policy, terms, security page and help center. News coverage is a second source, labeled as such. If you can browse, browse; if not, say what you couldn't check.
2. **Work through the checklist below.** Mark each item `Pass`, `Concern` or `Unknown`, with one line of evidence and its source.
3. **Treat "Unknown" as a concern** until the maker says otherwise. Never fill a gap with a guess.
4. **Check the red list.** If the agent asks for any red-list item, the verdict is *walk away*, whatever else is true.
5. **Give a verdict and day-one settings.**

### The checklist
**A · Who's behind it** — real company and contact; privacy policy and terms that mention agents; how it protects tokens and who can see data; arbitration clause and opt-out window.

**B · Asks vs. needs** — what the task needs; what the consent screen asks for; whether read can be granted without send/edit/delete; whether it ever asks for a password in chat.

**C · Where it runs and how it pays** — maker's cloud, organization tenant or own machine; if self-hosted, not exposed to the internet; one-time or limited cards; acts as the person or under its own identity.

**D · Control while it works** — approvals for send, spend, delete, share and security changes; "Allow once" available; readable activity log; pause or stop; how it handles hidden instructions in emails, invites and web pages.

**E · What it keeps and how to leave** — retention of memory, chats, files and logs; training on user data by default and the opt-out; deleting memory versus disconnecting; account deletion.

### The red list (automatic walk away)
Password manager access · bank or brokerage logins · 2FA or recovery codes · ID documents (passport, driver's license, SSN) · crypto seed phrases · admin or production access at work.

## Output format
Open with a **one-line verdict**: *Try it read-only* · *Try it with limits* · *Walk away* — and the single reason.

Then:
1. **At a glance** — maker · where it runs · what it touches · how it pays · approvals available (yes/no).
2. **Checklist table** — Item · Status (`Pass` / `Concern` / `Unknown`) · Evidence · Source.
3. **Red flags** — only if there are any. One line each.
4. **Day-one settings** — the three to five settings to change before the first real task (for example: email read-only, approvals on for sending and spending, training opt-out, one-time cards only).
5. **What would change the verdict** — the one or two facts that, if found, would move it up or down.

### Style rules
- Plain words. Explain any term the first time it appears.
- **No emoji in the output.** Bold only the verdict and the red flags.
- Short lines. One idea per line.
- Always add: *"Product details change often — confirm on the maker's official site."*
- Never recommend one product over another. Compare facts, not brands.

## Hand-off
When done, offer: *"When you reach the consent screen, send me a screenshot and I'll check each permission (check-the-consent)."*
