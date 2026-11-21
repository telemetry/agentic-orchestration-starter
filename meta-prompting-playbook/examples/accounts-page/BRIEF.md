# Brief: Accounts page (iOS)

## Goal
A signed-in customer sees all their accounts with current balances on
one screen and can open any account. Success: every state in the design
is built from design system components and covered by tests, in one PR.

## Spec
- Design: <Figma link>; frames Accounts / Default, Loading, Empty,
  Error, Offline
- Content: accounts grouped by type; each row shows account name,
  masked number and balance; a total per group
- Interactions: pull to refresh; tap a row to route to account detail
- Data: <accounts API contract>; fixtures in <path>
- Module: <feature module path>
- Out of scope: the account detail screen, any API change

## Definition of done
- Unit tests cover every state transition and balance formatting
- Snapshot tests cover every state in light and dark, at default and
  largest Dynamic Type, on the pinned small and large simulators
- One UI journey test: launch, load, refresh, tap through to detail
- Accessibility audit passes on every state
- Design system lint passes with zero violations
- PR lists each line above with the command run and its output
- The journey is added to the nightly suite

## Boundaries for this feature
- Ask first: if Figma and the design system disagree (the design
  system wins; list the differences in the PR)
- Ask first: if a needed component has no Code Connect mapping
