---
name: data-validation
description: >-
  Verify every piece of incoming data — user input, third-party integration, or
  communication protocol — before it's passed to the next process, to prevent
  data loss, crashes, or invalid formats from propagating. Use whenever code
  receives input from any source. Triggers on "validate the input", "check the
  data format", "the data from the PLC/camera/API", "parse this safely",
  "invalid data", "sanitize input".
---

# Data Validation

Data enters the software from many sources — a user typing into the UI, a third
party's system, a communication protocol (TCP, MQTT, serial, …) — and any of it
can be malformed. If invalid data flows into the next process unchecked, the
result is wrong behavior, data loss, or a crash far from the real cause. This
skill puts validation at every entry point so bad data is caught at the border,
which is what makes the application robust.

## When to use this

Use during any input from any source — communication, integration, or user
input. The rule of thumb: the moment data crosses from outside the module into
your logic, it gets validated first.

## Workflow

1. Identify every entry point where external data comes in (UI fields, API
   calls, protocol messages, files, SDK callers).
2. Define what valid looks like for each: type, format, range, length, required
   fields, encoding.
3. Validate at the entry point, before the data reaches the next process. Reject
   or normalize invalid data there — never let it flow onward unchecked.
4. On invalid data, fail safely: clear error back to the source (pairs with the
   error-handling skill), log what was rejected, and keep the application alive.
5. For protocol data, also handle partial/corrupted messages — length checks,
   checksums where available, timeouts — so a bad packet can't wedge the
   pipeline.

## Output format

Entry-point validation for every input source: the checks applied, the
normalized/validated data passed onward, and safe rejection handling for
anything invalid — so no invalid format reaches downstream processing.

## Examples

Input:  A TCP message from a customer's line controller arrives with a
        truncated payload.
Output: Length/format check at the receiver rejects it, an error response is
        returned, the event is logged, and the inspection pipeline continues
        unaffected.

Input:  User enters "abc" in a numeric exposure-time field.
Output: Field validation rejects it with a clear message before any processing.

## Bundled resources

- Pairs with `error-handling` (#14) for safe rejection and alerting, and with
  `configurable-settings` (#7) for validating config values on load.
