# Spec-Driven Agent Kit (SDAK)

> **Spec-Driven & Test-Driven Development Governance for AI Coding Agents.**
> Seamlessly bridge raw client feedback, formal engineering specs, and production code.

## Key Features
- **Dual Mode (Greenfield & Brownfield):** Architecture blueprints for new apps; minimal-change guardrails for Change Requests (CR) and bug fixes.
- **Zero-Clone Remote Consumption:** AI agents (Claude Web, Claude Code CLI, Cursor, Windsurf) can fetch latest rules and templates directly via GitHub Raw URLs without cloning locally.
- **Embedded Claude Code Skills:** Built-in slash skills (`spec-workflow`, `spec-pdf`, `spec-verify`) to scaffold briefs, export clean PDFs for client review, and prevent spec drift before PR.
- **Contract-First Quality Gate:** Acceptance Criteria matrix directly translates client requirements into unit and integration test suites.

## Repository Layout
```text
├── agent.md                  # Universal workspace governance & agent rules
├── request-template.md       # Client requirement intake & assumptions triage
├── spec-template.md          # Technical spec (Feature / Enhancement / CR)
├── edgecases-template.md     # ADR & locked edge case decision log
├── bug-report-template.md    # Root cause analysis & minimal fix
└── skills/                   # Portable Claude Code skills
    ├── spec-workflow/        # Intake & scaffolding automation
    ├── spec-pdf/             # Client-facing PDF export
    └── spec-verify/          # Pre-PR spec drift & test gatekeeper
```

## Quick Start (Zero-Clone Integration)
Add this directive to your global `~/.openclaude/CLAUDE.md` or project rules:
```markdown
## Spec-Driven Governance
Before drafting specifications or implementing changes:
1. Fetch latest governance: https://raw.githubusercontent.com/<owner>/spec-driven-agent-kit/main/agent.md
2. Fetch template: https://raw.githubusercontent.com/<owner>/spec-driven-agent-kit/main/spec-template.md
```

## License
MIT License.
