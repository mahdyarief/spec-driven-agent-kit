---
title: # {Feature / Enhancement / Change Request Name}
slug: # kebab-case (e.g., repeat-load)
type: change-request # feature | enhancement | change-request
status: draft # draft | in-review | approved | implemented
author: # fill in
date: # YYYY-MM-DD
target_release: # TBD
---

# {Title}
> **Source:** `feedback/{slug}/request.md` · **Rules:** `agent.md` · **Edge cases:** `feedback/{slug}/edgecases.md` *(or embedded below for Size S)*

<!-- Note: For Size S tasks, edge cases can be kept directly in a "## Edge Cases" section at the bottom of this file. For Size M/L, keep edgecases.md separate. -->

## Overview & Problem / Motivation
- **Context / Current State:**
  - *For New App / Greenfield Feature:* User problem, business goals, target user persona, and foundational architecture.
  - *For Existing App (CR / Enhancement):* What is currently implemented in FE/BE with `file:line` references.
- **Client feedback / Feature motivation:** {What needs to be built/changed, why now, and success criteria}

## Scope
- **In Scope:** {Minimal-change items delivered in this brief}
- **Out of Scope (needs separate brief):** {Any new table/column/migration, new endpoint, contract break, or new settings domain}

## User Stories & Acceptance Criteria
- *As a {role}, I want to {action} so that {benefit}.*

| # | Scenario / Input | UI Behavior | API Payload | Expected Result |
|---|---|---|---|---|
| 1 | ... | ... | ... | ... |

- [ ] {Testable acceptance criterion mapped to table rows}
- [ ] {Existing flows, self-collection/edit, and existing records remain backward-compatible}

## UI / UX Changes ({frontend_repo} / apps/web)
- **Affected Routes / Screens:** {e.g., `src/routes/checkout/index.tsx` or `pages/dashboard/index.vue` — *for greenfield: specify new page paths*}
- **Component & State Changes:** {Exact fields, labels, visibility rules, and pure state/form helpers}

## API & Database Changes ({backend_repo} / apps/api)
| Method | Path | Contract Change | Validation / Logic Change |
|---|---|---|---|
| POST | `/v1/...` | None / Extended / New | {Describe validation, entity, or service changes} |

- **Database / Migrations:** None *(or specify new tables/columns/indexes if building new feature/app)* · **SDK Regen Needed:** Yes / No

## Business Rules & Error Handling
1. **{Rule name}:** {Exact business logic — *for brownfield: add file:line reference; for greenfield: add domain validation invariant*}

| Error Key | HTTP | Message (EN & Localized) | Trigger |
|---|---|---|---|
| `...` | 400 | "..." | ... |

## Dependencies & Implementation Notes (Tests & Docs)
- **Merge Order & Docs:** {e.g., BE PR first, then FE PR; update API docs / Swagger}
- **Tests:** Backend Tests (`tests/unit/...`, `tests/integration/...`) · Frontend Unit Tests & Manual QA Checklist
<!-- Note for Greenfield Projects: If building a brand new application, file:line references do not exist yet. Instead, specify proposed directory structure, initial schemas, and new file boundaries. -->
