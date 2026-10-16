---
name: spec-archive
description: Archive completed and verified specification briefs into specs/archive/YYYY-MM-DD-<slug>/ to keep active specs clean.
---

# Spec Archive Skill

Safely archives completed feature and change request specifications after PR merge and production verification.

## Trigger Phrases
- `/spec-archive <slug>`
- "archive spec <slug>"
- "mark <slug> as complete and archive"

## Execution Procedure

1. **Verify Completion:**
   - Check `spec.md` status (must be `implemented` or verified).
   - Verify all tasks in `tasks.md` are checked (`[x]`).

2. **Create Archive Destination:**
   - Target path: `specs/archive/YYYY-MM-DD-<slug>/` (using current date).
   - Move active topic directory:
     `mv specs/<slug>/ specs/archive/YYYY-MM-DD-<slug>/`
     (or `feedback/<slug>/` if configured).

3. **Update Living Documentation:**
   - If the spec established permanent architectural patterns, update `steering/product.md`, `steering/tech.md`, or `steering/structure.md`.
   - Update repository changelog or release notes if applicable.
