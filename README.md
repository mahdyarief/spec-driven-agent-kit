# Spec-Driven Agent Kit (SDAK)

> **Spec-Driven & Test-Driven Development Governance for AI Coding Agents.**
> Seamlessly bridge raw client feedback, formal engineering specs, and production code.

## Key Features
- **Dual Mode (Greenfield & Brownfield):** Architecture blueprints for new apps; minimal-change guardrails for Change Requests (CR) and bug fixes.
- **Project Steering Context (`steering/`):** Living documents for product vision (`product.md`), technology stack (`tech.md`), and codebase architecture (`structure.md`).
- **Atomic Task Breakdown (`tasks-template.md`):** Phased execution checklist (Database → SDK → UI → Verification) for systematic agent implementation.
- **BDD & Contract Quality Gate:** Acceptance Criteria matrix augmented with GIVEN-WHEN-THEN scenarios for automated test generation.
- **Zero-Clone Remote Consumption:** AI agents (Claude Web, Claude Code CLI, Cursor, Windsurf) can fetch latest rules and templates directly via GitHub Raw URLs without cloning locally.
- **Embedded Claude Code Skills:** Built-in slash skills (`spec-workflow`, `spec-pdf`, `spec-verify`, `spec-archive`) to scaffold briefs, export clean PDFs, prevent spec drift, and manage lifecycle.

## Repository Layout
```text
├── agent.md                  # Universal workspace governance & agent rules
├── request-template.md       # Client requirement intake & assumptions triage
├── spec-template.md          # Technical spec (Feature / Enhancement / CR) with BDD
├── edgecases-template.md     # ADR & locked edge case decision log
├── bug-report-template.md    # Root cause analysis & minimal fix
├── tasks-template.md         # Phased task execution checklist
├── steering/                 # Project-level living architecture documents
│   ├── product.md            # Vision, goals, personas, and anti-goals
│   ├── tech.md               # Tech stack, constraints, and invariants
│   └── structure.md          # Repository structure and layering patterns
└── skills/                   # Portable Claude Code skills
    ├── spec-workflow/        # Intake & scaffolding automation
    ├── spec-pdf/             # Client-facing PDF export
    ├── spec-verify/          # Pre-PR spec drift & test gatekeeper
    └── spec-archive/         # Post-release specification archiver
```

## Quick Start (Zero-Clone Integration)
Add this directive to your global `~/.openclaude/CLAUDE.md` or project rules:
```markdown
## Spec-Driven Governance
Before drafting specifications or implementing changes:
1. Fetch latest governance: https://raw.githubusercontent.com/mahdyarief/spec-driven-agent-kit/main/agent.md
2. Fetch template: https://raw.githubusercontent.com/mahdyarief/spec-driven-agent-kit/main/spec-template.md
```

## License
MIT License.
