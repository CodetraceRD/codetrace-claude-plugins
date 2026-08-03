---
name: configurable-settings
description: >-
  Externalize parameters, paths, and settings into a configuration file instead
  of hard-coding them, so end-users can reconfigure the software themselves
  without a developer. Use when building any setting, path, or parameter that
  might change per deployment or per customer. Triggers on "make this
  configurable", "don't hard-code the path", "settings page", "config file",
  "the customer needs to change this".
---

# Configurable Setting File

Parameters, settings, and file paths should not be fixed inside the software. If
they are, every change needs a developer. Instead, surface them on a settings
page and persist them to a config file, so once the product is deployed the
end-user can reconfigure paths and parameters on their own.

## When to use this

Use whenever you're developing a setting or any configurable part — a folder
path, a parameter, a device address, a threshold. If a value might differ
between deployments or customers, it belongs in config, not in code.

## Workflow

1. Identify values that vary by deployment or that a user might need to change
   (paths, parameters, device settings) — these must not be hard-coded.
2. Store them in a configuration file with sensible defaults.
3. Expose them through a settings interface so the user can edit and save.
4. Load from config at runtime, and validate values on load.

## Output format

A configuration file (with defaults) plus the load/save handling, so settings
persist and are user-editable after deployment.

## Examples

Input:  The image-save folder path is hard-coded to a developer's machine.
Output: Path moved into a settings file, editable on the settings page, defaulted
        sensibly and validated on load.

## Bundled resources

- Relevant at deployment time; pairs with `installation-builder` (#2).
