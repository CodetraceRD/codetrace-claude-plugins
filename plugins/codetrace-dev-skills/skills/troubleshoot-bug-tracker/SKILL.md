---
name: troubleshoot-bug-tracker
description: >-
  Troubleshoot and fix bugs, then record every issue and its resolution using the
  Troubleshoot Template — whether the bug came from a user ticket or was spotted
  by Claude itself. Use each time code is being debugged or a fault is
  investigated. Triggers on "there's a bug", "debug this", "user submitted a
  ticket", "why is this failing", "troubleshoot". Keeps a permanent history of
  problems solved.
---

# Troubleshoot & Bug Tracker

Every bug that's investigated — reported by a user *or* discovered by Claude
during other work — should leave a record, so the team builds a searchable
history of problems and how they were solved. This skill both drives the
troubleshooting and captures the outcome using the Troubleshoot Template.

## When to use this

Use each time you troubleshoot or debug code. Also use it proactively: if you
notice a bug while doing unrelated work, log it with this skill rather than
letting it go unrecorded.

## Workflow

1. Capture the intake: ticket ID (auto-generated), submitter, date, software
   version, bug description, and how to reproduce/trigger it.
2. Reproduce and isolate the fault; identify the root cause.
3. Apply the fix and confirm the bug no longer triggers.
4. Record the full entry using the Troubleshoot Template so it's kept in history.

## Output format

A completed Troubleshoot Template record: Ticket ID, submitter, date, software
version, bug description, trigger steps → root cause, analysis report, fix &
solution, date. Saved to the bug history.

## Examples

Input:  User ticket: "Live view goes black after switching camera brand."
Output: A Troubleshoot record — root cause (uninitialized handle on re-init),
        analysis, and the applied fix — saved to history.

## Bundled resources

- Troubleshoot Template (from your Claude Template) — the fixed output structure.
