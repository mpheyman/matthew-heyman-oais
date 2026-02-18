# Stage and Gate Guardrails (v0)

These rules prevent agent drift: the agent must not skip stages, assume completion, or implement before human sign-off.

## 1. Validate preceding stage before advancing

- **Before moving to any new stage**, the agent MUST confirm with the user that the **current stage is complete**.
- Do **not** infer completion from:
  - Existing build-out or code already present
  - Current context or prior conversation
  - Assumption that "we've covered it"
- **Required:** Explicitly state the current stage, list what "complete" means for that stage (per lifecycle), and ask: *"Confirm Stage N complete so I can advance to Stage N+1?"* (or equivalent). Only advance after the user confirms.
- If the user has not confirmed, do not advance. If switching features, confirm the active feature's current stage with the user before doing work in that feature.

## 2. Respect human-in-the-loop gates

- **Stage 3 (Alignment Gate)** and **Stage 5 (Convergence Review)** are human decision points.
- The agent MUST NOT:
  - Advance to the next stage (e.g. Stage 4 or Stage 6) until the user has given **explicit confirmation** (e.g. "Proceed", "Approved", "Ship", or a clear yes).
  - Start work that belongs to the next stage before the user has approved the gate.
- **Required:** Present the gate (alignment or convergence), list what approval means, and **stop**. Wait for the user to say they approve (or revise/stop/pause). Do not proceed on the same turn as presenting the gate; treat approval as a separate user message.

## 3. No implementation before Alignment Gate sign-off

- **Stage 4 (Implementation)** MUST NOT begin until the user has **explicitly approved** the Stage 3 Alignment Gate (e.g. "Proceed", "Approved", recorded in alignment_gate.md).
- The agent MUST NOT:
  - Write implementation code, apply code changes, or perform implementation tasks while the feature is in Stage 0, Stage 1, or Stage 2.
  - Begin Stage 4 work based on "context" or "we've agreed in conversation" without a recorded Alignment Gate approval.
- **Required:** If the feature is in Stage 0–3, do not implement. If in Stage 3, wait for explicit sign-off before any Stage 4 work.

## 4. Seek clarification when planning or refining

- When there are **multiple valid interpretations**, **potential deviations** from the spec, or **ambiguity** in planning or refining (Stages 0–2, or refinement during later stages), the agent MUST **ask clarifying questions** rather than assume.
- Be **inquisitive**: if a decision could go more than one way (scope, approach, priority, trade-off), surface it and ask the user to choose or confirm before proceeding.
- Do not guess the user's intent. Do not fill in blanks with a "reasonable" default without asking when the choice affects scope, quality, or risk.

---

## Summary (for quick reference)

| Guardrail | Rule |
|-----------|------|
| Preceding stage | Confirm with user that current stage is complete before advancing; do not infer from context or existing build. |
| Gates | Do not advance past Stage 3 or Stage 5 without explicit user approval; wait for a separate confirmation. |
| Implementation | Never implement (Stage 4) until Stage 3 Alignment Gate has explicit sign-off; no code in Stage 0–2. |
| Clarification | When ambiguity or multiple valid paths exist, ask; do not assume. |
