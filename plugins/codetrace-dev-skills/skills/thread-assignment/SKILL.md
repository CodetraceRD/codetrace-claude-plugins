---
name: thread-assignment
description: >-
  Keep UI and backend work on separate threads so the interface never lags,
  hangs, or freezes, and assign multi-threading where parallel processing helps.
  Use whenever building anything with concurrent or heavy background processing,
  or when the UI must stay responsive during long operations. Triggers on
  "UI freeze", "the app hangs", "run this in the background", "parallel
  processing", "threading", "responsiveness".
---

# Thread Assignment (UI vs Backend)

UI work and backend processing must not share a thread. When they do, heavy
backend work blocks the interface and the user sees lag, hanging, or a frozen
UI. This skill enforces separating them, and assigns multi-threading where a
process genuinely benefits from running in parallel.

## When to use this

Use whenever there is multiple or parallel processing, or any long-running
backend operation that could block the interface. Apply it while designing the
concurrency model of a feature, not after a freeze is already reported.

## Workflow

1. Identify which work is UI (rendering, user interaction) and which is backend
   (processing, I/O, computation).
2. Keep the UI thread free — never run backend processing on it. Move heavy work
   to a separate worker thread and communicate results back safely.
3. Where a backend process can be split into independent units, assign
   multi-threading for parallel processing — but guard shared state to avoid
   race conditions.
4. Confirm the UI stays responsive under load.

## Output format

A threading design (or corrected code) where UI and backend run on separate
threads, with parallelizable backend work assigned across threads and shared
resources protected.

## Examples

Input:  Image processing runs on the UI thread and the window freezes during
        inspection.
Output: Processing moved to a worker thread; results marshalled back to the UI;
        window stays responsive. Batch inspection parallelized across threads.

## Bundled resources

- Pairs with the modular architecture skills (#6, #10) when defining node I/O.
