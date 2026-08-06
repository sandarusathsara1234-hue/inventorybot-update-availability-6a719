# InventoryBot — /update-availability Workflow (Repo 2)

## Overview

This workflow executes **after confirmation** in Gabriel Chat. Phase A simulation runs first (canvas simulation in Repo 1), then this workflow handles Phase B external app execution.

## Phases

### Phase A — Simulate (in chat, via Repo 1 canvas)

1. `/update-availability` triggers canvas simulation
2. Reads Gabriel inventory list → detects OOS items
3. Stages availability changes (status → staged_offline)
4. Reads Gabriel substitutes list → ranks substitutes
5. Each stage requires human approval (stage gates)

### Phase B — Execute after confirm (this workflow)

1. **Navigate** (browserless start)
2. **Read Gabriel inventory list** — OOS detection
3. **Read Gabriel substitutes list** — rank
4. **HARD GATE: Confirmation** — review OOS + substitutes before any external writes
5. **Square** — verify inventory (only if confirmed)
6. **Shopify** — STAGE availability updates (draft, not published)
7. **Sheets** — sync substitution rules
8. **Second confirmation** — publish Shopify changes live?
9. **API output** — structured result with summary

## Key constraints

- **No external writes without confirmation** — cancel = external apps untouched
- **Shopify stages first** — permanent publish only after second confirmation
- **Browserless only** — no browser automation
- **Flat step fields** — no wrapper objects (arguments/params/input)
- **Gabriel lists first** — Phase A data comes from Gabriel Lists, not Square/Shopify/Sheets

## Testing

Test only in Gabriel Chat:

1. Open InventoryBot persona
2. Run `/update-availability`
3. Paste goal: "Update online availability and propose substitutions for out-of-stock grocery items."
4. Approve stage gates (Phase A)
5. Confirm HARD GATE to proceed to Phase B
6. Confirm second gate to publish Shopify changes

## Expected result

> Catalog availability staged with substitution recommendations for approval.
