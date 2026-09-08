# Is RAG Dead? Let's Build the Version That Isn't

### MIT AI-Powered Women — Tinkering Lab, 2026

**Welcome — and thank you so much for joining me today!** 👋

I'm really glad you're here. Whatever brought you to this room — curiosity, a project
at work, or just wanting to see what all the noise is about — you're in the right
place, and I'm looking forward to building something with you.

Over the next hour we're going to settle an argument the internet has been having all
year. Not by debating it, but by building both sides of it and looking closely at what
each one actually does under the hood.

**A promise before we start: you don't need to know anything coming in.** No code, no
prior AI experience, nothing to install. Everything happens in your browser, and we'll
go step by step together. If you've never built anything with AI before, this is a
lovely place to start — and if you build these systems for a living, stick around,
because we're going to open up the retrieval traces, which is where it gets genuinely
interesting.

If you get stuck at any point, just say so. There is no such thing as a silly question
in this room, and something going sideways is usually the most interesting thing that
can happen in a lab.

---

## First, what is RAG?

**RAG** stands for **Retrieval-Augmented Generation**. It's a mouthful for a simple
idea: *let the AI look something up before it answers.*

On its own, a model only knows what it learned during training. It has never read your
company handbook, doesn't know your product specs, and its knowledge stops at some date
in the past. Ask it *"how many vacation days do I get?"* and it has no choice but to
guess.

RAG fixes that. Before the model answers, the system finds the relevant page from your
documents and hands it over. It's the **open-book version of AI**: fetch the right
pages first, then answer.

### How the "fetch" part actually works

<img width="1536" height="1024" alt="Designer (41)" src="https://github.com/user-attachments/assets/151c5be3-96a2-4977-93ba-de4e977c394f" />

In short: documents get split into small **chunks**, each chunk's meaning is turned into
a list of numbers (an **embedding**), and when you ask a question it gets turned into
numbers the same way. The system then hands the model whichever chunks sit **closest**
to your question.

**You'll see this live.** In Act 1 we open the trace and look at the actual chunks that
came back, with their real relevance scores.

---

## So what's the debate?

For a couple of years, RAG was *the* thing to learn in AI. Then the tone flipped and
you started seeing **"RAG is dead"** everywhere. Three different arguments hide behind
that one slogan:

| Camp | The claim | Verdict |
|---|---|---|
| **1** | Context windows got huge — just paste everything in | Weak — cost, latency, and models reasoning unevenly over long context |
| **2** | One-shot RAG breaks on real questions | **Real** — this is the one worth taking seriously |
| **3** | Vector databases are dead | Partly real — vector search is one method, not all of retrieval |

Meanwhile the other half of the internet insists retrieval matters more than ever.
**So who's right?** Let's build it and find out.

---

## What we're going to do

We'll build the same assistant twice, over the same three documents, in the
**Microsoft Foundry** portal:

**Act 1 — Retrieval as a lookup.**
Classic RAG: all three documents in one index, one search per question. It works well!
Then we open the trace and learn to read what it's actually doing — the chunks, the
files, the relevance scores. You'll notice the shape never changes: one search, one
answer, no matter how hard the question is.

**Act 2 — Retrieval as a knowledge layer.**
We rebuild it on **Foundry IQ**: one knowledge base spanning two named sources (HR and
Product), with an engine that plans the query instead of running a single lookup. Same
model, nearly the same prompt — different architecture. We read that trace too, and
compare.

### An honest note about what you'll see

On three clean documents, **both versions answer well.** We tested this thoroughly, and
we're not going to pretend Act 1 falls over — it doesn't. What changes is the
*architecture*: named sources instead of one pile, a planning engine instead of a single
query, per-chunk citations across sources, and retrieval that's shared across agents
rather than wired into one.

Those differences are what matter at ten thousand documents. Understanding them on
three is how you get there.

---

## What we'll have settled by the end

> **Retrieval isn't dead. It stopped being a single lookup and became infrastructure.**
>
> Or put another way: **RAG is only dead if knowledge never changes.**

## What you'll walk out with

- **Two working assistants** you can point at your own documents.
- **The ability to read a retrieval trace** — open it up, see which chunks came back and
  why. This is the durable skill, and most people have never seen it.
- **A decision framework**: when one-shot RAG is genuinely enough, and when you need a
  knowledge layer.
- **A real answer** to the debate, backed by something you built.

---

## Ready? Start here

1. **[Prerequisites](lab-workbook/00-prerequisites.md)** — set up your free Azure account if you havent already done this.
2. **[Act 1 — Retrieval as a Lookup](lab-workbook/01-act1-flat-index.md)** — build it, then read
   the trace.
3. **[Act 2 — Retrieval as a Knowledge Layer](lab-workbook/02-act2-knowledge-layer.md)** —
   rebuild on Foundry IQ and compare.
4. **[Cost & Teardown](lab-workbook/04-cost-and-teardown.md)** — clean up (especially the search
   service!).
5.  **summit-gear-docs.zip	All three documents in one download — grab this at the start of Act 1**

## A note on cost

We use a small model and small documents, so the model side costs cents. The one thing
to watch is that Act 2's knowledge base runs on **Azure AI Search**, which bills while
it exists — only use the **free tier** and delete it at the end. We'll tear everything down
together.

---

*Facilitator: Rajya Laxmi Yellajosyula — Senior AI Product Manager, Microsoft.*
*Summit Gear is a fictional company created for this lab.*
