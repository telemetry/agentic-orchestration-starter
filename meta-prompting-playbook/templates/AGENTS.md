# AGENTS.md

<!-- Written once per repo. Keep it to what the agent cannot find by reading the code. -->

## Commands
- Build: <exact command with flags>
- Lint, including design system rules: <exact command>
- Unit tests, one file: <exact command>
- Snapshot tests: <exact command>
- UI tests, one journey: <exact command>
- Full PR check suite: <exact command>

## Conventions
- <State management and architecture rules, with one real code example>
- <Design system: components and tokens only>

## Testing rules
- Query UI elements by accessibility identifier, never by visible label
- Wait for elements to exist; never use fixed sleeps
- Launch a fresh app per UI test in test mode: test user, seeded data, mocked network
- One page object per screen
- One accessibility audit per screen state

## Git
- <Branch naming, commit format, PR template>

## Boundaries
- Always: run lint and tests before opening a PR; attach command output
- Ask first: new dependencies, CI config changes, changes outside the
  feature module, any new design system component
- Never: commit secrets, use real customer data, re-record snapshot
  baselines, skip or delete a failing test
