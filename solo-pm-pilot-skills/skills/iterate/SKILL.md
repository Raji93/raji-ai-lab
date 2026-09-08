---
name: iterate
description: Take what you built through the loop that makes it real — refine it from feedback, define the evidence needed to trust it (evals and a golden dataset for AI; acceptance criteria, usability testing, or an A/B test otherwise), run the checks against pass bars, then turn the result into a clear path forward - ship, pause, hand off to engineering with a PRD-ready spec, or buy instead — and capture what you learned for the next cycle. Use whenever a PM has something working and needs to improve it, prove it, or prepare an engineering-ready handoff. Triggers include "iterate on this", "we got feedback", "how do I know it's good enough", "define evals", "build a golden dataset", "run an experiment", "what's needed to ship", "should we pause this", "hand off to engineering", "write the PRD", "productionize this", "should we build or buy", "what did we learn". This is step 3 of Scope -> Build -> Iterate.
---

# Iterate — Refine, prove, and ship (or pause, hand off, buy)

The loop that turns a rough thing into something you can trust. **Move through the phases in order** — you don't ship on a vibe.

## Core objective
- Turn feedback into concrete improvements.
- Define how you will know it is good enough **before** you measure it.
- Create the evidence needed for a real decision: evals for AI, acceptance criteria for product changes, a test plan for process changes.
- Produce a handoff that can be picked up without extra interpretation.
- Capture what you learned so the next cycle starts warm.

## When to use / when not to
- **Use** once something exists and you're improving it, proving it, or preparing it for delivery.
- **Don't use** to frame the problem (`scope`) or to build the first version (`build`).

## Input — what this needs
Ideally the **handoff block from `build`**. Read these first and carry them through:
- `proof_goal` — the assumption under test. This is what you're deciding about.
- `success_signal` / `kill_signal` — the bars set *before* anyone saw the artifact. **Do not move them now.**
- `fakes_or_stubs` — every faked part becomes a readiness gap or a scaling task.
- `scaling_plan` — the starting point for the ship/hand-off decision.

If there's no block, reconstruct the equivalent before proceeding, plus the feedback and context (who it's for, data sensitivity, scale, who'd own it).

## Before you generate: confirm the format
Ask the user one quick question — which format they want for the output:

- **Markdown / in-chat** — fastest to read and edit; good while still running checks and refining.
- **HTML one-pager** — a clean, styled, shareable artifact; best for the proof summary or an engineering handoff.

Ask once and wait. Skip only if they already stated a preference. **Keep the four-section proof block and the PRD as monospace / code blocks** — they're meant to be copied and re-run, so field names and structure stay intact.

## Required output shape — the proof block
Always produce this structure first, in both formats:

```text
# 1) What changed
summary:
feedback_cluster:
priority_changes:
deferred_items:

# 2) What "good enough" means
success_metrics:
pass_bars:              # minimum acceptable + stretch, set BEFORE measuring
failure_modes:

# 3) How we will prove it
test_method:
evals:                  # AI only — else n/a
golden_dataset:         # AI only — else the equivalent evidence set
sample_size:
regression_set:
proof_result:           # what actually happened: did each bar clear? state the numbers

# 4) What happens next
decision:               # ship | pause | hand off | buy | back to scope
next_steps:
owner:                  # named person. "Nobody" is a Blocker.
risks:
learnings:              # what we now know — true whatever the decision
revisit_trigger:        # if paused: the date or condition that reopens it
monitoring_plan:        # what to sample once live, and the drift signal
handoff_prd_path:       # if handing off
```

Then add supporting detail: rationale for each change · what is proven versus still uncertain · what should ship now versus later · what should be built, bought, or handed off.

### If Markdown: restraint rules
- **No emoji** in headers or body.
- **Ration bold** to the one load-bearing phrase per section.
- Keep the proof block and the PRD as fenced code blocks so structure survives a copy-paste.
- Beyond those, at most one table (usually the eval results). Everything else is prose.

### If HTML: emit this template inline
Generate the output using the exact template below. Fill the `{{PLACEHOLDERS}}`, delete unused sections, and **do not change the CSS**. The proof block renders in the monospace panel, eval results in the light table, and the decision is the one emphasized callout. Include the PRD section only in Full mode. Emit the filled-in HTML as a `.html` artifact.

```html
<!DOCTYPE html>
<!--
  ITERATE — PROOF & HANDOFF TEMPLATE
  The iterate skill fills the {{PLACEHOLDERS}} and removes optional sections.
  Do NOT edit the CSS. Include the PRD section only in Full mode.
-->
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Iterate — {{ARTIFACT_NAME}}</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Newsreader:ital,opsz,wght@0,6..72,400;0,6..72,500;0,6..72,600&family=Inter:wght@400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --paper:#FBFBFA; --ink:#1C1B1A; --muted:#726F69; --faint:#9A968E;
    --rule:#E7E4DC; --accent:#2F5D50; --accent-soft:#EAF0ED;
    --warn:#9A3B25; --warn-soft:#F6ECE8; --panel:#F3F2ED;
    --pass:#2F5D50; --fail:#9A3B25; --maxw:720px;
  }
  *{box-sizing:border-box;}
  html{-webkit-text-size-adjust:100%;}
  body{margin:0;background:var(--paper);color:var(--ink);
    font-family:"Inter",-apple-system,BlinkMacSystemFont,sans-serif;
    font-size:16px;line-height:1.62;-webkit-font-smoothing:antialiased;}
  .wrap{max-width:var(--maxw);margin:0 auto;padding:72px 28px 96px;}
  .eyebrow{font-size:12px;letter-spacing:.16em;text-transform:uppercase;color:var(--accent);font-weight:600;margin:0 0 14px;}
  h1{font-family:"Newsreader",Georgia,serif;font-weight:500;font-size:clamp(32px,5.5vw,44px);line-height:1.08;letter-spacing:-.01em;margin:0 0 20px;}
  .lede{font-family:"Newsreader",Georgia,serif;font-size:clamp(19px,2.6vw,22px);line-height:1.5;color:#33322F;font-weight:400;margin:0;}
  .lede strong{font-weight:600;color:var(--ink);}
  section{margin-top:48px;}
  .label{font-size:12px;letter-spacing:.14em;text-transform:uppercase;color:var(--accent);font-weight:600;margin:0 0 16px;padding-bottom:9px;border-bottom:1px solid var(--rule);}
  h3{font-size:15px;font-weight:600;margin:22px 0 4px;}
  p{margin:0 0 14px;} p:last-child{margin-bottom:0;} .muted{color:var(--muted);}
  ul.clean{margin:0;padding:0;list-style:none;}
  ul.clean li{padding:11px 0;border-top:1px solid var(--rule);} ul.clean li:first-child{border-top:none;} ul.clean li b{font-weight:600;}
  .panel{background:var(--panel);border:1px solid var(--rule);border-radius:10px;padding:20px 22px;
    font-family:"JetBrains Mono",ui-monospace,monospace;font-size:13px;line-height:1.7;color:#2A2925;overflow-x:auto;white-space:pre-wrap;}
  table{width:100%;border-collapse:collapse;font-size:14.5px;margin-top:4px;}
  th{text-align:left;font-weight:600;font-size:11px;letter-spacing:.1em;text-transform:uppercase;color:var(--faint);padding:0 14px 10px 0;border-bottom:1px solid var(--rule);}
  td{padding:12px 14px 12px 0;border-bottom:1px solid var(--rule);vertical-align:top;}
  tr td:last-child,tr th:last-child{padding-right:0;}
  .pass{color:var(--pass);font-weight:600;} .fail{color:var(--fail);font-weight:600;}
  .callout{background:var(--accent-soft);border:1px solid #CFDDD8;border-radius:12px;padding:22px 26px;margin-top:16px;}
  .callout.stop{background:var(--warn-soft);border-color:#E4CDC5;}
  .callout .label{border:none;padding:0;margin-bottom:8px;} .callout.stop .label{color:var(--warn);}
  .callout p{margin:0;font-size:16px;} .callout p + p{margin-top:10px;} .callout b{font-weight:600;}
  hr.soft{border:none;border-top:1px solid var(--rule);margin:52px 0 0;}
  @media (max-width:560px){.wrap{padding:48px 20px 72px;}}
</style>
</head>
<body>
<div class="wrap">

  <p class="eyebrow">Iterate — Proof &amp; Handoff</p>
  <h1>{{ARTIFACT_NAME}}</h1>
  <p class="lede">Deciding whether <strong>{{PROOF_GOAL}}</strong> clears the bar.</p>

  <section>
    <p class="label">1 · What changed</p>
    <p>{{SUMMARY}}</p>
    <h3>Priority changes</h3>
    <ul class="clean">
      <li>{{CHANGE}}</li>
    </ul>
    <p class="muted" style="margin-top:12px;"><b>Deferred:</b> {{DEFERRED}}</p>
  </section>

  <section>
    <p class="label">2 · What "good enough" means</p>
    <p class="muted">Bars set before measuring — not moved after.</p>
    <ul class="clean">
      <li><b>Minimum acceptable:</b> {{MIN_BAR}}</li>
      <li><b>Stretch:</b> {{STRETCH_BAR}}</li>
    </ul>
  </section>

  <section>
    <p class="label">3 · How we proved it</p>
    <p><b>Method:</b> {{TEST_METHOD}} &nbsp;·&nbsp; <b>Evidence set:</b> {{GOLDEN_DATASET_or_equivalent}} ({{SAMPLE_SIZE}})</p>
    <table>
      <thead><tr><th>Check</th><th>Bar</th><th>Result</th><th>Verdict</th></tr></thead>
      <tbody>
        <!-- repeat one row per eval / acceptance check -->
        <tr><td>{{CHECK}}</td><td>{{BAR}}</td><td>{{RESULT}}</td><td class="pass">Pass</td></tr>
        <tr><td>{{CHECK}}</td><td>{{BAR}}</td><td>{{RESULT}}</td><td class="fail">Fail</td></tr>
      </tbody>
    </table>
  </section>

  <!-- Decision callout: use class="stop" for pause / back-to-scope -->
  <div class="callout">
    <p class="label">Decision — {{DECISION_ship_pause_handoff_buy}}</p>
    <p><b>{{DECISION_one_line}}</b></p>
    <p class="muted">Owner: {{OWNER}}. {{REVISIT_or_launch_note}}</p>
  </div>

  <section>
    <p class="label">4 · What we learned</p>
    <ul class="clean">
      <li><b>Learned:</b> {{LEARNING}}</li>
      <li><b>Changed our mind:</b> {{WHAT_MOVED_US}}</li>
      <li><b>Reusable:</b> {{REUSABLE_ASSET}}</li>
      <li><b>Re-scope next:</b> {{NEXT_QUESTION}}</li>
    </ul>
  </section>

  <!-- ===== FULL MODE ONLY: Engineering handoff PRD ===== -->
  <hr class="soft">
  <section>
    <p class="label">Engineering handoff PRD</p>
    <div class="panel">## Problem
{{PRD_PROBLEM}}

## Goal &amp; success metrics
{{PRD_GOAL}}

## Scope
In scope:    {{PRD_IN}}
Out of scope:{{PRD_OUT}}
Non-goals:   {{PRD_NONGOALS}}

## Requirements
{{PRD_REQUIREMENTS}}

## Acceptance criteria  (pass bars are non-negotiable)
{{PRD_ACCEPTANCE}}

## Edge cases &amp; failure handling
{{PRD_EDGES}}

## Data, security &amp; governance
{{PRD_DATA_SECURITY}}

## Dependencies &amp; assumptions
{{PRD_DEPENDENCIES}}

## Rollout / launch criteria
{{PRD_ROLLOUT}}

## Open questions
{{PRD_OPEN}}</div>
    <p class="muted" style="margin-top:14px;">Attached: evidence set + results, so the receiver can re-run the checks rather than take your word for it.</p>
  </section>

</div>
</body>
</html>
```


## Modes
- **Compact** (small change, low stakes): the four-section block plus three bullets of reasoning. Skip the PRD.
- **Full** (higher stakes, or handing to engineering): the block, the supporting detail, and the **Engineering handoff PRD** below.

## Phase 1 · Refine from feedback
Cluster feedback into concrete change requests, sort by **impact × effort**, implement or recommend the highest-impact / lowest-effort changes first, and explicitly note what is deferred. Re-check each change against the **guardrail metric** from `scope`.

## Phase 2 · Define "good enough"
Set the pass bars before you measure. Tie each behavior to a metric and define how it will be tested.
- **Any change:** acceptance criteria · usability testing · A/B tests or before/after tests with a defined sample size · QA cases for edge conditions.
- **If AI is involved, also:** evals for correctness, **groundedness / no-hallucination**, correct escalation or abstention, tone, safety, latency, and cost.
- Define a **minimum acceptable bar** and a **stretch bar**.
- Carry `success_signal` / `kill_signal` forward from `build` as the bars. **Moving a bar after seeing the result invalidates the test** — if you must, say so out loud and explain why.

## Phase 3 · Build the evidence set
- **If AI:** create a **golden dataset** with real examples labeled with expected answers, synthetic cases for coverage, and **adversarial / edge** cases (ambiguous, out-of-scope, unsafe). Start with ~50–200 examples, keep a **held-out set** you never tune against, and **version it**.
- **If not AI:** create the equivalent evidence set — a test-case list, usability script, historical backtest (leakage-safe: only data available at the decision moment), or QA checklist. Same principles: cover the edges, keep something held back, version it.
- Keep a **regression set** so a fix can't silently break a past win.

## Phase 4 · Run the checks
Choose the cheapest trustworthy method:
- **Programmatic** checks for exact matches, schema, thresholds, funnel math, and deterministic behavior.
- **Rubrics or LLM-as-judge** for quality, groundedness, and nuanced review.
- **Human review** for highest-stakes, edge-case, or customer-visible decisions.

Score against the pass bars and **record the result in `proof_result`** — the numbers, not an impression. Once live, sample real usage, watch for drift, and route low-confidence or high-risk cases to a human.

## Next steps and decision
Make the path forward explicit:
- Flag each item **Ready / Gap / Blocker** for security, privacy, compliance, governance, access control, support, reliability, and ownership. **A Blocker on security, data, or compliance stops a self-ship.**
- Weigh **blast radius · data sensitivity · integration depth · compliance/SLA · maintenance burden · team model**, then recommend with reasoning:
  - **Ship** — the minimum still required (security review, monitoring, data handling, named owner, kill switch) and the tripwires that force a later hand-off.
  - **Pause** — a legitimate outcome, not a failure. Record what you learned, **what to preserve** (the artifact, the evidence set, the findings note), **who owns it dormant**, and the **revisit trigger** — a date or condition ("when the SSO project lands"). *A pause without a trigger is a quiet death.*
  - **Hand off** — produce the Engineering handoff PRD below.
  - **Buy** — use your evidence set as the vendor bake-off yardstick; your pass bars turn a demo into a fair test on your own data.
  - **Back to scope** — if the result showed the problem, metric, or approach was wrong. That's a finding, not a failure.
- Name the accountable owner and the next milestone.

## Learn & improve — close the loop
Every cycle produces a finding, whatever the decision. Before you finish, write down:
- **What we learned** — about the user, the problem, or our own assumptions.
- **What changed our mind** — the specific result that moved you, so the reasoning survives.
- **What's reusable** — the evidence set, the query, the taxonomy, the component, the template.
- **What to re-scope next** — the sharper question this cycle exposed.

Hand that back to **`scope`** so the next loop starts warm instead of cold.

## Engineering handoff PRD
If the output is intended for engineering, produce a compact PRD-ready handoff with:
- **Problem statement**
- **User / problem context**
- **Desired outcome and success metrics**
- **Scope**: in scope / out of scope / non-goals
- **Functional requirements**
- **Acceptance criteria** — including the pass bars as **non-negotiables**
- **Edge cases and failure handling**
- **Data, security, and governance requirements**
- **Dependencies and assumptions**
- **Rollout plan / launch criteria**
- **Open questions and next actions**

Attach the **evidence set and results** — the receiver should be able to re-run your checks, not take your word for it.

### Handoff template
```text
## Engineering handoff PRD
### Problem
...

### Goal
...

### Success metrics
...

### Scope
In scope:
Out of scope:
Non-goals:

### Requirements
...

### Acceptance criteria
(pass bars are non-negotiable)
...

### Risks / dependencies
...

### Data & security
...

### Launch plan
...

### Open questions
...
```

## Guardrails
- Every check should map to a metric.
- Every test should cover edge and failure cases.
- Keep something held out to avoid overfitting.
- **Never move a pass bar after seeing the result** without saying so explicitly.
- Never ship sensitive or regulated data without review.
- Always name an owner.
- Keep a human in the loop for high-stakes or customer-facing output until the evidence says otherwise.
- **Pause and stop are real answers.** A loop that can only conclude "ship" isn't a decision process.

## Solo-PM check
- **Timebox** — how long will proving this take, and is that proportionate to the decision?
- **Solo-doable vs. needs someone** — you can run 5 usability sessions alone; you can't grant yourself security sign-off. Start those early.
- **Your red-teamer** — who checks your read of the results before you commit? Confirmation bias is strongest at exactly this step.
- **Leaves behind** — the evidence set and the findings note are the assets. Save them where the next cycle can find them.

## Ready to close the loop?
- [ ] Were the pass bars set before measuring — and left alone?
- [ ] Is `proof_result` filled with numbers, not impressions?
- [ ] Does the decision follow from the result, not from the effort already spent?
- [ ] Is there a named owner, and for a pause, a revisit trigger?
- [ ] Are the learnings written down for the next cycle?
- [ ] If handing off, does the receiver get the evidence set and the non-negotiables?

## Handoff
Ship, pause, hand off, or buy — then return the learnings to **`scope`** and start the next loop. If the results show the problem, metric, or approach was wrong, go back to **`scope`** directly.
