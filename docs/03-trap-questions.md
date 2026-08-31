# The Trap Questions

These are the questions you'll ask in **both** acts. The whole lab hinges on asking
the *same* questions twice — once to the ungrounded model (Act 1) and once to the
grounded agent (Act 2) — and watching the answers change.

Ask them exactly as written. Each one is designed to expose a specific failure of
ungrounded retrieval.

---

### Q1 — The guessable-but-wrong fact

> **How many paid vacation days do Summit Gear employees get?**

- **Act 1 (ungrounded):** The model invents a "typical" number like 15 or 20 days.
  It sounds confident and reasonable — and it's wrong.
- **Act 2 (grounded):** *22 days of PTO per year, plus your birthday off*, cited from
  the employee handbook.
- **Why it matters:** The most dangerous hallucinations are the plausible ones. No
  one double-checks an answer that sounds right.

---

### Q2 — The specific number

> **How long does the Summit X200 headlamp battery last on low mode?**

- **Act 1 (ungrounded):** The model makes up a figure — "around 20 hours" or similar.
  It has no way to know the real number.
- **Act 2 (grounded):** *47 hours on low*, cited from the product spec sheet.
- **Why it matters:** Specifics — prices, specs, dates — are where ungrounded models
  fail hardest and where being wrong costs the most.

---

### Q3 — The conflict

> **How many days per week can I work remotely?**

- **Act 1 (ungrounded):** The model guesses a generic hybrid-work answer.
- **Act 2 (grounded):** The strongest answer surfaces *3 days per week*, from the
  March 2026 memo, ideally noting that it supersedes the handbook's older "2 days."
- **Why it matters:** Real knowledge bases contradict themselves. Grounding isn't
  just about finding *an* answer — it's about finding the *right* source. This is a
  great moment to discuss recency, source priority, and why citations matter.

---

### Q4 — The gap (the refusal test)

> **What is Summit Gear's parental leave policy?**

- **Act 1 (ungrounded):** The model confidently fabricates a full policy —
  weeks of leave, eligibility, the works. All invented.
- **Act 2 (grounded):** The agent should say it **can't find** a parental leave
  policy in the provided documents. This "I don't know" is the single most important
  behavior in the whole lab.
- **Why it matters:** A grounded system that knows the limits of its knowledge is
  worth more than a clever one that always answers. Refusal is a feature.

---

### Q5 — The false premise (bonus)

> **Which of Summit Gear's three offices is dog-friendly?**

- **Act 1 (ungrounded):** The model plays along with the false premise and may invent
  a third office.
- **Act 2 (grounded):** The agent should correct the premise — Summit Gear has *two*
  offices (Boulder and Portland) — and note that *Boulder* is the dog-friendly one.
- **Why it matters:** Good grounding pushes back on wrong assumptions instead of
  agreeing with them.

---

## Running the comparison

Keep a simple scorecard on screen as you go. For each question, mark whether the
answer was **grounded**, **cited**, and **correct**:

| Question | Act 1: ungrounded | Act 2: grounded agent |
|----------|-------------------|------------------------|
| Q1 PTO | Wrong, confident | Correct + cited |
| Q2 headlamp | Made up | Correct + cited |
| Q3 remote days | Generic guess | Correct source + cited |
| Q4 parental leave | Fabricated | "Not in the documents" |
| Q5 offices | Played along | Corrected the premise |

By the time the table is full, the room has answered the session's question for
themselves: naive retrieval is dead; grounded retrieval is very much alive.
