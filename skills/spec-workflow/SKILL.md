---
name: spec-workflow
description: Intake client requirement, assess T-Shirt size, and scaffold request.md, edgecases.md, and spec.md with minimal-change guardrails.
---

# Spec Workflow Skill

Automates the translation of raw client feedback into engineer-ready specifications.

## Trigger Phrases
- `/spec-workflow <slug>`
- "create spec for <feature>"
- "intake client feedback for <slug>"

## Execution Procedure

1. **Intake & Triage:**
   - Prompt user for raw client feedback (WhatsApp / meeting notes / ticket).
   - Inspect existing codebase to understand *Current state (implemented in app)*.
   - Determine **T-Shirt size**:
     - **Size S:** Single `spec.md` with embedded edge cases, or `bug.md`.
     - **Size M / L:** 3 files (`request.md`, `edgecases.md`, `spec.md`).

2. **Scaffold Files from `_templates/`:**
   - `request.md`: Put verbatim client quote, factual current state, and assumptions table.
   - `edgecases.md`: Identify boundary conditions, state changes, backward compatibility. Apply minimal change as default decision (`Status: DECIDED`).
   - `spec.md`: Fill overview, in-scope, out-of-scope (move any schema/endpoint additions here), Acceptance Criteria matrix, and file:line implementation notes.

3. **Validate Guardrails:**
   - Ensure NO open questions remain (convert to assumptions + justification).
   - Ensure out-of-scope items are clearly flagged.
