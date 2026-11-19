---
name: orchestrating-delivery
description: Coordinates end-to-end feature delivery across parallel read-only discovery, multi-role critique, human Gate 1 approval, disjoint build lanes, and handover. Use when orchestrating a multi-step spec, feature slice, or cross-platform delivery in an Orb or local repo.
---

# Orchestrating Delivery

Run a structured 6-phase loop (`Gather -> Plan -> Approve -> Build -> Verify -> Close`) with clear human gates and non-overlapping subagent scopes.

## Workflow

1. **Hygiene (Phase 0):** Confirm clean branch/worktree, verify toolchain access, and create an ignored working directory (`.amp/in/<slice>/`) for temporary specs, design bundles, and plans.
2. **Parallel Read-Only Discovery (Phase 1):** Spawn independent read-only `Task` subagents in parallel:
   - **PM:** Reconciles ticket acceptance criteria, specs, and edge/error states.
   - **Designer:** Runs `mapping-figma-to-native` to classify Design System coverage.
   - **Systems Engineer:** Audits existing APIs, state boundaries, and architecture constraints.
3. **Plan & Adversarial Critique (Phase 2):** Synthesize `.amp/in/<slice>/DraftBuildPlan.md` and create a live Amp Artifact with `{{dropdown:Todo|*Doing:blue|Done:green}}` phase chips. Have PM, Designer, Engineer, and QA critique the plan in parallel, fold fixes in, and **stop for human `"go"` at Gate 1** before writing production code.
4. **Foundation & Contract Lock (Phase 3):** Build approved missing Design System tokens/components first, then lock pure Domain contracts/interfaces before parallel feature work.
5. **Disjoint Parallel Build (Phase 4):** Run Data and UI subagents concurrently in strictly disjoint directories. Keep shared manifests, app composition, and build-system runs solely with the Lead Orchestrator.
6. **Verify & Handover (Phase 5–6):** Hand off to `verifying-with-bite-checks` and `handing-over-pr`. Ask explicitly before committing, pushing, or opening a PR.
