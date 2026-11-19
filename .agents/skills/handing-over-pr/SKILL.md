---
name: handing-over-pr
description: Compiles a concise handover summary, attaches verification evidence, strips temporary scratch artifacts, and drafts a reviewable pull request. Use when wrapping up a verified feature slice for team review.
---

# Handing Over a PR

Produce a concise, verifiable handover for reviewers who have not read the diff.

## Workflow

1. **Compile `Summary.md` (Untracked in `.amp/in/<slice>/`):** Record before/after customer behaviour, acceptance-criterion results, key decisions, exact verification commands/counts, and any unverified gaps. Never claim blocked or skipped checks passed.
2. **Evidence Hygiene:** Ensure no tokens, credentials, customer data, or git-ignored `.amp/in/` dumps are staged or committed.
3. **Draft PR Description:** Keep it short: Why (ticket link), What Changed (up to 3 user-visible bullets), How to Verify (commands + visual proof), and Risks/Rollout.
4. **Approval Gate:** Present the title, target branch, summary, and reviewer list and wait for explicit user authorization before committing, pushing, or opening the PR.
