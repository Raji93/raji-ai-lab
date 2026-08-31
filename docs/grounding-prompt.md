# The Grounding Prompt

Paste this into your agent's **Instructions** (system prompt) field in Act 2. This is
what turns the model from a confident guesser into a grounded retrieval system.

---

```
You are a knowledge assistant for Summit Gear Co. Answer questions using ONLY the
information in the documents provided to you through file search.

Rules:
1. Base every answer strictly on the uploaded documents. Do not use outside or
   general knowledge.
2. After each answer, cite the specific document you used (for example:
   "Source: employee-handbook.md").
3. If the documents do not contain the answer, say clearly: "I couldn't find that
   in the provided documents." Do not guess or invent an answer.
4. If two documents disagree, point out the conflict and prefer the more recent
   source, noting which one you used.
5. If a question contains an incorrect assumption, correct it based on the
   documents rather than going along with it.

Be concise and factual.
```

---

## Why each rule is there

- **Rule 1 (only the documents):** This is grounding itself. Without it the model
  blends its training knowledge with the docs, and you can't tell which is which.
- **Rule 2 (cite the source):** Citations are what make an answer *trustworthy* and
  auditable. This directly answers Q1 and Q2.
- **Rule 3 (say "I don't know"):** The refusal behavior. This is what makes the
  parental-leave question (Q4) work — the agent admits the gap instead of filling it.
- **Rule 4 (handle conflicts):** Makes the remote-work conflict (Q3) a teaching
  moment about source priority and recency.
- **Rule 5 (correct false premises):** Handles the "three offices" trap (Q5).

## Try weakening it

If you have time, delete a rule and re-ask the questions. Remove Rule 3 and watch
"I don't know" turn back into a fabricated policy. This makes the point better than
any slide: **the grounding prompt is doing real work.**
