# Act 1 — Retrieval as a Lookup

**Goal:** Build classic RAG — one index, one search, one answer — and learn to read what it's actually doing under the hood. 
By the end of this act you'll be able to open a trace and see exactly which chunks the model was handed.

**Time:** ~20 minutes

---

## Before you click anything — what you're actually creating

Foundry isn't a single thing you log into. Three pieces have to exist before you can
build an agent, and the portal creates them in this order:

1. **A Foundry resource** — created in the **Azure portal**. This is the Azure resource
   that holds everything.
2. **A project** — your workspace inside that resource, for models, agents, and files.
3. **A model deployment** — an actual running instance of a model (like `gpt-4o-mini`)
   for your agent to think with.

Only then can you create an agent. We'll do these in order.

> **You'll need permission to create resources.** On a personal free Azure account
> you'll have this automatically. On a work account you may not — which is why the
> prerequisites ask everyone to use a **personal** free account.

---

## Step 1 — Create your Microsoft Foundry resource

We start in the **Azure portal**, not the Foundry portal. The Foundry resource has to
exist in your Azure subscription first — the Foundry portal is the workspace you get
*after* that resource is created.

1. Go to **[portal.azure.com](https://portal.azure.com)** and sign in with the free
   Azure account you created in the prerequisites.
2. In the search bar at the top, search for **Microsoft Foundry** and select the
   service.
3. Select **Create**.
4. **Create a new resource group.** Give it a name like `rag-lab-rg`. Putting
   everything in its own resource group means you can delete the whole lab in one
   action at the end.
5. Give your Foundry resource a **unique name** — names have to be globally unique, so
   add something personal, e.g. `rag-lab-<yourname>`.
6. **Leave everything else as the default.** Region, network, and identity defaults are
   all fine for this lab.
7. Select **Review + create**, then **Create**, and wait for deployment to finish
   (usually a couple of minutes).

Once it says the deployment is complete, select **Go to Foundry portal**. That takes
you to [ai.azure.com](https://ai.azure.com), already pointed at the resource you just
made — this is where you'll spend the rest of the lab.

> **While you wait:** provisioning takes a few minutes. Good moment to look at the
> chunking-and-embeddings diagram in the [main README](../README.md), because you'll see
> those exact chunks in the trace shortly.

> **If Create is greyed out or you get a permissions error:** your account can't create
> resources in that subscription. This is the most common blocker on a work account —
> switch to a **personal** free Azure account.

## Step 2 — Deploy a model

You're now in the **Foundry portal**. A project is usually created for you along with
the resource — if you don't see one, create a project now and give it any name.

An agent needs a deployed model to think with. Deploying creates your own endpoint for
that model inside the project.

1. In the Foundry portal, open the **Model catalog** (under **Discover → Models** in
   some layouts).
2. Search for and select **`gpt-4o-mini`**.
3. Select **Deploy**, choose the **Global Standard** deployment type, and keep the
   default deployment name.
4. Confirm, and wait for the deployment to finish.

> **Why `gpt-4o-mini`?** It's inexpensive, fast, and more than capable for this lab. We
> use the **same model in both acts on purpose** — so if Act 2 behaves differently,
> it's the retrieval architecture doing the work, not a bigger model.

> **If you don't see the model:** availability varies by region. Pick any small, current
> chat model that's offered in your region — the lab works the same with any of them.
> Just use the same one in both acts.

Once the deployment shows as succeeded, you're ready to build the agent.

## Step 3 — Create an agent with File Search

1. Open **Agents** and create a **new agent** on your `gpt-4o-mini` deployment.
2. In the **Setup** pane, find **Knowledge** and select **Add → Files**.
3. Upload **all three** documents from [`../sample-docs/`](../sample-docs/) — into this **one** index.
4. Finish adding the **File Search** tool.

That flatness is the point: three documents, two very different topics, one
undifferentiated index. This is how most RAG systems get built the first time.

**Wait for ingestion to finish** before asking anything.

## Step 4 — Set the instructions

Paste the **Act 1 instructions** from [`agent-instructions.md`](agent-instructions.md)
into the agent's **Instructions** field.

## Step 5 — Ask, and then open the trace

Ask an easy question first:

> What's our PTO policy?

You'll get a correct, cited answer. Now do the important part: **open the conversation
trace.** In the Foundry portal, open the run/thread detail for that message.

You'll see a tree like this:

```
Conversation
└─ Response
   ├─ Tool: file_search
   └─ Tool: message
```

Click the **`file_search`** node. On the right you'll see what actually came back:
the **file name**, a **relevance score**, and the **raw chunk text** the model was
handed. Most people have never seen the inside of a RAG call — take a minute here.

This is the single most useful skill in the whole lab. Everything else builds on being
able to read this view.

## Step 6 — Notice the shape never changes

Ask the harder questions from [`03-questions.md`](03-questions.md) and open the trace
each time:

- *"How many days a week can I work remotely?"* (needs the handbook **and** the memo)
- *"Which product should a new employee buy with their gear allowance, and how much is
  left over?"* (needs HR **and** product docs, plus arithmetic)
- *"What's covered if my headlamp battery dies in year two?"* (spec sheet **and**
  warranty policy)

**The answers are often good** — this is the honest part. Flat File Search on a clean
corpus is strong, and it will handle several of these well.

But look at the trace every time. It's always the same shape:

```
file_search → message
```

One search. One pass. The same behavior whether the question needs one fact or five,
one document or four. Simple RAG doesn't *think* about retrieval — it retrieves, then
answers.

## Step 7 — Note what you'd want at scale

With three documents, one broad search can scoop up most of what's relevant. Ask
yourself what happens when this index holds **ten thousand** documents across HR,
product, support, legal, and engineering:

- One query has to be good enough to find everything, on the first try.
- HR questions and product questions compete for space in the same result set.
- Nothing decides *which* part of the corpus is worth searching.
- There's no way to apply different permissions to different content.

That's the pressure Act 2's architecture is built for.

---

➡️ Continue to [`02-act2-knowledge-layer.md`](02-act2-knowledge-layer.md)
