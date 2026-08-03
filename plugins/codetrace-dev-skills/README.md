# CodeTrace Dev Skills

12 software development skills for CodeTrace R&D, created by Kenny Lam. They encode how CodeTrace builds software: a validated release pipeline, plugin-based modular architecture with a stable core, and deployment practices for customers and SDK integrators.

## The release pipeline (run in this order)

1. **code-validation-test** — verify new work is compatible with main, before and after merging.
2. **backward-compatibility-test** — confirm existing features still work after the change.
3. **release-note** — only after both pass: commit, push to GitHub, and record the release as a `.md` file.
4. **installation-builder** — rebuild the installer so deployment matches the new code.

## Architecture guardrails

- **structured-scripting** — organize the project into grouped folders, one concern each.
- **avoid-cross-over-scripting** — minimize dependencies between modules; prefer independent implementations.
- **software-flexibility** — never modify the stable core; add capability as plugins on top.
- **thread-assignment** — keep UI and backend on separate threads; parallelize where it helps.

## Development support

- **troubleshoot-bug-tracker** — troubleshoot bugs and record every fix using the Troubleshoot Template.
- **configurable-settings** — externalize paths and parameters so end-users configure without a developer.

## Customer deployment

- **sdk-integration-deploy** — design engine parts to be cleanly extractable as an SDK.
- **license-key** — protect externally shipped software/SDKs with license-key validation.

## Notes

- Skill create date: 31/7/2026 · Skill creator: Kenny
- Sources: `Skill List.one` and `Claude Template.one` in the OneDrive `Claude Skill` folder.

## Added in v0.2.0 (New batch, Aug 2026)

- **deployment-stress-test** — stress + memory-leak check before production deployment.
- **error-handling** — no silent crashes: every error caught, alerted, logged.
- **data-validation** — validate all incoming data (user, third-party, protocol) at entry points.
- **claude-cococom** — Cowork ↔ Claude Code bus communication via "Claude Summary" and "Claude Action" folders.
