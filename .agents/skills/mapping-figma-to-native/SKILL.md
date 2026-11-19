---
name: mapping-figma-to-native
description: Extracts Figma design context and classifies every visual element, token, and component against native iOS and Android design systems before coding. Use when turning Figma screens into native SwiftUI or Jetpack Compose plans and code.
---

# Mapping Figma to Native

Treat Figma and the live native Design System as paired sources of truth. Never invent colours, spacing, copy, or platform-inappropriate chrome.

## Workflow

1. **Confirm the Target:** Require an explicit Figma frame URL and node ID (never guess a frame).
2. **Retrieve Evidence:** Fetch node context, variable bindings, and a reference render into git-ignored `.amp/in/<slice>/figma/` without logging tokens.
3. **Classify Every Element:** Map each UI element against the target repository's Design System into four buckets:
   - **Supported:** Exact existing component/token symbol.
   - **Ambiguous:** Competing mappings or missing semantic definition.
   - **Missing:** Absent token, icon, or component requiring a Design System addition first.
   - **Provisional:** Temporary approximation awaiting design sign-off.
4. **Enforce Platform Separation:** Treat iOS and Android as equal citizens. Translate iOS navigation chrome, symbols, and marks to native Material/Compose equivalents on Android (and vice versa) — never cross-pollinate Apple and Google assets.
5. **Audit Accessibility & States:** Specify Light, Dark, narrow width (`320pt`/`320dp`), Max Dynamic Type (`AX3` / `200%`), empty, loading, and error states in `DraftBuildPlan.md` before Gate 1 approval.
