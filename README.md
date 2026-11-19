# Agentic Orchestration Starter Kit (Steps, Prompts & Skills)

A minimal, portable starter repository for running end-to-end **Figma / Spec → Verified Native iOS & Android + Executive Docs** workflows inside **Amp Orbs**.

```diagram
┌─────────────┐     ┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│ 1. SKILLS   │ ──▶ │ 2. PLAN     │ ──▶ │ 3. GATE     │ ──▶ │ 4. THE APP  │
│ Recipe cards│     │ 4-role test │     │ Human "go"  │     │ iOS+Android │
└─────────────┘     └─────────────┘     └─────────────┘     └─────────────┘
```

## Quick Start (3 Minutes)

1. **Install the 4 skills globally (optional — works across all Orbs & repos):**
   ```sh
   for s in .agents/skills/*; do amp skill add --global "$s"; done
   ```
2. **Start with the Meta-Prompt (`prompts/01-meta-prompt.md`):** Paste your rough goal + links into an Amp Orb so the agent audits your sources, finds blind spots, and writes the Spec, Phased Plan, and downstream Orb prompts *before* touching code.
3. **Run Concurrent Orbs:**
   - **Track B (Year in Review / Executive Summary):** `prompts/02-year-in-review-orb.md`
   - **Track A (iOS + Android Feature):** `prompts/03-ios-orb.md` + `prompts/04-android-orb.md`
4. **Prove Tests Catch Bugs:** Run `prompts/05-bite-check.md` to inject deliberate 1-line breaks and verify every check fails loudly before reverting green.

## What's Inside

| Path | What It Does |
|---|---|
| `STEPS.md` | The 6-step end-to-end delivery loop in plain English |
| `prompts/` | Copy-paste prompts for Meta-Prompting, Cloud Orbs, Bite Checks & Live Steers |
| `.agents/skills/` | 4 composable skills that hand off artifacts from intake → plan → build → PR |
| `assets/` | Minimal NIO-style schematic (`01-skill-chain.png` & `01-skill-chain-animated.html`) |

## Skill Chain

1. `orchestrating-delivery` — Master 6-phase conductor (`Gather → Plan → Approve → Build → Verify → Close`)
2. `mapping-figma-to-native` — Extracts Figma nodes & maps tokens/components (`Supported / Ambiguous / Missing / Provisional`)
3. `verifying-with-bite-checks` — Shared rules vectors, 4-mutation bite checks, and Light/Dark/Large-Text visual proof
4. `handing-over-pr` — Compiles `Summary.md`, verification evidence, and clean PR checklist
