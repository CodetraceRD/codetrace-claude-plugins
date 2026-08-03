---
name: sdk-integration-deploy
description: >-
  Design engine parts so they can be cleanly extracted and shipped to a vendor or
  customer as an SDK, without exposing the whole codebase. Use while developing
  engine/tool functions that a third party may later need to integrate into their
  own system. Triggers on "ship this as an SDK", "the customer wants to integrate
  our engine", "expose this as a library", "third-party integration".
---

# SDK Third-Party Integration

Sometimes a vendor or customer wants to integrate CodeTrace's engine into their
own system. That means certain parts — typically the engine, not the whole
product — must be cleanly detachable and packaged as an SDK. This skill keeps
those parts designed for clean extraction from the start.

## When to use this

Use while developing engine-level functions and tools that could plausibly be
deployed to a third party. Building for extractability up front is far cheaper
than retrofitting a tangled module into an SDK later.

## Workflow

1. Identify which parts are candidates to ship as an SDK (usually the engine and
   specific tools), and which must stay internal.
2. Give those parts a clean, documented public interface; keep internal details
   private so extraction doesn't drag the whole codebase along.
3. Minimize their dependencies on internal-only code (works hand-in-hand with
   `avoid-cross-over-scripting`).
4. Package the extractable part as an SDK deliverable with the interface a third
   party would call.

## Output format

An SDK-ready module: a cleanly bounded engine/tool part with a documented public
API, minimal internal coupling, packaged for a third party to integrate.

## Examples

Input:  A customer wants to embed the vision inspection engine in their line
        controller.
Output: The engine exposed behind a stable API and packaged as an SDK, without
        shipping the surrounding application code.

## Bundled resources

- Closely related to `avoid-cross-over-scripting` (#6) and `license-key` (#9).
