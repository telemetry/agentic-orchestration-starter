---
name: verifying-with-bite-checks
description: Verifies native builds using shared rule vectors, deliberate mutation bite checks, architecture audits, and visual inspection across Light, Dark, and Large Text modes. Use before declaring any feature or screen complete.
---

# Verifying With Bite Checks

Passing tests alone do not prove correctness. Prove the suite catches real regressions and inspect real rendered outputs.

## Workflow

1. **Shared Rule Vectors:** Capture key formatting, boundary, empty, error, and session rules in a platform-neutral `rules.json` vector list and bind both iOS and Android tests to every rule ID (fail loudly if any rule is unbound).
2. **Mutation "Bite Checks":** Temporarily inject 4 realistic single-line bugs into production code one at a time (e.g. wrong `$0.00` sign styling, rounding/scale mismatch, broken error mapping, missing accessibility label). Confirm each break fails the test suite, revert cleanly, and re-run green.
3. **Architecture & Boundary Guard:** Run repository architecture/module-boundary checks and a read-only skeptic review verifying zero peer-feature imports or data-layer leakage into UI.
4. **Visual Proof Matrix:** Render Light, Dark, and Max Accessibility Text (`AX3` / `200%`) states on real simulator/emulator targets (via local runner or laptop when running Orb-first), inspect every capture visually, and report any unverified checks honestly.
