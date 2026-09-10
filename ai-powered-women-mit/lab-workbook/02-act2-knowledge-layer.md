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

## Step 1 — Create an Azure AI Search service

Foundry IQ knowledge bases need a search service to live on, and Act 1's flat index
already used one — but if you're starting fresh for Act 2, or want a dedicated service
for this exercise, create one now:

1. From your Foundry project, jump to [portal.azure.com](https://portal.azure.com) and search for **"AI Search"** and select **Create a search service**.
2. Fill in the **Basics** tab:
   - **Subscription** — your Azure subscription.
   - **Resource group** — reuse the same resource group as your Foundry project (keeps
     everything together for cleanup later).
   - **Service name** — a globally unique, lowercase name (e.g. `test-iq12`). Azure
     checks availability live as you type.
   - **Location** — ideally the same region as your Foundry project.
   - **Pricing tier** — select **Free** (50 MB storage, 1 replica, 1 partition, 1 search
     unit). That's more than enough for this lab's three-document corpus.
3. Click **Review + create**, then **Create**. Deployment takes about a minute.

> ⚠️ **Free tier is capped at one per subscription per region.** If you already have a
> free-tier search service from Act 1, reuse it — you can create the knowledge base on
> the same service instead of provisioning a second one.

## Step 2 — Create a knowledge base with two sources

Back in the Foundry portal, create a **knowledge base** on the search service you just
created, and add **two knowledge sources**:

1. **HR source** — upload the two files from
   [`../sample-docs/hr-docs/`](../sample-docs/hr-docs/).
2. **Product source** — upload the one file from
   [`../sample-docs/product-docs/`](../sample-docs/product-docs/).

Same three documents as Act 1 — but no longer one undifferentiated pile. They're now
two named domains under one endpoint.

> **Note:** a knowledge base and its sources must live on the same search service, and
> a single knowledge base can front up to 10 sources.

## Step 3 — Set retrieval reasoning effort to *medium*

This is the setting that matters. **Retrieval reasoning effort** controls how much
planning the engine does. Iterative search — where the engine searches again if the
first results aren't good enough — depends on **medium** effort. On minimal, you get a
single pass.

Set it to **medium**.

## Step 4 — Create an agent that uses the knowledge base

1. Create a **new agent** on the same **`gpt-4o-mini`** deployment. (Keep Act 1's agent
   intact — you'll want both to compare.)
2. Attach the **knowledge base** you just created.
3. Paste the **Act 2 instructions** from
   [`agent-instructions.md`](agent-instructions.md).

Notice the instructions are nearly identical to Act 1's. **The prompt isn't what
changed — the retrieval architecture is.**

## Step 5 — Ask the same questions, and read the new trace

Ask the same questions you asked in Act 1. Then open the trace. It looks different:

```
Conversation
└─ Response
   ├─ Tool: mcp_list_tools
   ├─ Tool: kb-<name>: knowledge_base_retrieve
   └─ Tool: message
```

Two things to point out before you even look at call count:

1. **`mcp_list_tools`** — the agent is *discovering* the knowledge base as a tool.
   Knowledge is now an endpoint any agent can call, not retrieval logic baked into this
   one agent.
2. **`knowledge_base_retrieve`** replaces `file_search`. The agent asks the knowledge
   layer for what it needs; the layer decides how to get it — including whether one
   call is enough.

### Example 1 — a question with conflicting sources: two calls

Ask: *"How many days a week can I work remotely?"*

The engine calls `knowledge_base_retrieve` **twice**. Here's why: the first call likely
surfaces the Employee Handbook's remote-work section (an older 2-day limit). At
**medium** reasoning effort, the engine judges whether that's actually sufficient — for
a policy question, it isn't confident that's still current, so it searches again. The
second call surfaces the March 2026 People Team memo, which raised the limit to 3 days.
The final answer reconciles both, explicitly noting the memo *supersedes* the
handbook, and cites both files inline:
`【9:0†remote-work-memo.md】【9:1†employee-handbook.md】`.

### Example 2 — a question spanning both knowledge sources: one call

Ask: *"I'm a full-time employee based in the Boulder office, working on customer demos
for the Summit X200 headlamp. How many days a week can I work remotely, and what's the
battery life and warranty on the X200 if a customer asks?"*

This time the engine needs only **one** call — even though the answer draws from
**both** named sources (`hrpolicies` and `productspecs`). A single
`knowledge_base_retrieve` call isn't scoped to one source; it can search across every
source in the knowledge base at once and return individually-attributed chunks from
each. The answer cites `remote-work-memo.md` for the policy half and
`product-spec-sheet.md` twice — once for battery life, once for warranty — each with
its own `uid` and snippet.

**The actual lesson, side by side:**

| | Example 1 | Example 2 |
|---|---|---|
| Question touches | One domain (HR), two conflicting documents | Two domains (HR + Product), complementary documents |
| Calls made | 2 — search, judge insufficient, search again | 1 — first pass already sufficient |
| Why | Reconciling an outdated vs. updated policy needs a second look | Nothing conflicting to resolve; one search spans both sources |

Call count isn't "one call per source" and it isn't "more sources means more calls." It
tracks whether the engine judges its first pass **sufficient** — and one call can
already pull individually-attributable chunks from every source in the knowledge base.
That's the actual capability worth pointing at on screen.

## Step 6 — The honest comparison

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

---

## The verdict

Retrieval didn't die. It stopped being a single lookup and became a **layer**:

- **Act 1** — retrieval as a step inside one agent. One index, one search, every time.
- **Act 2** — retrieval as shared infrastructure. Multiple sources, a planning engine,
  per-source citations, reusable across agents.

That's the answer to "is RAG dead?" — *one-shot RAG is fading; retrieval is becoming
infrastructure.*

