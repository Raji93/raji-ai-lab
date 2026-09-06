# The Questions

Ask these in **both** acts and open the trace each time.
The point is to watch *how* each system goes about answering.

---

## Warm-up — one document, one source

**Q1.**

```text
What's our PTO policy?
```

Lives entirely in the handbook (HR source). Both acts answer it well.

**Q2.**

```text
How long does the Summit X200 headlamp battery last on low?
```

Lives in the spec sheet (Product source). Again, both handle it. In Act 2, notice the
retrieval draws from the Product source — the knowledge layer knew where to look.

---

## Cross-document — two files, same source

**Q3.**

```text
How many days a week can I work remotely?
```

The handbook says 2 days; the March 2026 memo says 3.
A good answer surfaces **3** and notes the memo supersedes the handbook.
Both acts usually get this right — the interesting part is seeing *both files* appear in the retrieved chunks.

**Q4.**

```text
What was our remote-work policy before, and what changed?
```

Same two documents, but now the question explicitly requires both.
Watch whether the retrieved chunks include the handbook's original rule *and* the memo, or just one.

---

## Cross-source — HR **and** Product

These are the ones that need both knowledge sources. They're the heart of the
comparison.

**Q5.**

```text
Which product should a new employee buy with their gear allowance, and how much would be left over?
```

Needs the $500 allowance (HR) plus both prices, $89 and $210 (Product), plus
arithmetic.

**Q6.**

```text
I want to buy the Trailblazer 45L. Do I need pre-approval to expense it, and can I use my gear allowance instead?
```

Deliberately tricky: the price is in the Product source; the $75 pre-approval threshold and the gear allowance are both in HR — and they govern different things.

**Q7.**

```text
What's the warranty on the more expensive of our two products?
```

A small chain: find which product costs more (Product source), then find its warranty (also Product source). Tests whether the system can follow a two-step question rather than matching keywords.

---

## What to record

For each question, note from the trace:

| | Act 1 | Act 2 |
|---|---|---|
| Tool called | `file_search` | `knowledge_base_retrieve` (+ `mcp_list_tools`) |
| How many retrieval nodes | | |
| Which files appear in the chunks | | |
| Citation granularity | file name | per-chunk source IDs |
| Answer complete and correct? | | |
