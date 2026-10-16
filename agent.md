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

## 2. Modes of Operation

### Mode A: Greenfield (Building New Applications / Features from Scratch)
- **Goal:** Establish architecture, domain boundaries, data models, and core flows with clear acceptance criteria before writing code.
- **Spec Focus:**
  - Problem statement, user persona, and business value.
  - Initial data schema & API contract design.
  - Acceptance Criteria matrix (Concrete Input → UI Flow → API/DB State → Output).
  - Out of Scope for MVP / Initial Phase.

### Mode B: Brownfield (Change Requests, Enhancements, and Bug Fixes)
- **Goal:** Solve client feedback or fix defects with minimal changes to existing code.
- **Spec Focus:**
  - Factual *Current State* with `file:line` citations.
  - Strict *Minimal Change First* policy (reuse existing tables, columns, endpoints, and helpers).
  - Explicit *Out of Scope* for major-impact architectural additions (separate brief).
  - Backward compatibility guarantees for historical data.

---

## 3. Feedback → Brief Workflow

### 3.1 Workflow Steps
1. **Intake & Read:** Ingest raw feedback (chat, ticket, or PRD) and inspect the target codebase.
2. **T-Shirt Sizing & Scaffolding:**
   - **Size S (Micro CR / 1-Component Tweak / Minor Bug):** Single file (`spec.md` with embedded edge cases, or `bug.md`).
   - **Size M / L (Multi-step Flow / Schema or API Touch / High Ambiguity):** Complete 3-file suite (`request.md`, `edgecases.md`, `spec.md`).
3. **Decision Locking (`edgecases.md`):** Convert ambiguities into locked decisions (`Status: DECIDED`). Client words first; where client is silent, select the minimal-change option.
4. **Specification (`spec.md`):** Define user stories, acceptance criteria matrix, UI changes, API/DB changes, error keys, and implementation notes with exact `file:line` pointers.
5. **Client Sign-Off via PDF:** For Size M/L, combine markdown files and render to PDF using `markdown-preview` for client approval before coding.
6. **Implementation Gate:** Code execution starts only after brief review and sign-off.

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
