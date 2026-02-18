# Agent Roles (v0)

These are logical roles. In Cursor, you may implement them as separate chats, separate agent profiles, or separate “runs.”

## Product Orchestrator (Human)
- Owns: direction, priorities, Tier A changes, final ship decision.
- Responsibilities: approve alignment gates, resolve conflicts, accept/reject change proposals.

## Product Orchestrator Agent (Primary Entry Point)

Purpose:
- Single conversational entry point for all work (new ideas, feature progress, context switching).
- Maintains multiple concurrent features via features/_active.md and per-feature state.md.
- Enforces lifecycle transitions with adaptive guidance:
  - Bank idea
  - Promote to feature
  - Attach to existing feature

Responsibilities:
- Read OAIS truth sources before acting:
  - oais/core/authority_model.md
  - oais/workflows/lifecycle.md
  - oais/agents/stage_gate_guardrails.md
  - oais/index/canonical_index.md
- Read product truth sources if present (outside /oais):
  - VISION.md
  - PRODUCT_STANDARDS.md
  - TECHNICAL_CONSTRAINTS.md
- Create feature directories and required docs automatically.
- Update features/_active.md and features/<slug>/state.md.
- Route to “internal” roles (research/spec/decomposition/implementation/review/deploy/audit) as needed.
- Enforce stage and gate guardrails: confirm preceding stage complete before advancing; do not advance past Stage 3 or Stage 5 without explicit human approval; never implement (Stage 4) before Alignment Gate sign-off; seek clarification when planning/refining has ambiguity or multiple valid paths.
- Escalate to Human for Stage 3 (Alignment) and Stage 5 (Convergence).
- Require Change Proposal for any Tier A modification.




## Research Agent
- Outputs: Opportunity assessment, references, risks, assumptions.

## Spec Agent
- Outputs: PRD/spec with outcomes + acceptance criteria.

## Decomposition Agent
- Outputs: task breakdown, dependency list, risk list, token/cost bands (rough).

## Implementation Agent
- Outputs: code changes + tests, minimal surface area.

## Review Agent
- Outputs: diff review notes, quality issues, security/perf concerns, recommended changes.

## Docs/Index Agent
- Outputs: canonical index updates, doc map updates, feature logs.

## Deploy/Audit Agent
- Outputs: deploy checklist completion + post-deploy audit summary.
