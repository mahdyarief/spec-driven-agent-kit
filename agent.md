# agent.md — Spec-Driven Agent Governance & Rules

Universal specification and governance rules for AI coding agents (Claude Web, Claude Code CLI, Cursor, Windsurf, and custom agent harnesses).

> **Public Remote Source:** `https://github.com/mahdyarief/spec-driven-agent-kit`
> **Zero-Clone Policy:** AI agents reference and fetch the latest version of this file and its templates directly via HTTP/MCP without requiring a local git clone.

---

## 1. Remote Consumption & Zero-Clone Architecture

To ensure all agents automatically use the latest rules and templates without local cloning:

| Platform / Agent | Integration Method | Configuration |
|---|---|---|
| **Claude Code CLI / OpenClaude** | Global `CLAUDE.md` or Remote Skill | Add directive in `~/.openclaude/CLAUDE.md`: `Always fetch latest spec rules from https://raw.githubusercontent.com/mahdyarief/spec-driven-agent-kit/main/agent.md` |
| **Claude Web / Custom GPT / Projects** | Project Instructions / Web Access | Add project custom instructions pointing to the public GitHub repository or Raw URLs. |
| **Cursor / Windsurf / Copilot** | `.cursorrules` / System Prompt | Include: `Before drafting specifications, fetch templates from https://raw.githubusercontent.com/mahdyarief/spec-driven-agent-kit/main/` |
| **MCP-Compatible Harnesses** | Remote MCP Server (SSE / Stream) | Connect `spec-driven-agent-kit` MCP server exposing `get_template`, `validate_spec`, and `export_pdf`. |

---

## 2. Workspace & Codebase Layout

Coding agents must first inspect the workspace to identify how source code is organized:

| Architecture | Source Code Paths | Operating Rules & Precedence |
|---|---|---|
| **Polyrepo (Separate FE & BE)** | `{fe_repo}/`<br>`{be_repo}/` | FE and BE live in separate sibling directories or repositories. Contract-first: BE API / Swagger updates precede FE SDK regeneration. Sub-repo instructions (`AGENTS.md`) govern local code conventions. |
| **Monorepo (Turborepo / Nx / pnpm)** | `apps/{web,api,mobile}/`<br>`packages/{ui,shared,types}/` | Multiple apps share internal packages. Any change in `packages/*` requires checking impact across all consuming apps. |
| **Unified / Fullstack Repo** | `src/app/`, `src/server/`<br>or `frontend/`, `backend/` | Single repository containing both layers (e.g., Next.js, Remix, Nuxt, Laravel, Django). |
| **Specification / Briefs** | `specs/<topic>/`<br>or `feedback/<topic>/` | One folder per topic: `request.md` + `spec.md` + `edgecases.md` (or `bug.md`), plus combined `<topic>.pdf`. Never mix specs into application source folders. |

---

## 2. Modes of Operation

### Mode A: Greenfield (Building New Applications / Features from Scratch)
- **Context Awareness:** When building an application for the first time, **no existing codebase or `file:line` references exist**. Agents must NOT expect or hallucinate existing file paths.
- **Goal:** Establish foundational architecture, domain boundaries, data models, and core flows with clear acceptance criteria before writing code.
- **Spec Focus:**
  - Problem statement, user persona, business value, and target tech stack.
  - Proposed directory structure and module layout (e.g., polyrepo vs monorepo vs fullstack).
  - Initial data schema (tables, relations, indexes) & API contract design (endpoints, payloads, responses).
  - Acceptance Criteria matrix (Concrete Input → UI Flow → API/DB State → Output).
  - Out of Scope for MVP (guardrail against premature over-engineering).

### Mode B: Brownfield (Change Requests, Enhancements, and Bug Fixes)
- **Context Awareness:** Codebase already exists in production or development branch.
- **Goal:** Solve client feedback or fix defects with minimal changes to existing code.
- **Spec Focus:**
  - Factual *Current State* verified directly from code with exact `file:line` citations.
  - Strict *Minimal Change First* policy (reuse existing tables, columns, endpoints, and helpers).
  - Explicit *Out of Scope* for major-impact architectural additions (separate brief).
  - Backward compatibility guarantees for historical data.

---

## 3. Feedback → Brief Workflow

### 3.1 Workflow Steps
1. **Project Steering Alignment:** Check `steering/product.md`, `steering/tech.md`, and `steering/structure.md` for project boundaries and architectural invariants.
2. **Intake & Context Discovery:** Ingest raw feedback (chat, ticket, or PRD).
   - *For Brownfield:* Inspect the target codebase to understand current behavior and verify `file:line` citations.
   - *For Greenfield:* Define target tech stack, project scaffolding, and proposed directory structure (no codebase reference exists yet).
3. **T-Shirt Sizing & Scaffolding:**
   - **Size S (Micro CR / 1-Component Tweak / Minor Bug):** Single file (`spec.md` with embedded edge cases, or `bug.md`).
   - **Size M / L (New Application MVP / Multi-step Flow / Schema or API Touch):** Complete 4-file suite (`request.md`, `edgecases.md`, `spec.md`, `tasks.md`).
4. **Decision Locking (`edgecases.md`):** Convert ambiguities into locked decisions (`Status: DECIDED`). Client words first; where client is silent, select the minimal-change option.
5. **Specification (`spec.md`):** Define user stories, acceptance criteria matrix (with BDD GIVEN-WHEN-THEN scenarios), UI changes, API/DB changes, error keys, and implementation notes:
   - *Brownfield:* use exact `file:line` pointers and merge order.
   - *Greenfield:* specify new file paths, proposed directory structure, initial migrations, and seed data.
6. **Task Breakdown (`tasks.md`):** Break the spec into sequential, atomic execution tasks across phases (Database & Contracts → SDK & Helpers → UI/UX → Verification).
7. **Client Sign-Off via PDF:** For Size M/L, combine markdown files and render to PDF using `markdown-preview` for client approval before coding.
8. **Implementation & Verification Gate:** Execute tasks step-by-step. Run `/spec-verify <slug>` to prevent spec drift and verify test coverage.
9. **Archival (`spec-archive`):** Upon merge and release, archive the topic folder to `specs/archive/YYYY-MM-DD-<slug>/` to keep active specs clean.

---

## 4. Change Policy & Minimal Change Rules

- **Minimal change first.** Solve feedback by extending existing endpoints, schemas, modes, helpers, and components.
- **No major-impact solutions in a minor brief.** Anything requiring a new table, column, migration, new endpoint, API breaking change, or new settings domain must be categorized under **Out of Scope (needs separate brief)**.
- No speculative abstractions, premature generalizations, or unrelated cleanup.
- Existing records and user data must remain backward-compatible.

---

## 5. Engineering & Implementation Rules

- **Contract-First:** Backend schema → Use Case / Controller → Swagger / OpenAPI → Regenerate Frontend SDK → Frontend UI. Never hand-edit generated SDK code.
- **Dual Validation:** Frontend validates for UX responsiveness; backend validates for authoritative truth. Every UI constraint must be enforced on the server.
- **Date & Time Conventions:** Adhere strictly to project timezone rules and standardized date formats (e.g. `YYYY-MM-DD` string in DB/API).
- **No Spec Drift:** If edge cases or implementation details shift during development, update `spec.md` and `edgecases.md` in the exact same commit and pull request as the code.
- **Testing & Verification:**
  - Backend: Vitest / Jest unit and integration tests covering each Acceptance Criteria row.
  - Frontend: Unit tests for pure business helpers and manual test checklist for UI states.
  - Report exact test results; never claim unverified work as complete.
