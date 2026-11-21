# Sub-agent swarms

Set up a small team of specialised subagents under one orchestrator, and start with two or three running in parallel. A large swarm is the wrong starting point for feature work.

## Why stay small

- Anthropic's write-up of its multi-agent system says most coding tasks have fewer parallel parts than research, and that multi-agent is a poor fit when agents need the same context or depend on each other ([Anthropic](https://www.anthropic.com/engineering/multi-agent-research-system)).
- In that system, multi-agent runs used about 15 times the tokens of a chat. Early versions spawned 50 subagents for simple queries until explicit limits were added.
- Osmani's advice is to run parallel agents only on non-overlapping work and to start with two or three ([Osmani](https://addyosmani.com/blog/good-spec/)).
- A subagent does not give a smarter answer than the main agent. It gives parallelism, a clean context, or a reviewer that has not seen how the code was written ([Claude Code docs](https://code.claude.com/docs/en/best-practices)).

## Roles

| Role | Job | Edits code | When |
| --- | --- | --- | --- |
| Planner | Turns the brief into the build prompt and asks questions | No | Once per brief |
| Builder | Owns the checklist and delegates independent pieces | Yes | Once per brief |
| Builder subagents | One each for views, state and view model, tests and fixtures | Own files only | In parallel |
| Verifier | Runs the checks and returns pass or fail with the output | No | After each build pass |
| Reviewer | Compares the diff with the brief in a fresh context | No | Before human review |
| Triage | Reads nightly failures, groups them by cause, opens issues or fix PRs | Fix PRs only | Nightly |

## Handoffs

Every handoff to a subagent needs four things:

1. An objective
2. An output format
3. Which tools and sources to use
4. Clear task boundaries

Anthropic found vague handoffs caused duplicated and misread work.

Tell the reviewer to report gaps that affect correctness and to skip style. A reviewer asked to find problems always finds something, and fixing every finding adds needless layers.

## Setting this up on Amp

Amp's docs describe the building blocks ([Amp](https://ampcode.com/docs/models-and-subagents)):

- **Task** is the general-purpose subagent. It does delegated work end to end and reports back. Use it for builder subagents.
- **Oracle** reviews code and advises on hard decisions and never edits files. Use it as the reviewer.
- **Finder** searches the workspace and returns files and line ranges.
- You can ask Amp to split independent work across several subagents.
- Plugins can define custom subagents, which is where a verifier or design system reviewer would live.

Limits to design around: each subagent has its own context, starts only with what the main agent gives it, cannot talk to other subagents, and returns only a final summary. So the handoff text is the whole interface.

## Swarm rules

- One writer per file. Parallel builders get separate files or separate worktrees.
- Reviewer and verifier are read-only.
- Agents return evidence: the command run and its output, or the screenshot.
- Cap fix attempts per failure. Three is my suggestion as a starting number, not a sourced one.
- Get the single-agent flow working on one screen before adding parallel builders.

## Open question

I did not find documentation on running Amp unattended in CI. Confirm that with Amp before designing the nightly triage agent around it.
