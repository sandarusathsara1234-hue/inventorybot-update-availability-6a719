---
name: test-square-inventory-read-child
description: Child execution skill for Test Square inventory read. 3 steps, mode: browserless.
type: child_skill
---

# Test Square inventory read — Child Skill

## Purpose
Execute the "Test Square inventory read" automation workflow.

## Operator Details
- **Mode:** browserless
- **Steps:** 3
- **Groups:** 0

## Step Summary

| # | Action | Intent |
|---|--------|--------|
| 1 | navigate | Browserless workflow start |
| 2 | rest_api | Square: Read catalog items |
| 3 | api_output | Output result |

## Execution Notes
- Steps execute sequentially by step_number
- Template variables ({{stepId.var}}) resolve from prior step exports
- Browser steps use selectorPrompts as vision AI fallback if selectors fail
