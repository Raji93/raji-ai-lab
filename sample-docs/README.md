# Sample Documents

These three documents describe **Summit Gear Co.**, a fictional outdoor-equipment
company. They are the knowledge base your agent will use in Act 2 of the lab.

| File | What it contains |
|------|------------------|
| `employee-handbook.md` | Company policies — offices, hours, remote work, PTO, expenses |
| `product-spec-sheet.md` | Two products with specific specs — the Summit X200 headlamp and Trailblazer 45L backpack |
| `remote-work-memo.md` | A newer memo that **updates** the handbook's remote-work rule |

## Why a fictional company?

The whole point of this lab is to show the difference between a model *guessing*
and a model *retrieving*. That only works if the documents contain facts the model
could not possibly know from training. A made-up company with made-up policies and
product specs gives us clean "gotcha" moments.

## The traps (facilitator note)

These documents are designed with four deliberate traps that expose the difference
between the ungrounded model (Act 1) and the grounded agent (Act 2):

1. **The guessable-but-wrong fact.** PTO is *22 days plus your birthday off* — an
   unusual number the model will not guess correctly.
2. **The specific number.** The Summit X200 headlamp runs *47 hours* on low. The
   ungrounded model will invent a plausible-sounding figure.
3. **The conflict.** The handbook says 2 remote days; the memo says 3. A good
   grounded answer should surface the memo (the newer source) and ideally note the
   conflict.
4. **The gap.** Nothing here mentions **parental leave**. The ungrounded model will
   confidently make up a policy; the grounded agent should say it can't find one.

There's also a **false-premise** trap: Summit Gear has only *two* offices, so a
question about "all three offices" should be corrected, not answered.

See `../docs/03-trap-questions.md` for the exact questions and expected answers.

## Want to make it your own?

Swap in your own company, policies, and products — just keep the four trap types
above and the lab still works. Keep the total under ~20 pages so ingestion is fast
during a live session.
