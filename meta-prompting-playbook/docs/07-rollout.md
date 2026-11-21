# Rollout plan

Roll out in four stages, and do not add parallel subagents until one squad has shipped a screen with the single-agent flow.

## Stages

| Stage | What happens | Done when |
| --- | --- | --- |
| 1. Foundations | Write AGENTS.md; map the most-used design system components with Code Connect; stand up the PR check suite | An agent can build, lint and test with one command each |
| 2. Pilot | One iOS squad and one Android squad deliver the accounts page from a brief | Both PRs merge with evidence attached |
| 3. Teach | 45-minute session for all squads using the pilot as the demo | Every squad has written one real brief |
| 4. Scale | Add builder subagents, the reviewer and the nightly triage agent | Nightly run is green and trusted for two weeks |

## The 45-minute session

| Time | What happens |
| --- | --- |
| 5 min | The idea: we write the what, the agent writes the how |
| 10 min | Demo: the accounts page brief, the interview, the PROMPT.md that comes back |
| 15 min | In pairs, write a brief for a feature you are working on now |
| 10 min | Two pairs show their prompts; the group spots what the brief missed |
| 5 min | Agree the template and where briefs live |

## First steps

- [ ] Draft AGENTS.md for the iOS repo with the exact build, lint and test commands
- [ ] Check Code Connect coverage for SwiftUI and Compose components
- [ ] Pick the pilot squads
- [ ] Start the journey inventory with product owners
- [ ] Agree the PR and nightly check lists with QA
- [ ] Confirm with Amp how to run agents unattended in CI

## Open questions

- Which snapshot tool and pinned simulator set do we standardise on?
- Who owns snapshot baseline approvals?
- What attempt cap and spend cap apply to unattended runs?
- Where does the nightly run execute, and how many shards can it have?
