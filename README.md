# CodeTrace Claude Plugins

Internal plugin marketplace for CodeTrace R&D. Maintained by Kenny Lam.

## Install (each engineer, once)

In Claude Code:

    /plugin marketplace add <github-org-or-user>/codetrace-claude-plugins
    /plugin install codetrace-dev-skills@codetrace

Skills then appear namespaced, e.g. `codetrace-dev-skills:release-note`.

## Update (whenever a new version is published)

    /plugin update codetrace-dev-skills

## Publishing a new version (maintainer)

1. Edit the skills under `plugins/codetrace-dev-skills/skills/`.
2. Bump `version` in both `plugins/codetrace-dev-skills/.claude-plugin/plugin.json`
   and `.claude-plugin/marketplace.json`.
3. Commit and push. Engineers pick it up with `/plugin update`.

## Contents

- **codetrace-dev-skills v0.2.0** — 16 skills: release pipeline
  (code-validation-test, backward-compatibility-test, release-note,
  deployment-stress-test, installation-builder), architecture guardrails
  (structured-scripting, avoid-cross-over-scripting, software-flexibility,
  thread-assignment), development support (error-handling, data-validation,
  troubleshoot-bug-tracker, configurable-settings, claude-cococom), customer
  deployment (sdk-integration-deploy, license-key).
