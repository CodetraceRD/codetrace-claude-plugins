---
name: error-handling
description: >-
  Handle every error properly so the application never crashes or dies silently —
  each error is caught, alerted to the user, and where possible warned about
  before it happens again. Apply during all development, background processes and
  front-end UI alike. Triggers on "error handling", "try catch", "the app crashed",
  "it died without any message", "exception", "make this robust", "fail safely".
---

# Error Handling

An application must never crash or stop dead without the user knowing why. Every
error should be well handled: caught, reported with a clear alert, and — where
possible — anticipated so the user is notified before it happens next time.
Silent failures are the worst outcome, because on a production line a dead
application without an alert means unexplained downtime.

## When to use this

Apply during development, every time code is written — whether it's a background
process or front-end UI. Error handling is not a cleanup pass at the end; it's
written together with the logic it protects.

## Workflow

1. For each operation that can fail (file/device I/O, communication,
   user input, processing), wrap it in proper error handling rather than letting
   the exception escape and kill the application.
2. On error: keep the application alive, alert the user with a clear message
   (what failed, and what to do), and log the details for troubleshooting.
3. Where an error condition can be predicted (disk nearly full, camera
   disconnected, connection unstable), check for it early and notify the user
   before it becomes a failure.
4. Make sure background-thread errors are surfaced to the UI safely — an error
   swallowed inside a worker thread is still a silent failure.
5. Route recurring or significant errors into the bug history via the
   troubleshoot-bug-tracker skill.

## Output format

Code where every failure path is handled: the application stays alive, the user
is alerted, details are logged, and predictable failures warn in advance —
no crash or dead state without the user knowing.

## Examples

Input:  Camera disconnects mid-inspection and the app currently just freezes.
Output: Disconnection caught in the capture layer, inspection paused, user
        alerted "Camera 2 disconnected — check cable", event logged, and
        reconnection attempted automatically.

## Bundled resources

- Works with `thread-assignment` (#4) for surfacing worker-thread errors, and
  `troubleshoot-bug-tracker` (#5) for recording recurring errors.
