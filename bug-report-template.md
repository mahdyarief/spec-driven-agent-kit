---
title: # {Module — Short bug summary}
slug: # kebab-case (e.g., order-blackout-range-error)
type: bug
status: open # open | in-progress | fixed | verified | closed
severity: major # critical | major | minor | cosmetic
author: # fill in
date: # YYYY-MM-DD
jam: # https://jam.dev/c/<jam-id> (optional)
---

# {Bug Title}

## 1. Summary & Test Context
- **Summary:** {1–2 sentences: what fails, where, and user impact}
- **Context:** Portal URL · API Env · User/Project ID · Test Data (Order/Class ID, Date) · Jam URL

## 2. Steps to Reproduce
1. {Step 1 with concrete input}
2. {Step 2}
- **Actual Result:** {Exact error message, HTTP status, or wrong UI state}
- **Expected Result:** {Correct behavior per spec}

## 3. Evidence (Jam / Network / Console)
| Source | Finding |
|---|---|
| **Network** | {Method, endpoint, status code, payload/response} |
| **Console / Video** | {Error log, component state, video timestamp `t=...`} |

## 4. Root Cause Analysis (`file:line`)
- **Location:** `{repo}/path/to/file.ts:L10-25`
- **Root Cause:** {Why the current code produces the actual result}

## 5. Affected Components & Minimal Fix
| Layer | File (`file:line`) | Change |
|---|---|---|
| Backend / Frontend | `{path:line}` | {Targeted fix without unrelated refactoring} |

- **Recommended Fix:** {Exact code/logic adjustment; confirm backward compatibility and no schema/API break}

## 6. Verification & Regression Checklist
- [ ] Reproduction scenario passes with new/updated test in `{test_file_path}`
- [ ] Existing adjacent flows and historical records verified unaffected
