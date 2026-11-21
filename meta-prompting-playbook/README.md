# Meta prompting playbook

How we take a feature from Figma to a tested PR and on to release using coding agents.

**The idea in one line:** we write the what, the agent writes the how.

You write a short brief. The agent interviews you and writes the detailed build prompt. You approve it. A fresh agent session builds from it. Automated checks, not the agent's opinion, decide when it is done.

## Start here

| If you want to | Read |
| --- | --- |
| Explain the idea to someone in a minute | [docs/01-meta-prompting.md](docs/01-meta-prompting.md) |
| See the whole flow from brief to release | [docs/02-pipeline.md](docs/02-pipeline.md) |
| Set up subagents | [docs/03-subagent-swarms.md](docs/03-subagent-swarms.md) |
| Design the test suite | [docs/04-test-suite.md](docs/04-test-suite.md) |
| Run the whole app every night | [docs/05-nightly-automation.md](docs/05-nightly-automation.md) |
| Know what must be enforced | [docs/06-guardrails.md](docs/06-guardrails.md) |
| Roll this out to a team | [docs/07-rollout.md](docs/07-rollout.md) |
| Check where the advice comes from | [docs/sources.md](docs/sources.md) |

## Use it on a feature

1. Copy [templates/AGENTS.md](templates/AGENTS.md) into your repo root once and fill it in.
2. Copy [templates/BRIEF.md](templates/BRIEF.md) for each feature and fill it in.
3. Paste the instruction in [templates/META_PROMPT_INSTRUCTION.md](templates/META_PROMPT_INSTRUCTION.md) to your agent.
4. Review the `PROMPT.md` it writes, then run it in a fresh session.

A complete worked example for an iOS accounts page is in [examples/accounts-page](examples/accounts-page).

## Repo layout

```
docs/                    The playbook, one topic per file
templates/               AGENTS.md, BRIEF.md and the meta prompt instruction
examples/accounts-page/  A filled-in brief and the build prompt it produces
```

## Status

Version 2, 20 November 2026. Checked against ten published sources. Items marked "my suggestion" in the docs are not sourced and should be confirmed with your platform, QA and security teams before adoption.
