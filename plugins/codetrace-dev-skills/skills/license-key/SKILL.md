---
name: license-key
description: >-
  Add license-key protection so software or an SDK can't be used publicly without
  authorization, protecting product ownership. Use when developing a product or
  SDK that will be deployed to a customer and needs usage locked. Triggers on
  "license key", "lock this to a customer", "prevent unauthorized use", "protect
  ownership", "activation". Not always required — apply when the deliverable ships
  externally.
---

# License Key Generation

Not every project needs it, but when software or an SDK is deployed externally,
a license key prevents public/unauthorized use and protects ownership of the
product. This skill designs and generates that locking mechanism.

## When to use this

Use when developing a product, or an SDK for a customer, where usage must be
restricted. If the deliverable stays fully internal, this skill usually doesn't
apply — so confirm the deployment context first.

## Workflow

1. Confirm the deliverable ships externally and genuinely needs locking.
2. Choose what the key binds to (customer, machine, expiry, feature set).
3. Generate keys and implement validation that fails closed — unauthorized or
   tampered keys must block use.
4. Keep the validation resistant to trivial bypass, and document how keys are
   issued.

## Output format

A license-key generation + validation mechanism: how keys are generated, what
they bind to, and the runtime check that gates usage.

## Examples

Input:  The inspection SDK is being shipped to an external integrator.
Output: A per-customer license key with expiry, plus a runtime validation that
        disables the SDK if the key is missing, invalid, or expired.

## Bundled resources

- Applies to deliverables from `sdk-integration-deploy` (#8) and shipped products.
