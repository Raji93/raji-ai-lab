---
name: audit-your-keys
description: Run a monthly audit of the access a person has given AI agents and third-party apps. Takes screenshots or lists from Google's linked apps page, Microsoft's app permissions page, and each agent's connector settings, then sorts every connection into keep, downgrade, or revoke with the reason, gives step-by-step removal instructions, lists which agents still hold memory that should be reset, and produces an audit log to save. Triggers include "audit my agent access", "what have I connected", "clean up my connected apps", "key audit", "which apps can read my email", "revoke old permissions", "monthly security check". This is step 3 of Vet -> Grant -> Audit.
---

# Audit your keys — once a month

Step 3 of the safety rhythm: **Vet → Grant → Audit → repeat.**
Keys don't expire when you stop using an agent. This skill finds the ones that should.

## When to use / when not to
- **Use** once a month, after trying a new agent, or after any "did I connect that?" moment.
- **Don't use** at a live consent screen (`check-the-consent`) or before signing up (`vet-an-agent`).

## Input
Any of:
- A screenshot or list from **Google:** myaccount.google.com/linkedapps (under **View by**: **Access to › Any account access** first — these apps can read or change Google data — then **Linked account**, then **Sign in with Google**, which only signs the person in and is lowest risk).
- A screenshot or list from **Microsoft:** microsoft.com/consent (personal) or the work account's app permissions.
- Screenshots of each agent's **connector or app settings** (usually under Settings › Connectors, Apps or Integrations).
- The person's own notes: "I tried X in the summer and haven't used it since."

If they share nothing, walk them through collecting it first, in that order. Keep it to 15 minutes.

## How to work
1. **Build one list** of every app or agent, what it can touch, and when it was last used (if shown).
2. **Apply the rules in order:**
   1. Touches anything on the **red list** (password manager, bank or brokerage, 2FA or recovery codes, ID documents, seed phrases, work admin access) → **revoke now**.
   2. Not used in **30 days** → **revoke**.
   3. Can **send, delete, spend or share**, and the person doesn't need that → **downgrade** (to read-only, or ask-first).
   4. Still used and limited to what it needs → **keep**.
3. **Unknown "last used"?** Ask the person. If they don't remember, treat it as unused.
4. **Check memory, not just access.** For every agent being revoked, add the step to reset or delete what it already learned. Disconnecting isn't deleting.

## Output format
Open with a **one-line summary**: *"X connections: revoke N, downgrade N, keep N."* Put red-list items first if there are any.

Then:
1. **Revoke now** — red-list items, each with where to click.
2. **Audit table** — App or agent · What it can touch · Last used · Decision · Why.
3. **How to do it** — step-by-step for each place (Google, Microsoft, each agent), in the order that takes the least time.
4. **Make it forget** — which agents still hold memory or activity, and how to reset each.
5. **Audit log** — a clean copy of the table with today's date, ready to paste into notes.
6. **Next audit** — suggest a date one month out and offer to draft a calendar reminder.

### Style rules
- Plain words. No emoji in the output.
- Bold only the decisions in the "Revoke now" list.
- Don't shame the person for what they connected. Just make the list shorter.
- If a screenshot is cut off, say which part is missing.
- Agent settings menus change often; tell the person if a path might have moved.
