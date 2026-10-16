---
name: spec-verify
description: Verify PR readiness against the approved spec — checks for spec drift, acceptance criteria test coverage, and backward compatibility.
---

# Spec Verify Skill

Pre-PR gatekeeper that ensures code implementation matches the approved specification without unrecorded drift.

## Trigger Phrases
- `/spec-verify <topic-slug>`
- "check spec drift for <topic>"
- "verify PR against spec"

## Execution Procedure

1. **Read Approved Spec:**
   - Load `spec.md` (Acceptance Criteria, In Scope, Business Rules).
   - Load `edgecases.md` (Decisions).

2. **Inspect Git Diff & Tests:**
   - Check git status and staged/committed diff for the feature branch.
   - Verify every row in the Acceptance Criteria matrix is covered by code or tests.
   - Verify test files (`tests/unit/...`, `tests/integration/...`) were added or updated.

3. **Check for Spec Drift:**
   - Did implementation change an API schema, field name, or business rule not present in `spec.md`?
   - If yes: require updating `spec.md` and `edgecases.md` in the exact same commit/PR.
   - Confirm no out-of-scope items were accidentally introduced.
