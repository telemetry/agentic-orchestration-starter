# The 6-Step Agentic Delivery Loop

1. **Step 0 · Start With a Meta-Prompt (`prompts/01-meta-prompt.md`)**
   Ask an Orb to audit your links, surface hidden blockers, draft the Spec + Phased Plan, and generate clean execution prompts before touching code.
2. **Step 1 · Parallel Discovery (`orchestrating-delivery` + `mapping-figma-to-native`)**
   Run Read-Only PM, Designer, and Systems Engineer subagents in parallel to collect specs and map Figma designs against your real Design System tokens (`Supported / Ambiguous / Missing / Provisional`).
3. **Step 2 · 4-Role Adversarial Critique & Gate 1**
   Have PM, Designer, Lead Engineer, and QA critique `DraftBuildPlan.md` in parallel. Fix issues in the blueprint, then **stop for human `"go"`** before writing production code.
4. **Step 3 · Design System & Domain Lock**
   Build approved missing tokens/components first and lock pure domain models/interfaces before parallel feature coding starts.
5. **Step 4 · Disjoint Parallel Build**
   Give Data and UI coding subagents non-overlapping directories. Only the Lead Orchestrator edits project manifests, navigation wiring, or build files.
6. **Step 5 · Bite Checks, Visual Proof & Handover (`verifying-with-bite-checks` + `handing-over-pr`)**
   Inject deliberate 1-line bugs to prove tests catch regressions, inspect Light/Dark/Large-Text renders on both iOS and Android, and compile `Summary.md` before asking to commit/PR.
