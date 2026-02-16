---
owner: System
tier: B
type: oais_contract
created: 2026-02-15
depends_on:
  - oais/contracts/project_structure.md
  - oais/workflows/convergence.md
---

# Static Site Conventions (v0)

These conventions apply when shipping a static site from a directory like `public/` (or whichever directory your host serves as the static root).

## Goals
- Avoid “works in prod, breaks locally” surprises
- Keep v0 static sites deployable with minimal tooling
- Make manual verification predictable

## Conventions

### 1) Prefer relative links inside `public/`
- **Do**: `href="labs/"`, `href="./docs/README.md"`, `href="../index.html"`
- **Avoid**: `href="/labs/"`, `href="/"` when you expect the HTML to be opened directly or served from a non-root base path.

Rationale: absolute-root links depend on the deployed domain root and can break when:
- opening HTML via `file://...`
- serving the static root under a subpath in local/dev environments

### 2) If content must be served raw (no build), keep it under the static root
If you want `.md` files to be accessible as URLs without a build step, put them under the served directory (e.g. `public/...`).

### 3) Directory routing: include `index.html`
If you want `/labs/` to resolve, ensure `public/labs/index.html` exists (most static hosts map directory paths to `index.html`).

## Manual validation (recommended)
Run a local static server against the served directory:

- `python3 -m http.server --directory public 8000`
- Open `http://localhost:8000/` and click through key links

## Notes / known caveats
- Some static hosts may set an odd content-type for `.md`. That’s acceptable for “raw markdown v0,” but should be validated post-deploy.

## Changelog
- 2026-02-15: Added conventions after shipping Labs v0 and catching a local broken-link issue caused by absolute-root URLs.

