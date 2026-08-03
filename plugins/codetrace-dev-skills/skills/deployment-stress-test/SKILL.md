---
name: deployment-stress-test
description: >-
  Stress test and memory-leak check the complete software before it goes to
  production, to reduce the chance of downtime on the production line. Use once
  development is complete and the software is ready to deploy — before the
  installer ships. Triggers on "stress test", "memory leak", "soak test",
  "is this ready for production", "pre-deployment check", "long-run test".
---

# Deployment Stress & Memory Test

Software that passes functional tests can still fail in production after hours
of continuous running — memory leaks, resource exhaustion, and degradation under
load only show up under stress. Because CodeTrace software runs on production
lines where downtime is costly, every deployment must first survive a stress and
memory check.

## When to use this

Use once the software is complete in development and before deploying to
production. This runs after the release pipeline's functional gates
(code-validation-test, backward-compatibility-test) and before the installer is
handed to the customer.

## Workflow

1. Define the stress scenario from real production usage: continuous operation
   over an extended period, peak load (e.g. maximum inspection rate, all
   cameras/communication channels active), and repeated start/stop cycles.
2. Run the software under that load while monitoring memory usage over time —
   steadily climbing memory that never returns is a leak, even if nothing
   crashes yet.
3. Also watch handles, threads, CPU, and disk usage for the same creeping
   growth, and check behavior when resources run low.
4. Investigate and fix every leak or degradation found, then re-run the test
   until the profile is flat and stable.
5. Record the result (duration tested, load applied, memory profile, issues
   found and fixed) so the release has evidence it was stress-tested.

## Output format

A stress-test result: test duration and load description, memory/resource
profile over time, list of leaks or failures found and their fixes, and a final
verdict — close to no bugs and no memory leak — before deployment proceeds.

## Examples

Input:  Vision inspection software is ready to deploy to the production line.
Output: 24-hour continuous run at full inspection rate — memory flat after fix
        to image-buffer release; verdict PASS, cleared for deployment.

## Bundled resources

- Runs before `installation-builder` (#2) ships the final installer; complements
  the functional gates `code-validation-test` (#3) and
  `backward-compatibility-test` (#11).
