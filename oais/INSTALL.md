# Install the OAIS into any repo (60 seconds)

1) Copy `/oais` into the repo root.
2) Start POA using `oais/agents/product_orchestrator_prompt.md`.
3) If this is a brand-new repo, POA will detect missing product truth docs and ask to enter **Bootstrap Mode**.
4) In Bootstrap Mode, POA will guide you to create (repo root):
   - `VISION.md`
   - `PRODUCT_STANDARDS.md`
   - `TECHNICAL_CONSTRAINTS.md`
5) After bootstrap, POA will scaffold execution artifacts (if missing):
   - `/ideas/idea_backlog.md`
   - `/features/_active.md`
6) Then continue normally. Example:
   - “New idea: …”

That’s it.
