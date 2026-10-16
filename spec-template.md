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

## UI / UX Changes (`fe-feat-166`)
- **Affected Routes:** {e.g., `app/routes/_dashboard.../1-information-step.tsx:L405-470`}
- **Component & Helper Changes:** {Exact fields, labels, visibility rules, and single-source pure helpers (`app/lib/...`)}

## API & Database Changes (`backend-feat-166`)
| Method | Path | Contract Change | Validation / Logic Change (`file:line`) |
|---|---|---|---|
| POST | `/v1/...` | None / Extended | {Describe validation/usecase change} |

- **Database / Migrations:** None *(or specify table/migration if `type: feature`)* · **FE SDK Regen Needed:** Yes / No

## Business Rules & Error Handling
1. **{Rule name}:** {Exact rule + `file:line` evidence verifying FE & BE alignment}

| Error Key | HTTP | Message (EN & ID in `locales/`) | Trigger |
|---|---|---|---|
| `...` | 400 | EN: "..." · ID: "..." | ... |

## Dependencies & Implementation Notes (Tests & Docs)
- **Merge Order & Docs:** {e.g., BE PR first, then FE PR; update `backend-feat-166/docs/...`}
- **Tests:** BE Vitest (`tests/unit/...`, `tests/integration/...`) · FE Unit (`app/lib/...`) & Manual checklist (`fe-feat-166/docs/...`)
