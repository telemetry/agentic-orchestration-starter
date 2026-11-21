# Nightly whole-app automation

Run every critical journey, every snapshot and every accessibility audit against the main branch each night, sharded across parallel simulators, with an agent triaging failures into issues and fix PRs before the team starts work.

## How to set it up

1. **Build a journey inventory.** List the critical user journeys per domain: a customer goal plus the steps to reach it. Each journey has one automated test and a named owner. Product owners help write this list. Google recommends documenting these journeys and verifying them end to end ([Google Testing Blog](https://testing.googleblog.com/2021/06/how-much-testing-is-enough.html)).
2. **Make the app deterministic.** The nightly run launches the app in test mode with a seeded test user and mocked network and payments. Real network calls and leaked state are the second and third most common causes of flaky UI tests, after timing ([Bitrise](https://bitrise.io/guides/xcuitest)).
3. **Build once, run many.** Build for testing once, then hand the same build to every shard and simulator ([Sentry](https://docs.sentry.io/platforms/apple/guides/ios/snapshots/)).
4. **Shard across simulators.** Bitrise cites a 30-minute serial UI suite dropping to 8 to 10 minutes on four parallel simulators. Size the shard count so the whole run finishes well before the working day.
5. **Use simulators for breadth and devices for depth.** Run most tests on simulators. Run a critical subset on real devices on a slower cadence, since devices catch hardware-specific problems but cost more.
6. **Quarantine flaky tests.** Detect tests that pass and fail on the same commit, move them out of the main pipeline, and fix them as a priority. A flaky nightly run trains people to ignore red.
7. **Let an agent triage.** A triage agent reads the results, groups failures by likely cause, and opens an issue with logs and failing screenshots. For clear regressions it opens a fix PR for human review.
8. **Send one morning report.** Pass rate, new failures by domain, tests quarantined, fix PRs waiting for review.

## Before any agent runs unattended

Answer five questions for it ([Claude Code docs](https://code.claude.com/docs/en/best-practices)):

- Does it know what done looks like?
- Can it check its own work?
- What is it allowed to touch?
- What stops it: a cap on turns or spend?
- Where does the result go, and who signs off?

## My suggestions, not from a source

- Add a small separate suite that runs against a real test environment, so mocked journeys do not hide API contract drift.
- Run the suite against the next OS beta as a non-blocking job, so OS changes surface early.
- Do not use automatic retries to turn a red run green. Retries hide flakiness that quarantine would expose.
- Android runs the same nightly shape with its own tools; the journey inventory is shared across both platforms.
