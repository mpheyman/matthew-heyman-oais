# Bootstrap Lifecycle (v0)

Bootstrap is a one-time initialization track that runs **before** the Feature Execution Lifecycle when a repo does not yet have defined product truth docs.

## Purpose
- Create product truth from scratch in an empty repo.
- Establish standards/constraints so feature work is guided and consistent.
- Only then allow normal feature promotion/execution.

## Stages

### Bootstrap 0 — Detect + confirm
Inputs:
- Presence/placeholder state of `VISION.md`, `PRODUCT_STANDARDS.md`, `TECHNICAL_CONSTRAINTS.md`

Output:
- Explicit human confirmation to enter Bootstrap Mode (or explicit decline)

### Bootstrap 1 — Vision discovery
Goal: Draft `VISION.md` with the human.

Minimum prompts:
- Problem to solve
- Target user
- Success definition
- Non-goals / out of scope
- Commercial vs experimental intent

Exit criteria:
- `VISION.md` drafted
- Human explicitly approves (or requests revisions)

### Bootstrap 2 — Product standards
Goal: Draft `PRODUCT_STANDARDS.md` (principles + quality bar).

Minimum prompts:
- Design philosophy
- Accessibility requirements
- Performance / JS stance
- Security/privacy posture
- UX/content principles

Exit criteria:
- `PRODUCT_STANDARDS.md` drafted
- Human explicitly approves (or requests revisions)

### Bootstrap 3 — Technical constraints
Goal: Draft `TECHNICAL_CONSTRAINTS.md` (baseline technical shape + non-goals).

Minimum prompts:
- Static vs dynamic bias / frameworks
- Data needs (DB or none)
- Auth needs (or none)
- Hosting/deploy target
- Explicit non-goals

Exit criteria:
- `TECHNICAL_CONSTRAINTS.md` drafted
- Human explicitly approves (or requests revisions)

### Bootstrap 4 — Feature 0 (MVP definition) → handoff
Goal: Define the smallest usable version and seed the first feature.

Minimum prompts:
- MVP statement (one paragraph)
- Top 3 acceptance criteria
- Top risks + assumptions

Outputs:
- Feature created under `features/<slug>/` with Stage 0 state + draft spec
- `features/_active.md` updated

Handoff:
- Continue in the normal Feature Execution Lifecycle (Stage 0 → Stage 1 → ...).

## Approval language (recommended)
To make approvals unambiguous, POA should ask for a response in one of these forms:
- `Bootstrap Decision: Approved`
- `Bootstrap Decision: Revise` (include requested changes)
- `Bootstrap Decision: Declined`

