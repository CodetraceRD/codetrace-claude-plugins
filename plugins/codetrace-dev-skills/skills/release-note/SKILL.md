---
name: release-note
description: >-
  Record a completed implementation as a versioned release note (.md) and commit
  it to GitHub. Use whenever a new feature, integration, or fix has been finished
  and is ready to be saved — triggers on "I'm done with this implementation",
  "record this release", "commit and push", "what shipped". Before writing the
  note, this skill runs the code-validation and backward-compatibility checks
  first, so it is the final gate of the post-implementation pipeline.
---

# Release Note

Every completed implementation needs a permanent record of what changed, so the
team has a location to track activity over time. This skill produces that record
as a Markdown file and safely commits the work to GitHub — but only after the
change has been validated, so broken code never gets a release note.

## When to use this

Use this each time a new implementation or integration is complete and ready to
be saved. It is the last step of the release pipeline. Do NOT commit or write the
note before validation has passed.

## Workflow

1. Run the **code-validation-test** skill on the new work. If it fails, stop and
   report — do not proceed. (Validation before release is the whole point: it
   prevents shipping a change that breaks the main branch.)
2. Run the **backward-compatibility-test** skill to confirm existing features
   still work. If it fails, stop and report.
3. Only once both pass, stage the changes, write a clear commit message, then
   commit and push to GitHub.
4. Generate the release note as a `.md` file using the Release Note Template
   (releaser name, release description, what's included, previous version,
   current version, date).

## Output format

A single `.md` release file following the Release Note Template, containing:
release description, list of what this release includes, previous → current
version, and date. Save it where releases are tracked.

## Examples

Input:  Finished the new camera-calibration node; validation + backward tests pass.
Output: A `release-YYYYMMDD.md` note summarizing the calibration node, versions
        bumped, committed and pushed to GitHub.

## Bundled resources

- Release Note Template (from your Claude Template) — the fixed output structure.
- Depends on skills: `code-validation-test` (#3) and `backward-compatibility-test`
  (#11), which must run and pass before this skill commits.
