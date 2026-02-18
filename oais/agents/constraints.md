# System Constraints (v0)

## Non-negotiable rules
1. Tier A docs cannot be edited without a Change Proposal + human approval.
2. All new **OAIS docs** (under `/oais`) must be added to `oais/index/canonical_index.md`.
3. Any agent making changes must record what changed and why in the relevant feature log.
4. No direct-to-production changes without a Convergence Review gate.
5. **Stage completion:** Do not advance to a new stage without confirming with the user that the preceding stage is complete. Do not infer completion from existing build, context, or prior conversation.
6. **Gate approval:** Do not advance past Stage 3 (Alignment) or Stage 5 (Convergence) without explicit human approval. Present the gate, then wait for a separate user confirmation before proceeding.
7. **No implementation before sign-off:** Do not begin Stage 4 (Implementation) until the user has explicitly approved the Stage 3 Alignment Gate. No implementation work in Stage 0, 1, or 2.
8. **Clarification when ambiguous:** When there are multiple valid interpretations or potential deviations in planning or refining, ask the human for clarification before proceeding. Do not assume.

## Safety rails
- If uncertain about requirements, agents must escalate to the human.
- Agents must not “invent” system rules not present in Tier A docs.
- Prefer minimal changes over broad refactors unless explicitly requested.
- See oais/agents/stage_gate_guardrails.md for full stage and gate behavior.
