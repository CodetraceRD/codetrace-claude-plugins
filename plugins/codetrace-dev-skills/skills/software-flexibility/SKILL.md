---
name: software-flexibility
description: >-
  Protect the core/base of the software from change — build a strong, firm
  foundation once, then add or remove capability as plugins/features on top,
  rather than editing the base. Use at the start of new development and during
  maintenance/troubleshooting to prevent core modifications. Triggers on "don't
  touch the base", "add this as a plugin", "keep the core stable", "reusable
  across projects", "minimize changes".
---

# Software Flexibility

The base of the software should be developed strong and firm, then left alone.
Future needs are met by adding to a feature/plugin list or plugging capability in
and out — not by modifying the foundation. This keeps the same base reusable
across different projects and avoids destabilizing what already works.

## When to use this

Use at the start of new development to get the base right, and — critically —
during maintenance and troubleshooting: when fixing a bug, do not change the base
structure; solve it at the plugin/feature layer wherever possible.

## Workflow

1. Distinguish the *core/base* (stable foundation) from *features* (plugins that
   attach on top).
2. When adding capability, implement it as a feature/plugin against the base's
   existing interfaces — don't modify the base.
3. When fixing or maintaining, resist changing the base; contain the change to
   the feature layer unless the base is genuinely defective.
4. If the base truly must change, treat it as a deliberate, reviewed decision —
   because it affects every project built on it.

## Output format

Changes expressed as plugins/features on top of an unchanged base; any
unavoidable base change explicitly justified and flagged.

## Examples

Input:  A customer wants a new defect-classification step.
Output: Added as a plugin node against the existing pipeline interface — base
        engine untouched — so other projects on the same base are unaffected.

## Bundled resources

- Completes the architecture cluster with `structured-scripting` (#10) and
  `avoid-cross-over-scripting` (#6). Consider whether #6 and #12 should merge.
