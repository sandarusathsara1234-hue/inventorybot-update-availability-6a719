---
name: persona-command-editor
description: Explain, extend, or modify a persona slash command across its parent chat configuration and connected Operator workflow.
metadata:
  version: "1.0"
  pageId: "f9db9227-bce2-489c-bb67-51702ac47d95"
  commandId: "cmd_17c0b826-7ed0-4f29-b88a-8cad73f484d7"
  actionId: "6a719989a284aeb9db4f60ed"
---

# Persona Slash Command Editor

Use this skill whenever the author asks what /update-availability does, wants to add a feature, or wants to modify its existing behavior.

## Connected implementation

- Command: `/update-availability`
- Operator action id: `6a719989a284aeb9db4f60ed`
- Current description: Update online availability and propose substitutions for out-of-stock grocery items.
- Parent persona repository: `https://github.com/sandarusathsara1234-hue/persona-inventorybot.git`
- Parent source of truth: `assets/chat-config.json`
- Command workflow repository: `https://github.com/sandarusathsara1234-hue/inventorybot-update-availability-6a719.git`
- Executable source of truth: `assets/workflow.json`
- Relationship manifest: `assets/persona-command.json`

The parent persona configuration owns command registration and presentation: id, trigger, label, description, enabled state, and the Operator action reference. The command repository owns executable steps, prompts, runtime configuration, inputs, outputs, and generated child skills.

## First-response protocol

Before changing files:

1. Read `assets/persona-command.json`, this skill, the root `SKILL.md`, `runner/SKILL.md`, and `assets/workflow.json`.
2. Open the parent persona repository and read its `SKILL.md` and `assets/chat-config.json`.
3. Locate command id `cmd_17c0b826-7ed0-4f29-b88a-8cad73f484d7` in the parent chat config and verify that its Operator action reference points to this workflow.
4. Summarize the current feature in specific terms: invocation inputs, routing, major workflow stages, outputs, approvals, and user-visible behavior.
5. Tell the author that you can explain the implementation, extend it with new features, or modify existing behavior, then ask what they want to add or change.

If the initial request already describes a concrete change, summarize your understanding and identify which repository or repositories need edits before implementing. If a required repository or file is unavailable, report exactly what is missing instead of guessing.

## Editing rules

1. Decide file ownership before editing:
   - Edit parent `assets/chat-config.json` for registration, trigger, label, description, enabled state, presentation, or action linkage.
   - Edit command `assets/workflow.json` for executable behavior, stages, prompts, runtime configuration, inputs, outputs, approvals, or artifacts.
   - Edit both when a feature crosses the routing/execution boundary.
2. Preserve `cmd_17c0b826-7ed0-4f29-b88a-8cad73f484d7` and its Operator action linkage unless the author explicitly requests replacement.
3. Follow the root workflow-builder skill and action-specific child skills. Preserve the locked runtime-start step and keep all step fields flat.
4. Update generated child skills whenever executable behavior changes.
5. Validate `assets/workflow.json` with the repository validator and keep `assets/chat-config.json` valid JSON without credentials or secrets.
6. Do not duplicate executable steps in chat config or persona routing metadata in workflow JSON.
7. Summarize changes by repository, commit each affected repository, and push each default branch.
