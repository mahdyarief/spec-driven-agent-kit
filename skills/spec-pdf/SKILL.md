---
name: spec-pdf
description: Combine request.md, spec.md, and edgecases.md for a given topic and convert into a client-ready PDF using markdown-preview.
---

# Spec PDF Export Skill

Combines the 3-file specification suite into a single document and generates a PDF for client review.

## Trigger Phrases
- `/spec-pdf <topic-folder>`
- "export spec to pdf for <topic>"
- "convert <topic> brief to pdf"

## Execution Procedure

1. **Locate Target Files:**
   - Look in `feedback/<topic>/` (or `features/<topic>/`) for `request.md`, `spec.md`, and `edgecases.md`.

2. **Run Merger & Normalization:**
   - Strip frontmatter from all 3 files.
   - Insert `\newpage` page breaks between sections.
   - Ensure blank lines before bullet lists so pandoc table/list parsing does not break.
   - Save merged output to `feedback/<topic>/<topic>.md`.

3. **Generate PDF:**
   - Call the `markdown-preview` MCP tool (`mcp__plugin_markdown-preview_markdown-preview__markdown_to_pdf`) with `path: feedback/<topic>/<topic>.md` and `outputPath: feedback/<topic>/<topic>.pdf`.
   - Verify generated file size > 0.
