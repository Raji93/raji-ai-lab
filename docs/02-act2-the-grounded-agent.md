# Act 2 — The Version That Isn't (Dead)

**Goal:** Give the same model the company's actual documents, turn on grounding with
a strict instruction, and re-ask the exact same questions. Watch confident nonsense
turn into correct, cited, honest answers.

**Time:** ~20 minutes

> We use the **Agent** with the **File Search** tool on **basic setup**. This is the
> important choice: basic setup uses a **Microsoft-managed** document store, so you
> do **not** have to create (or pay for) a separate Azure AI Search resource. Your
> per-person store is tiny and auto-expires.

---

## Step 1 — Create an agent

1. In the Microsoft Foundry portal, open the **Agents** section.
2. Create a **new agent**.
3. Select your **`gpt-4o-mini`** deployment as its model.

## Step 2 — Add your documents as knowledge

1. In the agent's **Setup** pane on the right, scroll to **Knowledge**.
2. Select **Add**, then choose **Files**.
3. Upload the three sample documents from the [`sample-docs/`](../sample-docs/)
   folder:
   - `employee-handbook.md`
   - `product-spec-sheet.md`
   - `remote-work-memo.md`
4. Follow the prompts to finish adding the **File Search** tool. Choosing the basic
   file upload option creates the managed vector store for you.

**Wait for ingestion to finish.** The files need to be fully processed (chunked and
embedded) before the agent can search them. If you ask a question too early, the
answer won't be grounded yet — give it a moment until the files show as ready.

## Step 3 — Set the grounding instructions

This is the single most important step in the lab. Paste the grounding prompt from
[`grounding-prompt.md`](grounding-prompt.md) into the agent's **Instructions** (system
prompt) field.

The short version of what it does: it tells the agent to answer **only** from the
uploaded files, to **cite** the file each answer came from, and to say **"I don't
know"** when the documents don't contain the answer. Grounding is what turns a
guessing machine into a retrieval system.

## Step 4 — Re-ask the exact same questions

Open the agent's chat and ask the **same five questions** from
[`03-trap-questions.md`](03-trap-questions.md), word for word. This time:

- **Q1 (PTO):** returns *22 days plus your birthday off*, cited from the handbook.
- **Q2 (headlamp):** returns *47 hours on low*, cited from the spec sheet.
- **Q3 (remote days):** surfaces *3 days per week* from the March 2026 memo — the
  newer source.
- **Q4 (parental leave):** says it **can't find** a parental leave policy in the
  documents instead of inventing one.
- **Q5 (offices):** corrects the premise — there are **two** offices, and Boulder is
  the dog-friendly one.

## Step 5 — Fill in the scorecard

Complete the comparison table from [`03-trap-questions.md`](03-trap-questions.md).
Every failure from Act 1 should now be a grounded, cited, correct answer — or an
honest "I don't know."

---

## Optional stretch — a taste of *agentic* retrieval

If you have time and want to show where retrieval is heading, add a **second tool**
to the agent — for example, the **web search** tool — alongside File Search. Now the
agent has to *decide* which source to use for a given question: the internal docs for
company facts, the web for anything current. That "decide what to fetch, when" loop
is the essence of **agentic retrieval** — the direction serious retrieval work is
moving in 2026, and a world away from the naive pipeline in Act 1.

---

## The verdict

You just built both sides of the argument. Naive, ungrounded retrieval **is** dead —
it hallucinates, invents specifics, and never admits ignorance. But grounded,
cited, source-aware retrieval? That's not dead. It's the version worth building.

➡️ Wrap up with [`04-cost-and-teardown.md`](04-cost-and-teardown.md) so you don't
leave anything running.
