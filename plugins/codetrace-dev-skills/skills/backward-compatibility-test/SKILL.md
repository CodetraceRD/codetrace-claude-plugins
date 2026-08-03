---
name: backward-compatibility-test
description: >-
  Confirm that a new implementation or bug fix hasn't broken any existing feature
  before it's released. Use right after integrating new work or applying a fix,
  as a required gate before writing a release note. Triggers on "did this break
  anything", "regression check", "backward compatibility", "make sure old
  features still work", "safe to release".
---

# Backward Compatibility Test

New work must never silently break what already works. After a change is
integrated, this skill re-checks existing features so a regression is caught
before release — it's the safety net that pairs with code validation.

## When to use this

Use each time after integrating a new implementation or a bug fix, before the
release note is written. Together with `code-validation-test`, it forms the
two-part gate the release pipeline depends on.

## Workflow

1. Identify the existing features and interfaces most likely affected by the
   change (and, ideally, run the full existing test set).
2. Exercise those features against the newly integrated code.
3. Compare behavior to the previous known-good baseline; any divergence is a
   regression.
4. Report pass/fail. On failure, name the broken feature so it's fixed before
   release.

## Output format

A backward-compatibility result — pass/fail — with, on failure, the specific
existing feature that regressed and how.

## Examples

Input:  A fix to the calibration node is merged.
Output: "PASS — existing inspection, capture, and export features unchanged."
        (or a precise regression report)

## Bundled resources

- Required gate for `release-note` (#1); pairs with `code-validation-test` (#3).
