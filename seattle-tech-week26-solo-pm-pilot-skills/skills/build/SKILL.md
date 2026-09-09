---
name: build
description: Turn a scoped plan into the smallest real artifact that tests its core assumption — a fake door, a Wizard-of-Oz trial, a clickable flow, a thin working prototype, a spreadsheet model, or a doc. Produces a structured handoff block (artifact type, the assumption being tested, the success and kill signals, tool stack, what's faked, how it scales) plus a runnable artifact. Covers platform-agnostic tool selection across open-source, Anthropic, OpenAI, Google, Microsoft, and app builders like v0, Lovable, and Replit; a no-engineering build path; and how a model integrates if AI is involved. Use whenever a PM needs to prototype, test an idea cheaply, choose tools, or make something concrete enough for people to react to. Triggers include "build a prototype", "how do I test this", "which tools should I use", "stand up a demo", "make an MVP", "prototype without engineers", "how would this scale". This is step 2 of Scope -> Build -> Iterate.
---

# Build — the smallest artifact that proves the assumption

**Build to learn quickly, not to impress.** The goal is not a polished product. The goal is something concrete enough that people can react to it — and a reaction you can read as signal.

## Core objective
- Identify the single assumption that matters most.
- Choose the smallest artifact that can test it.
- Prefer a low-fidelity prototype, mock, script, workflow, or lightweight page over a full implementation.
- Decide **before you build** what reaction would confirm the assumption, and what would kill it.

## When to use / when not to
- **Use** once the problem, metric, and riskiest assumption are reasonably clear (ideally from `scope`).
- **Don't use** to frame the problem (`scope`) or to refine and ship what you built (`iterate`).

## Input — what this needs
A scoped plan, or at minimum: the assumption to test, who it's for, the constraint (deadline, data sensitivity, existing stack).

**Ask before inventing.** If the assumption isn't clear, ask for it — building the wrong thing fast is still building the wrong thing. **Timebox it:** state up front how long this build should take (hours for a mock, days for a thin prototype). If the estimate exceeds the learning value, say so and shrink the artifact.

## Two outputs, one of them a document
`build` produces two things:
1. **The runnable artifact** — the prototype/mock/spreadsheet itself. If it's a UI, default to a single self-contained HTML file (see Visual bar).
2. **The build brief** — the handoff block plus reasoning, which is what `iterate` reads next. The format question below governs *this brief*, not the artifact.

## Before you generate the brief: confirm the format
Ask the user one quick question — which format they want for the build brief:

- **Markdown / in-chat** — fastest to read and edit; good while still choosing tools or shrinking scope.
- **HTML one-pager** — a clean, styled, shareable brief; best for a demo or handing to a stakeholder.

Ask once and wait. Skip only if they already stated a preference. Either way, **keep the handoff block itself as a monospace / code block** — it's meant to be copied straight into `iterate`, so its field names stay intact.

## Required output shape — the handoff block
Produce this block first, in both formats. **Core fields always; extended fields in Full mode.**

```
# core
artifact_type:      # fake door | wizard-of-oz | clickable | thin working thing | model/spreadsheet | doc
proof_goal:         # the ONE assumption this tests, stated so it could fail
success_signal:     # the reaction/result that confirms it (be specific: "3 of 5 users X")
kill_signal:        # the reaction that says stop or rethink
artifact_path:      # file path, or "n/a — manual/offline artifact"
tool_stack:         # tools chosen + the constraint that drove the choice
fakes_or_stubs:     # everything not real: data, integrations, auth, and the model itself
handoff_target:     # iterate | scope | ship

# extended (Full mode)
audience:           # who reacts to it, and how many
why_this_form:      # why this is the smallest useful version
scaling_plan:       # what changes if the signal is positive
effort:             # S / M / L, or hours–days
demo_steps:         # 3–5 beats, plus an offline fallback
```

Then add supporting notes — **reasoning, not a restatement of the block**:
- decision rationale (what you considered and rejected)
- failure modes and risks
- where a real engineer is genuinely needed (be honest; don't oversell no-code)
- a visual design note, if it's a UI artifact

### If Markdown: restraint rules
- **No emoji** in headers or body.
- **Ration bold** to the one load-bearing phrase per section.
- **At most two tables** beyond the handoff block — realistically the artifact-form table and the tool comparison. Everything else is prose.
- Keep the handoff block as a fenced code block so field names survive a copy-paste.

### If HTML: emit this template inline
Generate the brief using the exact template below. Fill the `{{PLACEHOLDERS}}`, delete unused sections, and **do not change the CSS**. The handoff block renders in the monospace panel; the tool comparison renders in the light table. Emit the filled-in HTML as a `.html` artifact. The runnable prototype stays a separate file.

```html
<!DOCTYPE html>
<!--
  BUILD BRIEF TEMPLATE
  The build skill fills the {{PLACEHOLDERS}} and removes optional sections.
  Do NOT edit the CSS. The runnable prototype is a SEPARATE file, not this brief.
-->
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Build Brief — {{ARTIFACT_NAME}}</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Newsreader:ital,opsz,wght@0,6..72,400;0,6..72,500;0,6..72,600&family=Inter:wght@400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --paper:#FBFBFA; --ink:#1C1B1A; --muted:#726F69; --faint:#9A968E;
    --rule:#E7E4DC; --accent:#2F5D50; --accent-soft:#EAF0ED;
    --warn:#9A3B25; --panel:#F3F2ED; --maxw:720px;
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
  p{margin:0 0 14px;} p:last-child{margin-bottom:0;}
  .muted{color:var(--muted);}
  /* monospace handoff panel */
  .panel{background:var(--panel);border:1px solid var(--rule);border-radius:10px;padding:20px 22px;
    font-family:"JetBrains Mono",ui-monospace,monospace;font-size:13px;line-height:1.7;color:#2A2925;overflow-x:auto;}
  .panel .k{color:var(--accent);} .panel .c{color:var(--faint);}
  table{width:100%;border-collapse:collapse;font-size:14.5px;margin-top:4px;}
  th{text-align:left;font-weight:600;font-size:11px;letter-spacing:.1em;text-transform:uppercase;color:var(--faint);padding:0 14px 10px 0;border-bottom:1px solid var(--rule);}
  td{padding:12px 14px 12px 0;border-bottom:1px solid var(--rule);vertical-align:top;}
  tr td:last-child,tr th:last-child{padding-right:0;} .cost{color:var(--muted);white-space:nowrap;}
  ul.clean{margin:0;padding:0;list-style:none;}
  ul.clean li{padding:11px 0;border-top:1px solid var(--rule);}
  ul.clean li:first-child{border-top:none;} ul.clean li b{font-weight:600;}
  ol.steps{margin:0;padding:0;counter-reset:s;list-style:none;}
  ol.steps li{padding:11px 0 11px 34px;border-top:1px solid var(--rule);position:relative;counter-increment:s;}
  ol.steps li:first-child{border-top:none;}
  ol.steps li::before{content:counter(s);position:absolute;left:0;top:11px;font-family:"Newsreader",serif;color:var(--faint);}
  .callout{background:var(--accent-soft);border:1px solid #CFDDD8;border-radius:12px;padding:20px 24px;margin-top:16px;}
  .callout .label{border:none;padding:0;margin-bottom:8px;} .callout p{margin:0;} .callout b{font-weight:600;}
  @media (max-width:560px){.wrap{padding:48px 20px 72px;}}
</style>
</head>
<body>
<div class="wrap">

  <p class="eyebrow">Build Brief</p>
  <h1>{{ARTIFACT_NAME}}</h1>
  <p class="lede">Testing one thing: <strong>{{PROOF_GOAL_one_sentence}}</strong></p>

  <section>
    <p class="label">Handoff block</p>
    <div class="panel"><span class="c"># core</span><br>
artifact_type:  {{ARTIFACT_TYPE}}<br>
proof_goal:     {{PROOF_GOAL}}<br>
success_signal: {{SUCCESS_SIGNAL}}<br>
kill_signal:    {{KILL_SIGNAL}}<br>
artifact_path:  {{ARTIFACT_PATH}}<br>
tool_stack:     {{TOOL_STACK}}<br>
fakes_or_stubs: {{FAKES_OR_STUBS}}<br>
handoff_target: {{HANDOFF_TARGET}}</div>
  </section>

  <section>
    <p class="label">Why this form</p>
    <p>{{WHY_THIS_FORM}}</p>
  </section>

  <section>
    <p class="label">Tool choice</p>
    <p>{{TOOL_RATIONALE_constraint_that_drove_it}}</p>
    <!-- OPTIONAL comparison table: include when the user weighs platforms -->
    <table>
      <thead><tr><th>Platform</th><th>What you'd build</th><th class="cost">Effort</th><th>Trade-off</th></tr></thead>
      <tbody>
        <!-- repeat one row per platform -->
        <tr><td>{{PLATFORM}}</td><td>{{WHAT}}</td><td class="cost">{{EFFORT}}</td><td>{{TRADEOFF}}</td></tr>
      </tbody>
    </table>
  </section>

  <section>
    <p class="label">What's faked</p>
    <ul class="clean">
      <!-- repeat one li per faked/stubbed part -->
      <li><b>{{FAKE_name}}</b> — {{FAKE_detail}}</li>
    </ul>
  </section>

  <section>
    <p class="label">Demo steps</p>
    <ol class="steps">
      <!-- 3–5 beats, plus an offline fallback -->
      <li>{{STEP}}</li>
    </ol>
  </section>

  <section>
    <p class="label">Decision rationale &amp; risks</p>
    <p>{{RATIONALE_what_you_considered_and_rejected}}</p>
    <p class="muted">{{RISKS_and_where_a_real_engineer_is_needed}}</p>
  </section>

  <div class="callout">
    <p class="label">Next</p>
    <p>Hand to <b>{{HANDOFF_TARGET}}</b> — {{NEXT_one_line}}</p>
  </div>

</div>
</body>
</html>
```


## Choosing the artifact form
Pick one and justify it in `why_this_form`:

| Form | Best when the question is | Typical cost |
|---|---|---|
| Fake door / landing test | does anyone want this at all? | hours |
| Wizard-of-Oz / manual trial | is the outcome valuable, before we automate it? | days |
| Clickable flow | is the flow understandable? | hours |
| Thin working thing | does the core mechanic actually work? | days |
| Model / spreadsheet | do the numbers hold up? | hours |
| Doc / spec | do we agree on what we're doing? | hours |

Not everything is an app. If a spreadsheet or a human behind the curtain answers the question, that's the right build.

## Tool map — platform-agnostic
Let **constraints** pick the tool — data residency, existing stack, budget, control, speed — not brand loyalty. Always name an alternative. When the user asks how they'd build it elsewhere, or names a constraint that forces a trade-off, **render this as a comparison table** (platform · what you'd build there · effort · the trade-off) rather than a flat list.

- **Models:** open-weight (Llama, Mistral, Qwen) for control/on-prem · hosted APIs (Anthropic Claude, OpenAI GPT, Google Gemini) for speed.
- **Orchestration & retrieval:** LangChain, LlamaIndex · vector stores (pgvector, Qdrant, Weaviate, Pinecone).
- **Rapid prototyping:** coding agents (Claude Code, Cursor) · app builders (v0, Lovable, Replit, Bolt).
- **Corporate stacks:** Microsoft (Foundry, Copilot Studio) · Google (Gemini Enterprise, Vertex) · AWS (Bedrock).
- **No-code / analysis:** Power Platform, AppSheet, Airtable, a spreadsheet, your analytics tool.

State the constraint that drove the pick, e.g. *"hosted API — no sensitive data, and speed matters more than control here."*

## Visual bar (UI artifacts)
Make it feel intentional and credible, not production-grade:
- **Single-file HTML by default**, no external dependencies or CDNs — a demo that needs the network is a demo that fails on stage.
- One accent color on a neutral base; two type sizes and one weight jump carry the hierarchy. A system font stack is fine.
- Consistent spacing rhythm, generous whitespace, left-aligned body text.
- Lightweight inline icons only where they speed comprehension — not decoration.
- **Show the reasoning, not a black-box answer** — evidence beside every output is what makes a prototype trustworthy.
- **Realistic sample data, never lorem ipsum.** Fake-looking data makes real logic look fake.

## Rules
- **One artifact, one question.** Don't overbuild.
- **Never use real customer data.** Synthetic or sample only, until security has cleared the path.
- Kill live external dependencies for demos: cache, stub, or pre-record, and keep an offline fallback.
- Be explicit about what's faked — including the model — so nobody mistakes a demo for production.
- Optimize for speed and rebuildability, not elegance. Pick what you can change in front of someone.
- Keep the output easy for later steps to ingest: consistent field names, a self-explanatory artifact, an explicit handoff target.

## Modes
- **Compact** (small stakes): the core block + three bullets of reasoning. Nothing else.
- **Full** (higher stakes): core + extended block, plus decision rationale, failure modes, readiness questions, and the demo script.

## Solo-PM check
- **Timebox** — how long will this take, and does it beat the learning value?
- **Solo-doable vs. needs someone** — what can you build alone this week; what needs a designer, a data pull, or an approval? Start that dependency now.
- **Who reacts** — name the 3–5 real people who'll see it. An artifact nobody reacts to produced no signal.
- **Leaves behind** — the template, component, or dataset you'll reuse next cycle.

## Ready for Iterate?
- [ ] Does the artifact test **one** assumption, and could it fail?
- [ ] Are the success and kill signals written down *before* anyone sees it?
- [ ] Is everything faked listed — and is the data synthetic?
- [ ] Can you demo it end-to-end, offline?
- [ ] Is `handoff_target` set?

## Handoff
Pass the artifact and its signals to **`iterate`** to refine it, prove it's good enough, and decide whether to ship, pause, or hand off. If the signal shows the assumption was wrong, go back to **`scope`**.
