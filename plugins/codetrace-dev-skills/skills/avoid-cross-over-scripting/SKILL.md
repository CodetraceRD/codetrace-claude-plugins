---
name: avoid-cross-over-scripting
description: >-
  Keep modules independent by minimizing cross-dependencies, so any part can be
  plugged out or in without dragging other scripts with it. Use when designing
  system structure or integrating software — prefer an independent implementation
  first, and only accept a dependency when there's genuinely no independent
  option. Triggers on "keep this modular", "reduce coupling", "make it
  pluggable", "this shouldn't depend on that", "integration structure".
---

# Avoid Cross-Over Scripting

Code that reaches across into other parts becomes impossible to plug out cleanly.
Because this codebase is built to plug features in and out, modules should carry
the *minimum* dependency on each other. Sometimes a dependency is unavoidable —
but when there's a choice, take the independent path first, and only fall back to
a dependent design when no independent option exists.

## When to use this

Use when developing the structure of the system and when integrating software —
i.e., whenever you're about to make one module reference another. This is a
guardrail: apply it as you write, to stop scripts from quietly entangling.

## Workflow

1. Before making module A call into module B, ask whether A can do the job
   independently (via its own inputs/outputs or a shared interface) instead.
2. If independence is possible, take it — even at slightly more effort — because
   it keeps the part pluggable.
3. If a dependency is truly required, make it explicit and narrow (a defined
   interface), never a deep reach into another script's internals.
4. Flag any cross-over you had to introduce, so it's a conscious decision.

## Output format

Module boundaries and code where dependencies are minimized and explicit;
independent implementations preferred; any unavoidable dependency documented and
kept to a clean interface.

## Examples

Input:  A new inspection node wants to directly read another node's internal
        buffer.
Output: Reworked so the node receives what it needs through a defined input port
        instead — no cross-over into the other node's internals.

## Bundled resources

- Part of the architecture cluster with `structured-scripting` (#10) and
  `software-flexibility` (#12).
