# Project Structure Contract (v0)

This OAIS is portable as `/oais` and assumes project-specific execution artifacts live OUTSIDE `/oais`.

---

## What belongs inside /oais (portable engine)

**Agents and humans:** Only the following belong inside `/oais`. Nothing else. This keeps the OAIS drag-and-drop safe for other products and projects.

### Required directories (and their contents)
- **agents/** — OAIS agent prompts, roles, constraints, memory rules (e.g. `product_orchestrator_prompt.md`, `roles.md`, `constraints.md`, `memory_rules.md`).
- **contracts/** — OAIS contracts (project structure, required artifacts, bootstrap mode, static site conventions, etc.).
- **core/** — OAIS core docs (operating model, authority model).
- **index/** — OAIS index and dependency docs (`canonical_index.md`, `document_map.md`, `dependency_graph.md`).
- **workflows/** — OAIS workflow specs (lifecycle, bootstrap_lifecycle, change_management, convergence).

### Required or allowed root files in /oais
- **README.md** — Human operator manual for the OAIS.
- **INSTALL.md** — How to install/copy the OAIS into a repo.

### Must NOT be inside /oais
- **Project-specific docs** — e.g. push instructions for a specific GitHub repo, product-specific runbooks, or any doc that references a single product/org.
- **Product or app code** — no `public/`, no app source, no product config that is not part of the generic OAIS.
- **Feature or idea artifacts** — no `features/`, no `ideas/`; those live outside `/oais`.

When adding or changing files under `/oais`, ensure they are generic to the OAIS and portable. If a doc is specific to one project (e.g. “how we push our OAIS to our repo”), keep it **outside** `/oais` (e.g. in repo root `docs/` or in a feature folder).

---

## Phases

### Uninitialized product (Bootstrap Mode)
In an empty/new repo, only `/oais` is required. The Product Orchestrator Agent (POA) must detect an uninitialized product and guide the human through creating the product truth docs:
- `VISION.md`
- `PRODUCT_STANDARDS.md`
- `TECHNICAL_CONSTRAINTS.md`

After those exist, POA scaffolds the execution directories/files below.

### Initialized product (normal operation)
Once initialized, these top-level directories must exist (outside `/oais`). POA must create them if missing:
- /ideas
- /features

## Optional top-level directories (project-defined)
- /public (or /site, /app, etc.)

## Rationale
- /oais is the portable “engine” (rules, workflows, prompts)
- /ideas and /features are project-specific “data” (instances executed under the OAIS)

## Required paths (outside /oais)

### Idea Bank
- ideas/idea_backlog.md

### Feature Registry
- features/_active.md

### Feature workspace (per feature)
- features/<slug>/state.md
- features/<slug>/spec.md
- features/<slug>/research.md
- features/<slug>/decomposition.md
- features/<slug>/implementation_log.md
- features/<slug>/deploy.md
- features/<slug>/audit.md
