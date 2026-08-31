# Act 1 — The "Dead" Version

**Goal:** Build the simplest possible setup — just a model, no documents — and watch
it confidently make up answers about a company it has never heard of. This is the
"RAG is dead" strawman that everyone loves to dunk on. We're going to earn the right
to fix it by first seeing it fail.

**Time:** ~12 minutes

> UI labels in the Microsoft Foundry portal shift from time to time. If a button
> isn't named exactly as written below, look for the closest equivalent — the flow
> is the same.

---

## Step 1 — Sign in and create a project

1. Go to **[ai.azure.com](https://ai.azure.com)** and sign in.
2. Create a new **project** (accept the defaults if prompted to create a resource or
   hub to go with it). Give it a name like `rag-is-dead-lab`.

## Step 2 — Deploy a model

1. Open the **Model catalog**.
2. Find and select **`gpt-4o-mini`**.
3. Click **Deploy**, choose the **Global Standard** deployment type, and confirm.
   Keep the default deployment name.

We use `gpt-4o-mini` because it's cheap, fast, and more than good enough for this —
the point of the lab isn't the model, it's what we feed it.

## Step 3 — Open the chat playground with NO data

1. In the left pane, open **Playgrounds → Chat**.
2. Select your `gpt-4o-mini` deployment.
3. **Do not attach any data.** Leave the system prompt at its default (or something
   generic like *"You are a helpful assistant."*).

This is the bare model — no documents, no grounding, nothing but its training.

## Step 4 — Ask the trap questions

Ask each of the five questions from
[`03-trap-questions.md`](03-trap-questions.md), one at a time. For example:

> How many paid vacation days do Summit Gear employees get?

Watch what happens. The model has never heard of Summit Gear Co. (it's fictional),
so it does what ungrounded models do: it **guesses, confidently.** You'll get a
plausible-sounding vacation policy, an invented headlamp battery life, and — most
tellingly — a completely fabricated parental leave policy.

## Step 5 — Note the failures

As a group, call out *how* it failed on each question:

- Did it make up a specific number?
- Did it sound confident while being wrong?
- Did it ever say "I don't know"? (It won't.)
- Did it invent facts that don't exist anywhere?

Keep these in mind. In Act 2 we ask the **exact same questions** and watch every one
of these failures disappear.

---

**This is the version people mean when they say "RAG is dead."** They're right that
it's broken. They're wrong that the fix is to give up on retrieval. On to Act 2.

➡️ Continue to [`02-act2-the-grounded-agent.md`](02-act2-the-grounded-agent.md)
