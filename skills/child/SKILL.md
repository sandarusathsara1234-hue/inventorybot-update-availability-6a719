---
name: update-online-availability-child
description: Child execution skill for Update online availability. 8 steps, mode: browserless.
type: child_skill
---

# Update online availability — Child Skill

## Purpose
Execute the "Update online availability" automation workflow.

## Operator Details
- **Mode:** browserless
- **Steps:** 8
- **Groups:** 0
- **Template Variables:** `{{SQUARE_LOCATION_ID}}`, `{{INVENTORY_THRESHOLD}}`, `{{step-b3d4e.inventoryItems}}`, `{{step-c5f6a.oosList}}`, `{{SHOPIFY_STORE_DOMAIN}}`, `{{GOOGLE_SHEET_ID}}`, `{{step-d7e8f.stagedAvailabilityChanges}}`, `{{step-e9a0b.substitutions}}`, `{{step-f1c2d.confirmed}}`

## Step Summary

| # | Action | Intent |
|---|--------|--------|
| 1 | navigate | Browserless workflow start |
| 2 | mcp_tool | Square: Read inventory counts |
| 3 | mcp_tool | Derive out-of-stock list from Square output |
| 4 | mcp_tool | Shopify: Stage availability updates (draft, not published) |
| 5 | mcp_tool | Google Sheets: Read substitution rules and rank substitutes |
| 6 | confirmation | Human approval: Review staged changes and substitutes |
| 7 | mcp_tool | Shopify: Publish availability updates ONLY if approved |
| 8 | api_output | Structured final result output |

## Execution Notes
- Steps execute sequentially by step_number
- Template variables ({{stepId.var}}) resolve from prior step exports
- Browser steps use selectorPrompts as vision AI fallback if selectors fail
