# The test suite

Build the suite as a pyramid: many fast unit tests, a solid integration layer, and end-to-end tests reserved for critical user journeys. That shape is Google's long-standing guidance, which also warns against trading integration tests for more end-to-end tests ([Google Testing Blog](https://testing.googleblog.com/2021/06/how-much-testing-is-enough.html)).

## Layers

| Layer | What it proves | How to do it well | On every PR |
| --- | --- | --- | --- |
| Static | It builds; only design system components and tokens are used | Lint rules for the design system run in CI, not only in the prompt | Yes |
| Unit | State, logic and formatting are correct | Fake or mock external dependencies | Yes |
| Integration | A feature module works with its neighbours | Small groups of units against faked network | Yes, changed modules |
| Snapshot | Every state looks right and has not drifted | Pin simulator model, OS and Xcode; keep snapshot tests in their own test plan | Changed screens |
| UI journey | A customer can complete a critical journey | See the four rules below | This feature's journeys |
| Accessibility | Labels, contrast and Dynamic Type hold up | Run the built-in audit on each screen state | This screen |
| Performance | Launch and scroll stay in budget | Small tests early catch regressions sooner | No, nightly |

## Four rules for UI journey tests that do not flake

From [Bitrise](https://bitrise.io/guides/xcuitest):

- Query elements by accessibility identifier, never by visible label.
- Wait for elements to exist. Fixed sleeps are the leading cause of flaky tests.
- Launch a fresh app per test in a test mode: test user, seeded data, mocked network and payments.
- Wrap each screen in a page object so a UI change means one edit.

Put these four rules in AGENTS.md so agent-written tests follow them from the start.

## Snapshots

The pinning advice comes from [Sentry's snapshot guide](https://docs.sentry.io/platforms/apple/guides/ios/snapshots/), which also suggests generating snapshots from SwiftUI previews so every preview becomes a test.

Agents never re-record a baseline to get to green. Baseline changes need a human approval.

## Accessibility

Apple's audit runs the same checks as Accessibility Inspector and fails the test automatically, but it only covers what is on screen. Each state needs its own audit call ([Apple, WWDC23](https://developer.apple.com/videos/play/wwdc2023/10035/)).

## Coverage

Track two numbers instead of one overall percentage:

- Coverage of changed lines per PR
- The share of critical journeys that have an automated test

## Android

The same layers apply with Jetpack Compose and its test tools. The journey inventory is shared across both platforms.
