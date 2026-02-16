# Dependency Graph (v0)

This is a lightweight dependency outline to help agents avoid circular/conflicting edits.

## Product truth (Tier A)
- `VISION.md`
  - depends: none
- `PRODUCT_STANDARDS.md`
  - depends: `VISION.md`
- `TECHNICAL_CONSTRAINTS.md`
  - depends: `VISION.md`, `PRODUCT_STANDARDS.md`

## OAIS core
- `oais/core/operating_model.md`
  - depends: `VISION.md`
- `oais/core/authority_model.md`
  - depends: `VISION.md`, `PRODUCT_STANDARDS.md`, `TECHNICAL_CONSTRAINTS.md`

## Bootstrap
- `oais/contracts/bootstrap_mode.md`
  - depends: `oais/contracts/required_artifacts.md`, `oais/contracts/project_structure.md`
- `oais/workflows/bootstrap_lifecycle.md`
  - depends: `oais/contracts/bootstrap_mode.md`, `oais/workflows/lifecycle.md`

## Feature lifecycle
- `oais/workflows/lifecycle.md`
  - depends: `oais/core/operating_model.md`
- `features/_active.md`
  - depends: `oais/workflows/lifecycle.md`

