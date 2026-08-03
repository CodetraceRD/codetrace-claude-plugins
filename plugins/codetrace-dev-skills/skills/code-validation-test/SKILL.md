---
name: code-validation-test
description: >-
  Verify that new development is compatible with the main branch, both before and
  after integration — including plugins built independently by different
  engineers. Use before merging any new function to main, and again right after
  merging. Triggers on "validate this", "is this safe to merge", "test the new
  node/plugin", "check compatibility before integration". This is a required gate
  before a release note is written.
---

# Code Validation Test

In a multi-developer, plugin-based codebase, each engineer builds their own
part (node/tool/engine) without interrupting others — but every part must be
proven compatible with the main branch before *and* after it's plugged in. This
skill is that verification gate.

## When to use this

Use it twice around every integration: (1) before merging new work into main, to
catch incompatibility early, and (2) after merging, to confirm nothing broke in
the combined system. Also use it to validate a plugin authored by another
engineer before accepting it.

## Workflow

1. Identify the new function/node/plugin being integrated and its inputs/outputs.
2. Before integration: run the validation checks in isolation to confirm the new
   part behaves correctly on its own.
3. After integration into main: re-run to confirm the part works in the combined
   system and hasn't broken the interfaces other modules rely on.
4. Report a clear pass/fail. On failure, identify which interface or dependency
   broke so it can be fixed before release.

## Output format

A validation result — pass/fail per check — with, on failure, the specific
function/interface that failed and why. Clear enough that the release pipeline
can gate on it.

## Examples

Input:  Engineer B submits a new TCP-communication plugin to merge into main.
Output: "PASS before merge; PASS after merge — inputs/outputs conform, no
        interface regressions." (or a precise failure report)

## Bundled resources

- Feeds: `release-note` (#1) and pairs with `backward-compatibility-test` (#11).
