# Build prompt: Accounts page (iOS)

<!-- This is the meta prompt: what the planner agent writes from BRIEF.md. -->

## Context
You are building one SwiftUI screen in <feature module path>.
Read first: BRIEF.md, AGENTS.md, and <two existing screens that show
the house pattern>. Use the Figma MCP server for the five frames named
in the brief. Use only components that have a Code Connect mapping.

## Answers from the interview
- Group order: <answer>
- Hidden-balance behaviour: <answer>
- Refresh failure with stale data: <answer>

## Steps
1. Inventory. List every component, token and state in the frames and
   map each to a design system component. Write it to INVENTORY.md.
   Check: no unmapped items. If any, stop and ask.
2. State model. Define the screen states and view model against the
   fixtures. Files: <paths>.
   Check: <unit test command> passes.
3. Views. Build each state from the inventory. Files: <paths>.
   Check: <build command> and <lint command> pass with zero violations.
4. Tests. Unit tests for transitions and formatting; snapshot tests
   for each state in the matrix from the brief; one UI journey test
   using accessibility identifiers and a page object; an accessibility
   audit per state. Files: <paths>.
   Check: each test command passes.
5. Full check. Run the complete PR check suite.
6. PR. Open a PR using the template.

## Delegation
Steps 2, 3 and 4 touch different files. After step 1, give each to a
subagent with: the objective, the files it owns, the check command,
and the inventory. No subagent edits another's files.

## Verification loop
After each step run its check. On failure, read the output, fix, and
re-run. After three failed attempts on the same check, stop and report.
Before the PR, have a reviewer subagent compare the diff with BRIEF.md
and report gaps that affect correctness. Skip style.

## Boundaries
As AGENTS.md, plus the two ask-first items in the brief.

## PR must contain
- Each definition-of-done line with the command run and its output
- Screenshots of every state, light and dark
- Differences found between Figma and the design system
- Anything not done, and why

## Still ambiguous
- <Questions the interview did not settle>
