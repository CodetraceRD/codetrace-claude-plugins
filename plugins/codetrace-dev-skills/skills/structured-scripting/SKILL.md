---
name: structured-scripting
description: >-
  Organize a project into well-structured, grouped folders so each concern lives
  in its own module — standardizing the layout and letting you hand a new
  engineer just their part without exposing the whole codebase. Use when starting
  a new project or tool, or laying out where new code should live. Triggers on
  "project structure", "folder organization", "how should I structure this",
  "where does this file go", "modular layout".
---

# Structured Scripting & Grouping

A project must be well structured, with each folder owning a clear group of
responsibilities. Good structure standardizes development, makes dependencies
predictable, and — importantly — lets you give a new engineer exactly the part
they need instead of the whole codebase, which reduces security and privacy
exposure.

## When to use this

Use when designing the structure of a project and when developing a new tool —
i.e., whenever you decide where code should live. Establish the grouping early;
retrofitting structure onto a sprawling project is painful.

## Workflow

1. Break the system into clear concern-groups (e.g. tool/inspection logic,
   communication layer, camera/device init, core, utilities) — each its own
   folder.
2. Place each script in the folder for its concern; don't mix concerns in one
   place.
3. Keep each group self-contained enough that it can be shared with one engineer
   in isolation.
4. Document the structure so the layout is standardized for the whole team.

## Output format

A grouped folder/module structure with each concern isolated, documented so new
engineers can be handed a single part without seeing the rest.

## Examples

Input:  Starting a new vision library.
Output: A structure with folders for `inspection-tools/` (one script per
        inspection tool), `communication/` (TCP, UDP, FTP, MQTT, …), and
        `camera-init/` (per-brand initialization) — each isolated and documented.

## Bundled resources

- Foundation of the architecture cluster with `avoid-cross-over-scripting` (#6)
  and `software-flexibility` (#12).
