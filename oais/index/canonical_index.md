# Canonical Index (v0)

This is the source of truth for all project documents and rules.

## Rules
1. This index tracks **OAIS documents** (everything under `/oais`).
2. Agents MUST consult this file before creating or modifying OAIS docs.
3. Tier B OAIS docs may be updated by agents, but changes must be recorded in the doc changelog.

## Documents

### Core
- oais/core/operating_model.md — Owner: Human — Tier: A — Depends: VISION.md
- oais/core/authority_model.md — Owner: Human — Tier: A — Depends: VISION.md, PRODUCT_STANDARDS.md, TECHNICAL_CONSTRAINTS.md

### Index
- oais/index/canonical_index.md — Owner: System — Tier: B — Depends: oais/core/*
- oais/index/document_map.md — Owner: System — Tier: B — Depends: oais/index/canonical_index.md
- oais/index/dependency_graph.md — Owner: System — Tier: B — Depends: oais/index/canonical_index.md

### Agents
- oais/agents/roles.md — Owner: System — Tier: B — Depends: oais/core/*
- oais/agents/constraints.md — Owner: System — Tier: B — Depends: oais/core/authority_model.md
- oais/agents/stage_gate_guardrails.md — Owner: System — Tier: B — Depends: oais/workflows/lifecycle.md
- oais/agents/memory_rules.md — Owner: System — Tier: B — Depends: oais/index/canonical_index.md
- oais/agents/product_orchestrator_prompt.md — Owner: System — Tier: B — Depends: oais/core/*, oais/workflows/lifecycle.md, oais/workflows/bootstrap_lifecycle.md, oais/contracts/bootstrap_mode.md, oais/agents/stage_gate_guardrails.md

### Workflows
- oais/workflows/lifecycle.md — Owner: System — Tier: B — Depends: oais/core/operating_model.md
- oais/workflows/bootstrap_lifecycle.md — Owner: System — Tier: B — Depends: oais/workflows/lifecycle.md, oais/contracts/bootstrap_mode.md
- oais/workflows/convergence.md — Owner: System — Tier: B — Depends: oais/core/authority_model.md
- oais/workflows/change_management.md — Owner: System — Tier: B — Depends: oais/core/authority_model.md

### Contracts
- oais/contracts/required_artifacts.md — Owner: System — Tier: B — Depends: oais/core/*
- oais/contracts/project_structure.md — Owner: System — Tier: B — Depends: oais/core/*
- oais/contracts/bootstrap_mode.md — Owner: System — Tier: B — Depends: oais/contracts/required_artifacts.md, oais/contracts/project_structure.md
- oais/contracts/static_site_conventions.md — Owner: System — Tier: B — Depends: oais/contracts/project_structure.md

### Project pointers (outside /oais)
- VISION.md — Owner: Human — Tier: A — Depends: none
- PRODUCT_STANDARDS.md — Owner: Human — Tier: A — Depends: VISION.md
- TECHNICAL_CONSTRAINTS.md — Owner: Human — Tier: A — Depends: VISION.md, PRODUCT_STANDARDS.md
- ideas/idea_backlog.md — Owner: System — Tier: B — Depends: VISION.md
- features/_active.md — Owner: System — Tier: B — Depends: oais/workflows/lifecycle.md

## Changelog
- 2026-02-15: Added `oais/agents/stage_gate_guardrails.md`; strengthened stage completion validation, human-in-the-loop gates, no-implementation-before-Alignment sign-off, and clarification-seeking in POA prompt, constraints, lifecycle, and roles.
- 2026-02-15: Restricted canonical index to OAIS docs + project pointers only (keeps feature artifacts and site content out of this index).
- 2026-02-15: Added OAIS contracts section and `oais/contracts/static_site_conventions.md`.
