---
name: installation-builder
description: >-
  Rebuild the software's installer file so deployment stays in sync with the
  latest code. Use whenever a new implementation or integration is completed —
  the same trigger as a release note. Triggers on "rebuild the installer",
  "update the setup file", "package for deployment", "new build for the
  customer". Every code change that ships must be reflected in a fresh installer.
---

# Installation Builder

Every product CodeTrace ships must come with an installer, because that is what
makes deployment and setup easy for the end-user. Whenever the code changes, the
installer must be rebuilt so what the customer installs matches the current code.

## When to use this

Use this each time after a new integration or implementation — right alongside
the release note. If the code changed, the installer is now stale and must be
regenerated.

## Workflow

1. Confirm the release has been validated and committed (this normally runs just
   after the `release-note` skill).
2. Rebuild the installer from the current, committed code so the packaged output
   reflects the latest changes.
3. Verify the installer produces a clean install/setup for the end-user.

## Output format

An updated installer file, built from the current committed code, ready to hand
to deployment or the end-user.

## Examples

Input:  Calibration node merged and released.
Output: A freshly rebuilt installer that includes the calibration node.

## Bundled resources

- Runs after `release-note` (#1) in the post-implementation pipeline.
