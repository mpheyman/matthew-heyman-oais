# Required Artifacts Contract (v0)

## OAIS truth sources (inside /oais)
- oais/core/operating_model.md (Tier A)
- oais/core/authority_model.md (Tier A)
- oais/index/canonical_index.md (Tier B)
- oais/workflows/lifecycle.md (Tier B)
- oais/workflows/convergence.md (Tier B)
- oais/workflows/change_management.md (Tier B)
- oais/agents/product_orchestrator_prompt.md (Tier B)

## Product truth sources (outside /oais)
- VISION.md (Tier A)
- PRODUCT_STANDARDS.md (Tier A)
- TECHNICAL_CONSTRAINTS.md (Tier A)

## Project execution sources (outside /oais)
- ideas/idea_backlog.md (Tier B)
- features/_active.md (Tier B)
- features/<slug>/* (feature artifacts)

## Orchestrator responsibility
The Product Orchestrator Agent must:
- verify required project directories exist (/ideas, /features)
- create missing required files using OAIS templates
- never require the human to scaffold feature folders or baseline docs
- **keep oais/ portable:** only add to `oais/` files that belong in the portable engine (see oais/contracts/project_structure.md — "What belongs inside /oais"). Never add project-specific docs (push instructions, product runbooks, etc.) to `oais/`.
