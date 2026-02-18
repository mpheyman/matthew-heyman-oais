# OAIS (v0) — Human Operator Manual

This directory is the **OAIS**. Copy this entire **`oais/`** folder into your project root to install. See **INSTALL.md** in this folder for steps.

This OAIS lets a human orchestrate a team of AI agents to ship product changes with governance.

## What you (the human) do
You only do two things:
1) Answer targeted questions from the Product Orchestrator Agent (POA)
2) Approve or reject two gates:
   - Stage 3: Alignment Gate (scope + outcomes)
   - Stage 5: Convergence Gate (diff + validation + risk)

Everything else (scaffolding docs, moving stages, creating files) is done by POA.

---

## One entry point
You always start with the **Product Orchestrator Agent**.

Prompt file:
- `oais/agents/product_orchestrator_prompt.md`

In any tool (Cursor, ChatGPT, etc.), run POA and say:
> “New idea: …”

POA will respond with:
- Context (idea bank vs feature)
- Current stage
- What it will do next
- Questions for you
- Next step after you answer

---

## Bootstrap Mode (new product initialization)

This OAIS is designed to be portable: you can drop `/oais` into an empty repo and use it to create a product from 0→1.

If POA does not detect an initialized product, it will ask to enter **Bootstrap Mode** and guide you through creating the root-level product truth docs:
- `VISION.md`
- `PRODUCT_STANDARDS.md`
- `TECHNICAL_CONSTRAINTS.md`

After you approve these, POA will scaffold the normal execution artifacts:
- `ideas/idea_backlog.md`
- `features/_active.md`

Then the standard feature lifecycle begins.

---

## Refining product truth (VISION, standards, constraints)

Your root product docs (`VISION.md`, `PRODUCT_STANDARDS.md`, `TECHNICAL_CONSTRAINTS.md`) are Tier A: changes go through a **Change Proposal** so you approve before any edit.

**How to use POA to refine them:**

1. **Start POA** (same as always): in Cursor or another tool, load `oais/agents/product_orchestrator_prompt.md` as context (or paste it into the chat), then talk to the agent.
2. **Ask for a proposed change.** POA will draft a change proposal in `features/<name>/change_proposal.md`, then wait for your approval before editing the doc.

**Copy-paste prompts you can use:**

- **Refine VISION**
  - *“I want to refine VISION.md. Propose a change proposal: [e.g. add a success-metrics section / tighten non-goals / clarify who the product is for]. Then I’ll approve and you apply.”*

- **Refine PRODUCT_STANDARDS**
  - *“Propose changes to PRODUCT_STANDARDS.md: [e.g. add accessibility criteria / clarify performance budget / add a section on content tone]. Use a change proposal, then I’ll approve.”*

- **Refine TECHNICAL_CONSTRAINTS**
  - *“Propose updates to TECHNICAL_CONSTRAINTS.md: [e.g. add hosting constraints / clarify no-DB rule / add auth non-goals]. Change proposal first, then apply after I approve.”*

- **Review and suggest (lighter weight)**
  - *“Review VISION.md, PRODUCT_STANDARDS.md, and TECHNICAL_CONSTRAINTS.md. Suggest 3–5 concrete refinements; for each, say which doc and what to add or change. I’ll pick which to turn into change proposals.”*

After you say **“Change Proposal: Approved”** (and the proposal is in place), POA will apply the edits to the root doc.

---

## Two flows (after Bootstrap)

### 1) Idea Bank (capture anytime)
Use when you have an idea but don’t want to execute now.

POA will create:
- `ideas/<id>.md`
and link it in:
- `ideas/idea_backlog.md`

### 2) Feature Execution (structured delivery)
Use when you want to ship.

POA will create:
- `features/<slug>/state.md`
- `features/<slug>/spec.md`
- `features/<slug>/research.md`
- `features/<slug>/decomposition.md`
- `features/<slug>/implementation_log.md`
- `features/<slug>/deploy.md`
- `features/<slug>/audit.md`
and update:
- `features/_active.md`

---

## Lifecycle (the only stages you need to remember)
- Stage 0: Intake (draft)
- Stage 1: Research
- Stage 2: Spec & Decomposition
- Stage 3: Alignment Gate (YOU approve)
- Stage 4: Implementation
- Stage 5: Convergence Gate (YOU approve)
- Stage 6: Deploy
- Stage 7: Audit

You do not “run” stages manually. POA moves stages and tells you when you’re needed.

---

## The OAIS boundaries (important)
- `/oais` = the portable engine (rules, workflows, prompts)
- `VISION.md` + `PRODUCT_STANDARDS.md` + `TECHNICAL_CONSTRAINTS.md` = product truth (Tier A, repo root)
- `/ideas` + `/features` = project-specific execution artifacts
- `oais/index/canonical_index.md` tracks OAIS docs + pointers only (not every feature file)

---

## What “good” looks like
A feature is healthy when:
- `features/<slug>/state.md` matches `features/_active.md`
- Stage 3 decision is recorded in `features/<slug>/alignment_gate.md`
- Stage 5 decision is recorded in logs
- Deploy + audit are written

---

## Copy/paste commands (human shortcuts)

### Start a new idea
New idea: <one sentence>
Goal: <what success looks like>
Constraints: <must/ must-not>

### Bank it
Bank this idea. Minimal notes only.

### Promote it
Promote to feature.
Slug: <slug>
Priority: P0/P1/P2

### Approve alignment
Alignment Gate Decision: Approved
Notes: <constraints>

### Approve convergence
Convergence Decision: Approved
Notes: <any required checks>

