<img width="1200" height="400" alt="banner" src="https://github.com/user-attachments/assets/e8a8974d-223d-443f-af37-df553424d157" />
<div align="center">
<p><strong>Welcome, and thank you for joining me at <a href="https://luma.com/b58ib6mr">Seattle AI Week 2026</a>.</strong></p>


## 🎤 Session reference

If you're here because of my session, you can find the details here:

[Keys You Shouldn't Hand Your Agent: Staying Safe as Personal Agents Take Over Home and Work · Luma](https://luma.com/b58ib6mr)


<p><strong>If you're here, you're probably about to let an AI agent into your inbox, calendar or wallet, or you already have.</strong></p>

</div>

---

## ✨ Why this repo exists

In 2026, personal agents went from demos to daily use. They read your mail, book your travel, pay with your cards, and keep working while you sleep. Every one of them starts with the same moment: you click **Allow**.

This playbook helps you make that click on purpose. It will help you:

- 🧠 understand what an agent is, and what makes a *personal* agent different
- ✅ vet an agent before you sign up
- 🔐 know which keys never to hand over
- 🧹 audit what you've already granted, in 15 minutes

The goal is not to scare you off agents. It is to help you use them with your eyes open.



## 🔄 The core loop

**Vet → Grant → Audit**

This is the safety rhythm for any personal agent:

- **Vet**: before you sign up, find out who's behind it, what it asks for and where it runs
- **Grant**: at the consent screen, start read-only, prefer "Allow once", and keep approvals on
- **Audit**: once a month, revoke what you don't use and make the agent forget what it doesn't need

---

## 🧩 What's inside

This folder includes:

- **A playbook to understand how personal agents work**
- **Three skills**, one for each step of the loop
- **Three paste-ready prompt versions** of those skills, for any AI chat
- **A printable one-page checklist that you can fully use**

### The playbook

 [`playbook/playbook.md`](./playbook/playbook.md)

| # | Page | What you'll get |
|---|---|---|
| 1 | [What is an agent?](./playbook/playbook.md#part-1-what-is-an-agent) | From chat to always-on agents, what an agent is made of, and how a personal agent differs |
| 2 | [Before you sign up](./playbook/playbook.md#part-2-before-you-sign-up) | A checklist for evaluating any personal agent |
| 3 | [Never hand over](./playbook/playbook.md#part-3-never-hand-over) | The red list, the always-ask list, and the permission ladder |
| 4 | [The 15-minute key audit](./playbook/playbook.md#part-4-the-15-minute-key-audit) | A monthly routine to revoke, downgrade and make agents forget |

### Skill map

| Skill | Step | Purpose |
|---|---|---|
| [`vet-an-agent`](./skills/vet-an-agent/SKILL.md) | Vet | Check any personal agent against the sign-up checklist before you join |
| [`check-the-consent`](./skills/check-the-consent/SKILL.md) | Grant | Paste or screenshot a consent screen and get a plain-language verdict on each permission |
| [`audit-your-keys`](./skills/audit-your-keys/SKILL.md) | Audit | Turn your connected-apps lists into a keep / downgrade / revoke plan |

Paste-ready versions live in [`prompts/`](./prompts). The one-page checklist is in [`checklists/`](./checklists).


---

## 🚀 Quick start

If you only do three things:

1. **Tonight:** run the [15-minute key audit](./playbook/playbook.md#part-4-the-15-minute-key-audit). Remove anything you don't use.
2. **Before your next sign-up:** paste the [`vet-an-agent`](./prompts/vet-an-agent.md) prompt into any AI chat with the agent's name.
3. **At the consent screen:** take a screenshot and run it through [`check-the-consent`](./prompts/check-the-consent.md) before you tap Allow.

Then print the [one-page checklist](./checklists/access-checklist.pdf) and keep it near your desk.

---

## 🌟 If you like this

If this resource helped you, please consider leaving a star on the repo. It means a lot to me and helps more people discover it.

Have suggestions, a correction, or an agent I should add? I'd love to hear from you. Reach out on [LinkedIn](https://www.linkedin.com/in/rajya).

---

## 📝 Notes

Views and materials are my own and do not represent my current or former employers. This is strictly educational, and nothing here is a product endorsement.

No specific products are reviewed or recommended here. Agents and their settings change fast, so always check the maker's official site before you rely on a detail.

These skills help structure your thinking, but they do not replace your own judgment. When in doubt, grant less.

---

## 📜 License

This project is released under CC0 1.0. You are free to use, adapt, and share it.

Thank you again for stopping by. I hope this helps you hand over fewer keys, and the right ones.
