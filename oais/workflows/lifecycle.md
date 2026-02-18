# Lifecycle (v0) — AI-Adapted Product Development (Adaptive + Multi-Feature)

## Stage transition rules (guardrails)
- **Before advancing:** Confirm with the user that the current stage is complete. Do not infer from existing build or context.
- **Stage 3 → 4:** Advance to Implementation only after explicit human approval of the Alignment Gate (e.g. "Proceed", "Approved"). Never implement in Stage 0, 1, or 2.
- **Stage 5 → 6:** Advance to Deploy only after explicit human approval of the Convergence Review (e.g. "Ship", "Approved").
- **Clarification:** When planning or refining, if multiple valid paths or ambiguity exist, ask the user before proceeding. See oais/agents/stage_gate_guardrails.md.

## Two flows
1) Feature Execution Flow (structured stages with gates)
2) Idea Bank Flow (capture anytime)

## Idea Bank Flow
- Any time a new idea appears, it can be recorded under /ideas without interrupting active work.
- The Product Orchestrator Agent must offer: Bank / Promote / Attach.

## Feature Execution Flow
Each feature lives in: features/<feature-slug>/

### Required files (minimum)
- features/<slug>/state.md
- features/<slug>/spec.md
- features/<slug>/research.md
- features/<slug>/decomposition.md
- features/<slug>/implementation_log.md
- features/<slug>/deploy.md
- features/<slug>/audit.md

### Feature State File
state.md must include:
- Feature name
- Current stage
- Human approval required (yes/no)
- Blocking issues
- Last updated date

## Stages

### Stage 0: Intake (Draft)
Output:
- features/<slug>/state.md (Stage 0)
- features/<slug>/spec.md (draft)
Or: bank idea under /ideas

### Stage 1: Research / Discovery
Output:
- features/<slug>/research.md
- spec.md refined
Exit:
- risks + assumptions listed
- open questions resolved or flagged

### Stage 2: Spec & Decomposition
Output:
- spec.md finalized (acceptance criteria, non-goals, copy)
- decomposition.md
Exit:
- tasks + validation checklist defined

### Stage 3: Alignment Gate (Human)
Checklist:
- aligns with VISION.md
- acceptance criteria unambiguous
- risks understood
- deploy impact understood
Decision:
- proceed / revise / stop / pause

### Stage 4: Implementation
Output:
- code changes + tests (if applicable)
- implementation_log.md updated

### Stage 5: Convergence Review (Human)
Inputs:
- diff summary
- how to validate
- risks + rollback plan
Decision:
- ship / iterate / stop / pause

### Stage 6: Deploy
Output:
- deploy.md checklist + results

### Stage 7: Audit / Retro
Output:
- audit.md with outcomes + issues + follow-ups
