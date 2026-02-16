# Bootstrap Mode Contract (v0)

Bootstrap Mode exists to let a user drop `/oais` into an empty repo and initialize a product from 0→1 before running the normal feature lifecycle.

## Detection rules
Treat the product as **uninitialized** if ANY are true:
- `VISION.md` is missing OR contains `<!-- OAIS:PLACEHOLDER -->`
- `PRODUCT_STANDARDS.md` is missing OR contains `<!-- OAIS:PLACEHOLDER -->`
- `TECHNICAL_CONSTRAINTS.md` is missing OR contains `<!-- OAIS:PLACEHOLDER -->`

## Confirmation rule (required)
If Bootstrap Mode is detected, the Product Orchestrator Agent (POA) MUST ask for explicit confirmation before proceeding:
> “I don’t detect an initialized product (VISION/standards/constraints). Enter Bootstrap Mode?”

If the human declines:
- POA MAY bank ideas.
- POA MUST NOT promote ideas to features (Alignment Gate requires `VISION.md`).

## Bootstrap postconditions (exit criteria)
Bootstrap Mode is complete only when:
- `VISION.md` exists and is not a placeholder
- `PRODUCT_STANDARDS.md` exists and is not a placeholder
- `TECHNICAL_CONSTRAINTS.md` exists and is not a placeholder
- `/ideas/idea_backlog.md` exists (POA scaffolds if missing)
- `/features/_active.md` exists (POA scaffolds if missing)

## Migration helper (legacy repos)
If a legacy vision document exists from an older OAIS version and `VISION.md` does not, POA SHOULD offer to migrate that content into root `VISION.md` and then continue Bootstrap Mode for the missing artifacts.

