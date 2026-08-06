---
name: update-online-availability-child
description: Child execution skill for Update online availability. 9 steps, mode: browserless.
type: child_skill
---

# Update online availability — Child Skill

## Purpose
Execute the "Update online availability" automation workflow.

## Operator Details
- **Mode:** browserless
- **Steps:** 9
- **Groups:** 0
- **Template Variables:** `{{step-b3d4e.oosList}}`, `{{step-c5f6a.substitutions}}`, `{{step-d7e8f.confirmed}}`, `{{step-f1c2d.stagedAvailabilityChanges}}`

## Step Summary

| # | Action | Intent |
|---|--------|--------|
| 1 | navigate | Browserless workflow start |
| 2 | mcp_tool | Read Gabriel inventory list (OOS detection) |
| 3 | mcp_tool | Read Gabriel substitutes list (rank) |
| 4 | confirmation | HARD GATE: Review OOS items and substitutes before external writes |
| 5 | mcp_tool | Square: read_inventory / verify (Phase B) |
| 6 | mcp_tool | Shopify: STAGE availability updates for OOS (Phase B) |
| 7 | mcp_tool | Sheets: rank_substitutes / sync rules (Phase B) |
| 8 | confirmation | Second confirmation: Publish Shopify availability updates? |
| 9 | api_output | Structured final result output |

## Execution Notes
- Steps execute sequentially by step_number
- Template variables ({{stepId.var}}) resolve from prior step exports
- Browser steps use selectorPrompts as vision AI fallback if selectors fail
