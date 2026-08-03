---
name: claude-cococom
description: >-
  Bus communication between Claude Cowork and Claude Code through two shared
  folders: "Claude Summary" (Claude Code writes complete work summaries for
  Cowork to read) and "Claude Action" (Cowork writes task assignments for Claude
  Code to pick up). Use during development whenever Claude Code and Claude
  Cowork are working together on a project. Triggers on "cococom", "sync with
  claude code", "check the action folder", "write the summary", "hand this task
  to claude code", "what did claude code finish".
---

# Claude CoCoCom (Cowork ↔ Code Bus Communication)

Claude Cowork and Claude Code cooperate on the same project but run in separate
sessions with no direct channel. This skill gives them a bus: two folders in the
project that act as a message queue in each direction. Claude Code reports what
it completed into **Claude Summary**; Claude Cowork assigns new work into
**Claude Action**. Each side checks its inbox and writes to its outbox, so the
two stay coordinated without a human relaying messages.

## When to use this

Use during development whenever Claude Code and Claude Cowork are working
together on a project. On the Cowork side: check Claude Summary at the start of
work and write to Claude Action when delegating. On the Claude Code side: check
Claude Action for new jobs before starting, and write to Claude Summary after
completing work.

## The two folders

- `Claude Summary/` — written by Claude Code, read by Claude Cowork. Contains
  complete summaries of work done: what was implemented, files changed, tests
  run, problems hit, and what's left open.
- `Claude Action/` — written by Claude Cowork, read by Claude Code. Contains
  task assignments: what to do, the context needed, and the expected output.

## Workflow

1. At the start of a session, read your inbox folder (Cowork reads
   Claude Summary; Claude Code reads Claude Action) for anything new since the
   last check.
2. Act on what's there: Cowork reviews completed work and plans next steps;
   Claude Code picks up the next assigned task.
3. When finishing, write to your outbox folder as one Markdown file per item,
   named with date and topic (e.g. `2026-08-03_login-fix.md`) so entries sort
   chronologically and never overwrite each other.
4. Mark items as processed (e.g. move to a `done/` subfolder or tag the file)
   so the same task isn't picked up twice.

## Output format

Markdown files in the two bus folders. A Claude Action task file states: task,
context, expected output, priority. A Claude Summary file states: what was done,
files changed, validation status, open items.

## Examples

Input:  (Cowork) Kenny asks to delegate the installer rebuild to Claude Code.
Output: `Claude Action/2026-08-03_rebuild-installer.md` — task, context, and
        expected output written; Claude Code picks it up on its next session.

Input:  (Claude Code) Finished implementing the TCP node with tests passing.
Output: `Claude Summary/2026-08-03_tcp-node.md` — implementation summary, files
        changed, validation results, ready for Cowork review.

## Bundled resources

- Pairs naturally with the release pipeline: Cowork can assign
  `code-validation-test` / `release-note` runs through Claude Action and read
  the results from Claude Summary.
