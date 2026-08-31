# Cost & Teardown

This lab is designed to be **near-free** — cents per person at most — but only if you
follow a couple of rules and clean up at the end. Here's how to keep it that way.

## Why it's cheap

- **Small model.** `gpt-4o-mini` costs a tiny fraction of larger models, and a
  60-minute lab uses a trivial number of tokens.
- **No standalone search service.** By using the agent's **File Search on basic
  setup**, you rely on a **Microsoft-managed** document store instead of provisioning
  your own Azure AI Search resource — which is the single most expensive thing you
  could accidentally spin up. Don't use the chat playground's "add your own data"
  flow, which asks you to connect that paid search resource.
- **Tiny, auto-expiring store.** Your uploaded documents are only a few pages, so the
  managed vector store is small, and its size is what you're billed on. Vector stores
  support **expiration policies** so they clean themselves up.

## Set an expiration policy (optional but tidy)

When you create the file store, if the option is offered, set an **expiration policy**
so the store is automatically deleted after a short window (for example, 1 day). This
means even if you forget to clean up, the storage cost stops on its own.

## Teardown checklist (do this at the end)

Delete resources in this order so nothing keeps billing:

1. **Delete the agent** you created.
2. **Delete the uploaded files / vector store** (if not already handled by an
   expiration policy).
3. **Delete the model deployment**, or the whole **project**, if you don't plan to
   reuse it.
4. If you created a dedicated **resource group** for this lab, delete the resource
   group — that removes everything under it in one action and is the surest way to
   avoid a surprise charge.

## For facilitators running a full room

- Have every attendee create their **own** project, agent, and store. There's no
  shared bottleneck, and each person's cost is negligible.
- Remind people to run the teardown checklist before they leave. Put it on your last
  slide.
- If you obtained **Azure Pass** codes or a sponsored environment for the room, those
  absorb the cost entirely — worth asking your Microsoft contact about ahead of time.

> If you used the **GitHub Models** fallback instead of Azure, there's nothing to tear
> down — it's free-tier and has no resources to delete.
