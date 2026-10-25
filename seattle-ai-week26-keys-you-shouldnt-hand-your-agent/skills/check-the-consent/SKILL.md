---
name: check-the-consent
description: Review an AI agent's consent or permissions screen before the person taps Allow. Takes a screenshot or pasted text of a Google, Microsoft, or agent consent screen plus the task the person wants done, translates every permission into plain words, rates each one green (needed and low risk), amber (needs approvals or a narrower version) or red (don't grant), flags "Select all", hidden extra apps, send/delete/full-drive scopes and offline access, and returns a verdict with exactly what to uncheck. Triggers include "should I allow this", "what does this permission mean", "check this consent screen", "it's asking for access to my Gmail", "is this scope too much", "Allow or Cancel". This is step 2 of Vet -> Grant -> Audit.
---

# Check the consent — before you tap Allow

Step 2 of the safety rhythm: **Vet → Grant → Audit.**
The consent screen is the moment keys change hands. Help the person grant **only what the task needs.**

## When to use / when not to
- **Use** when someone is looking at a "This app wants to…" screen, a connector setup, or an agent's permission settings.
- **Don't use** to decide whether to sign up at all (`vet-an-agent`) or to review old grants (`audit-your-keys`).

## Input
1. A screenshot or the text of the consent screen (all of it — ask them to scroll and capture the rest if it looks cut off).
2. **The task** they want the agent to do.

If the task is missing, ask for it first. Without it, every permission looks either fine or scary.

## How to work
1. **List every permission on the screen**, including ones under "See more" or behind a "Select all" option.
2. **Translate each into plain words.** Example: "See, edit, create and delete all your Google Drive files" → *"It can open, change and delete every file in your Drive."*
3. **Compare against the task.** Does the task need it? Could a narrower version work (read instead of send, one calendar instead of all)?
4. **Rate each permission:**
   - **Green** — the task needs it and it can't send, spend, delete or share.
   - **Amber** — the task may need it, but only with approvals on or a narrower version.
   - **Red** — the task doesn't need it, or it touches the red list.
5. **Look for the common traps:**
   - The intro screen names fewer apps than the consent screen asks for.
   - "Select all" is one tap away.
   - Delete permissions bundled with read (for example, calendar access that includes "permanently delete").
   - "Send email on your behalf" when the task is only reading.
   - Full Drive access when the task needs one folder or file.
   - Offline or always-on access ("even when you're not using the app").
   - Requests to type a password, 2FA code or card number into chat.
6. **Give a verdict.**

## Output format
Open with the **verdict** in one line:
- **Allow** — everything is green.
- **Allow, but uncheck these first** — list them.
- **Don't allow** — and the one reason.

Then:
1. **Permission table** — Permission (as written) · What it really means · Needed for your task? · Rating.
2. **Uncheck before you continue** — a short list, if any.
3. **Turn on after you connect** — approvals for sending, spending, deleting and sharing; read-only where offered; one-time cards for payments.
4. **If you can't uncheck it** — what to do instead: pick a narrower option, use a separate account, or don't connect this app.

### Style rules
- Plain words. Quote the permission exactly once, then explain it.
- **No emoji in the output.** Bold only the verdict.
- Never assume a permission is safe because a big company asks for it.
- If the screenshot is unreadable or cut off, say which part you couldn't read rather than guessing.

## Hand-off
When done, offer: *"Once a month, run the key audit (audit-your-keys) to remove anything you no longer use."*
