# Act 2 — Retrieval as a Knowledge Layer

**Goal:** Rebuild the same assistant on **Foundry IQ** — one knowledge base spanning
multiple knowledge sources, with an engine that plans the query instead of running a
single lookup. Then compare the two traces side by side.


> **What Foundry IQ is:** a shared knowledge layer. Instead of wiring retrieval into
> every agent, you define a knowledge base once, connect it to one or more knowledge
> sources, and any number of agents query it through a single endpoint. The retrieval
> engine plans which sources to query, runs searches, and returns grounded results with
> citations.

---

## Step 1 — Create a knowledge base with two sources

A knowledge base is to be crrated using a fodunry IQ resource.update the steps of creating a Fodunry IQ resource in Azure portal here.

In the Foundry portal, create a **knowledge base** and add **two knowledge sources**:

1. **HR source** — upload the two files from
   [`../sample-docs/hr-docs/`](../sample-docs/hr-docs/).
2. **Product source** — upload the one file from
   [`../sample-docs/product-docs/`](../sample-docs/product-docs/).

Same three documents as Act 1 — but no longer one undifferentiated pile. They're now
two named domains under one endpoint.

> **Note:** a knowledge base and its sources must live on the same search service, and
> a single knowledge base can front up to 10 sources.

## Step 2 — Set retrieval reasoning effort to *medium*

This is the setting that matters. **Retrieval reasoning effort** controls how much
planning the engine does. Iterative search — where the engine searches again if the
first results aren't good enough — depends on **medium** effort. On minimal, you get a
single pass.

Set it to **medium**.

## Step 3 — Create an agent that uses the knowledge base

1. Create a **new agent** on the same **`gpt-4o-mini`** deployment. (Keep Act 1's agent
   intact — you'll want both to compare.)
2. Attach the **knowledge base** you just created.
3. Paste the **Act 2 instructions** from
   [`agent-instructions.md`](agent-instructions.md).

Notice the instructions are nearly identical to Act 1's. **The prompt isn't what
changed — the retrieval architecture is.**

## Step 4 — Ask the same questions, and read the new trace

Ask the same questions you asked in Act 1. Then open the trace. It looks different:

```
Conversation
└─ Response
   ├─ Tool: mcp_list_tools
   ├─ Tool: kb-<name>: knowledge_base_retrieve
   └─ Tool: message
```

Three things to point out:

1. **`mcp_list_tools`** — the agent is *discovering* the knowledge base as a tool.
   Knowledge is now an endpoint any agent can call, not retrieval logic baked into this
   one agent.
2. **`knowledge_base_retrieve`** replaces `file_search`. The agent asks the knowledge
   layer for what it needs; the layer decides how to get it.
3. **Click that node.** The output is a list of individually-identified sources —
   each with its own `uid`, snippet, and source file — and the answer cites them
   inline, like `【8:1†product-spec-sheet.md】`. One call, chunks drawn from *both*
   knowledge sources, each separately attributable.

## Step 5 — The honest comparison

Put the two answers side by side. On a three-document corpus, **they will often be
comparable.** Act 1 answers most of these questions well.

Say that out loud. It's the most credible thing you can do, and it sets up the real
lesson:

> *"On three documents, a flat index does fine. That's not a failure of the knowledge
> layer — it's a sign our corpus is small. The architecture matters when the corpus
> doesn't fit in one lookup."*

What genuinely changed is **structural**, and you can point at all of it on screen:

| | Act 1 — flat index | Act 2 — knowledge layer |
|---|---|---|
| Sources | One undifferentiated index | Named sources under one endpoint |
| Retrieval | One search, always | Engine plans; iterative at medium effort |
| Citations | Document name | Per-chunk source IDs across sources |
| Reuse | Retrieval wired into this agent | One knowledge base, many agents |
| Governance | Whatever's in the index | Source-level, permission-aware |
| Scaling | One query must find everything | Source selection narrows the search |

## Step 6 — Trust the trace, not the agent

Worth doing live, because it's a genuinely useful lesson: ask an agent how many
searches it ran. In our testing, an agent confidently claimed **five searches** when the
trace showed exactly **one**.

Models don't have reliable introspection into their own retrieval. If you want to know
what a system did, **read the trace.** That habit will serve attendees far beyond this
lab.

---

## The verdict

Retrieval didn't die. It stopped being a single lookup and became a **layer**:

- **Act 1** — retrieval as a step inside one agent. One index, one search, every time.
- **Act 2** — retrieval as shared infrastructure. Multiple sources, a planning engine,
  per-source citations, reusable across agents.

That's the answer to "is RAG dead?" — *one-shot RAG is fading; retrieval is becoming
infrastructure.*

➡️ Wrap up with [`04-cost-and-teardown.md`](04-cost-and-teardown.md).
