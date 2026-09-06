# Cost & Teardown

This lab is designed to be cheap, but Act 2 costs more than Act 1 — worth understanding
before you build, and worth cleaning up after.

## What costs what

- **The model.** `gpt-4o-mini` is inexpensive and a 60-minute lab uses a trivial number
  of tokens. Negligible.
- **Act 1 — File Search on basic setup.** Uses a Microsoft-managed store, billed on the
  size of your (tiny) document set. Cents.
- **Act 2 — Foundry IQ.** This is the real cost. Foundry IQ is built on Azure AI Search
  knowledge bases, so **you need an Azure AI Search service**, and the knowledge base
  and its sources must live on the same search service. Search services bill hourly
  while they exist, not per query.

> **Use the free or lowest tier of Azure AI Search for this lab**, and **delete it when
> you're done**. A Standard-tier search service left running is by far the most
> expensive mistake available here.

- **Query planning.** At medium retrieval reasoning effort the engine uses an LLM to
  plan queries, which adds a small number of tokens per question. Minor, but it's why
  Act 2 is slower and pricier per answer than Act 1 — a fair trade-off to mention out
  loud.

## Set an expiration policy

Where offered, set an **expiration policy** on file stores so they clean themselves up
even if someone forgets the teardown steps.

## Teardown checklist

Do these in order at the end of the session:

1. Delete the **Act 2 agent** and the **Act 1 agent**.
2. Delete the **knowledge base** and its **knowledge sources**.
3. **Delete the Azure AI Search service.** ← the one that keeps billing if you forget.
4. Delete the **model deployment**.
5. Delete the **project**, or the whole **resource group** if you made one for this lab.
   Deleting the resource group removes everything in one action and is the safest
   option.

## For facilitators running a full room

- Each attendee creates their own project, search service, and knowledge base, so
  there's no shared bottleneck — but that also means **every attendee has a search
  service to delete.** Put teardown on your final slide and give it two full minutes.
- Ask attendees to use the **free tier** of Azure AI Search where available.
- If you can get **Azure Pass** codes or a sponsored environment from your Microsoft
  contact, that absorbs the cost entirely and removes the billing anxiety from the room.
- Send the teardown checklist in your follow-up email too — people leave in a hurry.
