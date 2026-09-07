---
name: study-codebase
description: >-
  Study the codebase first — structure, conventions, and the idea behind the
  project — before executing any modification or change. Use at every first
  startup of Claude Code in a project, and any time the codebase is unfamiliar
  or was changed by others since the last session. Triggers on session start in
  a repo, "before you change anything", "get familiar with this project",
  "study the code first", or receiving a modification request in a codebase not
  yet studied this session.
---

# Study Codebase

Modifying code without understanding the codebase leads to changes in the wrong
place, broken conventions, and accidental edits to the core base. At every first
startup in a project, study the codebase before taking any action on it — know
the structure and the idea of the whole before touching any part. Only after
that understanding is established may modifications begin.

## When to use this

Every time Claude Code starts up in a project: run the study before the first
modification of the session. Also re-study when returning to a project after
others have changed it, or before a task that spans unfamiliar modules. A study
is required before action — if a change is requested and the codebase has not
been studied this session, study first, then act.

## Workflow

1. Map the structure: list the folders and modules, identify what each group
   owns (per the structured-scripting layout — e.g. inspection tools,
   communication, camera init, core), and find the entry points.
2. Read the orientation files if present: README, CLAUDE.md, the release notes
   history, and `.claude/skills/` — they carry the project's conventions and
   past decisions.
3. Identify the core base versus the plugin/feature parts (the
   software-flexibility boundary), and how modules depend on each other — this
   tells you where a change is allowed to land and what its blast radius is.
4. Write a short study summary before the first modification: the project's
   purpose, the structure map, the conventions observed, and where the
   requested change belongs. State it so the user can correct any
   misunderstanding early.
5. If CLAUDE.md is missing or outdated, offer to write/refresh it with what was
   learned — then the next startup studies faster and stays consistent.
6. Only after the summary: proceed with the requested modification, staying
   inside the boundaries identified.

## Output format

A codebase study summary delivered before the first change: purpose of the
project, structure map (folder → responsibility), core-vs-plugin boundary, key
conventions, and where the upcoming change will land. Then, and only then, the
modification work.

## Examples

Input:  First session of the day in the viFlow repo; task: "add a blur filter
        node".
Output: Study summary — node-based vision tool, `inspection-tools/` holds one
        folder per node, core pipeline under `core/` (do not modify), nodes
        register via the plugin interface. New blur node will be added as
        `inspection-tools/blur-filter/` following the existing node pattern.
        Then the implementation begins.

## Bundled resources

- Reads the boundaries defined by `structured-scripting` (#10),
  `avoid-cross-over-scripting` (#6), and `software-flexibility` (#12) — the
  study is what makes those guardrails enforceable from the first change.
