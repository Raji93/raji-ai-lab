# Facilitator Run of Show

A 60-minute plan for **"Is RAG Dead? Let's Build the Version That Isn't."** Times are
targets — the build steps are the flexible parts if you run long.

| Time | Segment | What you're doing |
|------|---------|-------------------|
| 0:00–0:08 | **Frame the debate** | One slide: "Naive RAG is dying. Retrieval isn't." Show a canned confident-but-wrong answer. Have everyone open [ai.azure.com](https://ai.azure.com). |
| 0:08–0:20 | **Act 1 — build the "dead" version** | Everyone deploys `gpt-4o-mini` and opens the chat playground with no data. ([`01-act1`](../docs/01-act1-the-dead-version.md)) |
| 0:20–0:28 | **Break it together** | Fire the five trap questions. Watch it hallucinate. This is the emotional hook — let people react. ([`03-trap-questions`](../docs/03-trap-questions.md)) |
| 0:28–0:48 | **Act 2 — build the grounded agent** | Create an agent, add the sample docs via File Search, paste the grounding prompt, wait for ingestion, re-ask the same questions. ([`02-act2`](../docs/02-act2-the-grounded-agent.md)) |
| 0:48–0:54 | **Fill the scorecard** | Complete the before/after table as a group. Every Act 1 failure is now grounded or an honest "I don't know." |
| 0:54–0:58 | **The verdict** | Land the opinion: retrieval is alive; the lazy version is dead. Optionally weaken the grounding prompt live to prove it's doing the work. |
| 0:58–1:00 | **Teardown** | Everyone deletes their resources. Put the [teardown checklist](../docs/04-cost-and-teardown.md) on the final slide. |

## Things to protect

- **Pre-work matters most.** The biggest risk is people arriving without an Azure
  account. Send [`00-prerequisites.md`](../docs/00-prerequisites.md) ahead of time and
  reinforce it. Have the **GitHub Models** fallback ready for stragglers.
- **Don't write boilerplate live.** Everything is portal clicks — no code — so the
  main time sinks are account setup and file ingestion. Budget for both.
- **Ingestion lag.** In Act 2, the files take a moment to process. Fill that time by
  explaining the grounding prompt while people wait.
- **Have a finished agent ready.** Keep a pre-built, working agent in your own account
  so that if the room hits a wall, you can still demo the payoff live.

## The one thing to say at the end

This title promises a verdict — so give one. Don't leave it open. Land on:

> *"Retrieval isn't dead. The lazy, ungrounded version is. And you just built the one
> that replaces it."*

That's the line people will quote afterward.
