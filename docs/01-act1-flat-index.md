# Act 1 — Retrieval as a Lookup

**Goal:** Build classic RAG — one index, one search, one answer — and learn to read
what it's actually doing under the hood. By the end of this act you'll be able to open
a trace and see exactly which chunks the model was handed.

**Time:** ~20 minutes

---

## Step 1 — Sign in and create a project

1. Go to **[ai.azure.com](https://ai.azure.com)** and sign in.
2. Create a new **project** (accept the defaults if prompted for a resource or hub).
   Name it something like `rag-is-dead-lab`.

## Step 2 — Deploy a model

1. Open the **Model catalog**.
2. Select **`gpt-4o-mini`**, click **Deploy**, choose **Global Standard**, confirm.

> We use the same model in both acts on purpose. If Act 2 behaves differently, it's the
> retrieval architecture doing the work — not a bigger model.

## Step 3 — Create an agent with File Search

1. Open **Agents** and create a **new agent** on your `gpt-4o-mini` deployment.
2. In the **Setup** pane, find **Knowledge** and select **Add → Files**.
3. Upload **all three** documents from [`../sample-docs/`](../sample-docs/) into this **one** index.
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
one document or four. 

**Simple RAG doesn't *think* about retrieval — it retrieves, then answers.
**

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
