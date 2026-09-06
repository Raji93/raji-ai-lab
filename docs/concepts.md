# Concepts — From One-Shot RAG to a Knowledge Layer

## The evolution in one line

**Model memory alone → one-shot RAG → agentic retrieval → a knowledge layer.**

Each step exists because the one before it ran out of room.

## 1. Model memory alone

The model answers from training data. It has never read your handbook and its knowledge
stops at a fixed date. For anything private or current, it can only guess.

## 2. One-shot RAG

Look something up before answering. Break documents into **chunks**, convert each into
an **embedding** (a list of numbers representing meaning), store them in a vector
index, and at question time retrieve the few closest chunks and answer from them.

This is Act 1. It's genuinely good — and it's **fixed**: one index, one query, one pass,
every time.

## 3. Agentic retrieval

Treat retrieval as a reasoning loop instead of a single lookup: **retrieve → read →
decide → search again → ground the answer.** The system assesses whether what it found
is enough and searches again if not.

## 4. The knowledge layer

Stop wiring retrieval into every agent. Define a **knowledge base** once, connect it to
multiple **knowledge sources**, and let any agent query it through one endpoint. The
engine plans which sources to query and returns grounded, cited results. This is Act 2 —
Foundry IQ.

## Why people say "RAG is dead"

Three different arguments get compressed into one slogan:

**"Context windows got huge — just paste everything in."** Weak. Models don't reason
evenly across a huge context (the *lost in the middle* problem), and you pay for every
token on every question. Retrieving the relevant slice is cheaper and often better.

**"One-shot RAG breaks."** Real. A single lookup genuinely struggles with vague or
multi-step questions. This is the critique agentic retrieval answers — and it's the one
this lab is about.

**"Vector databases are dead."** Partly real. Vector search is one retrieval method, not
the definition of retrieval. Coding agents often read files directly; exact-match
questions want keyword search; structured data wants SQL. Match the method to the data.

## What this lab actually demonstrates

Be precise, especially with a technical audience:

- On a **small, clean corpus**, flat File Search and a knowledge base perform
  **comparably**. We tested this. Don't claim otherwise.
- What differs is **architecture**: named sources vs. one pile, a planning engine vs. a
  single query, per-chunk cross-source citations, and retrieval that's reusable across
  agents and governable per source.
- Those differences pay off at **enterprise scale** — thousands of documents, many
  domains, real permissions — which is exactly when you can't afford to re-architect.

## So, is RAG dead?

No. **One-shot RAG is fading, and retrieval is becoming infrastructure.**

The only world where retrieval dies is one where a model could read your entire
knowledge base perfectly, once, and never need to look again. Knowledge doesn't work
that way — documents change, policies get superseded, decisions get made. Something has
to go and check.

> **RAG is only dead if knowledge never changes.**

## When to use what

| Situation | Reach for |
|---|---|
| Stable FAQ, manual, contained knowledge | One-shot RAG |
| Open-ended, multi-step, shifting knowledge | Agentic retrieval |
| Both exact-match and semantic needs | Hybrid retrieval |
| Many sources, many agents, real governance | A knowledge layer |
