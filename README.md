# Is RAG Dead? Let's Build the Version That Isn't

A hands-on, no-code lab for the **AI-Powered Women Conference 2026** Tinkering Lab.

> "RAG is dead" was the hottest take of 2026 — and like most hot takes, it's half
> right in a way that makes it mostly wrong. In this lab we settle the debate by
> **building both sides**, entirely in the browser. You'll watch a bare model
> confidently make up answers, then rebuild it as a grounded agent that cites its
> sources and refuses to guess. Same questions, both times — and the difference is
> the whole point.

## What you'll build

A document-Q&A experience in two acts, all in the **Microsoft Foundry** portal:

- **Act 1 — the "dead" version:** a plain model with no grounding that hallucinates
  confidently about a company it's never heard of.
- **Act 2 — the version that isn't:** an agent grounded in real documents that answers
  only from its sources, cites them, and says "I don't know" when it should.

No code. No local setup. Just a browser and about an hour.

## What you'll leave with

- Your own grounded, citation-backed document agent you can point at your own files.
- A clear, opinionated answer to "is RAG dead?" — backed by a demo, not a shrug.

---

## Start here

1. **[Prerequisites](docs/00-prerequisites.md)** — do this *before* the session
   (create your account so we don't lose lab time).
2. **[Act 1 — The Dead Version](docs/01-act1-the-dead-version.md)** — build the bare
   model and watch it fail.
3. **[Act 2 — The Grounded Agent](docs/02-act2-the-grounded-agent.md)** — add
   documents, ground it, and watch it recover.
4. **[Cost & Teardown](docs/04-cost-and-teardown.md)** — clean up so there are no
   surprise charges.

## Repo contents

| Path | What's inside |
|------|---------------|
| [`docs/`](docs/) | The step-by-step lab: prerequisites, both acts, the grounding prompt, trap questions, and teardown |
| [`sample-docs/`](sample-docs/) | The fictional **Summit Gear Co.** document set your agent will use |
| [`facilitator/`](facilitator/) | Run of show and facilitator notes (60-minute timing) |

## Key reference files

- **[The trap questions](docs/03-trap-questions.md)** — the five questions you'll ask
  in both acts, with expected before/after answers.
- **[The grounding prompt](docs/grounding-prompt.md)** — the system prompt that turns
  a guessing model into a grounded one.

---

## Why this lab keeps costs near zero

It uses a small model (`gpt-4o-mini`) and the agent's **File Search on basic setup**,
which relies on a Microsoft-managed, auto-expiring document store — so there's **no
separate search service to provision or pay for**. Expect cents per person, and the
[teardown steps](docs/04-cost-and-teardown.md) remove everything at the end.

## Make it your own

Want to reuse this for another talk? Swap in your own company and documents in
[`sample-docs/`](sample-docs/), keeping the four trap types described in the
[sample-docs README](sample-docs/README.md), and the lab still works.

---

*Facilitator: Rajya Laxmi Yellajosyula — Senior AI Product Manager, Microsoft.*
*Summit Gear Co. is a fictional company created for this lab.*
