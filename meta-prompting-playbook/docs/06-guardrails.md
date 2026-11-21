# Guardrails

Anything that must hold every time is enforced by the pipeline, not requested in a prompt. A model usually follows a written instruction, but there is no guarantee, so rules with zero exceptions belong in configuration the agent cannot override ([Claude Code docs](https://code.claude.com/docs/en/best-practices)).

## What to enforce

| Rule | Enforced by |
| --- | --- |
| Nothing merges without human approval | Branch protection the agent cannot bypass |
| Design system components and tokens only | Lint rules in CI |
| Agents do not re-record snapshot baselines | Required human owner on the baseline folder |
| No secrets or customer data in code, briefs or tests | Secret scanning in CI; deny rules on the agent |
| Agents stay inside the feature module | Path restrictions on the agent; code owners |
| Unattended runs cannot run away | Caps on turns and spend |
| Every claim of done has evidence | PR template check for command output and screenshots |

The last five rows are my mapping of the principle to a regulated environment. Confirm each mechanism with your platform and security teams.

Keep the enforced list short. Every enforced rule misfires occasionally and needs an owner. Preferences stay in AGENTS.md, where the agent can use judgement.

## Three tiers of boundary

From [Osmani](https://addyosmani.com/blog/good-spec/). These live in AGENTS.md:

- **Always:** things the agent does every time, such as running tests before a PR.
- **Ask first:** things that need a person, such as new dependencies or CI changes.
- **Never:** things with no exceptions, such as committing secrets or removing a failing test.

## Four habits that matter as much as the rules

- **Review the plan, not only the code.** PROMPT.md is the cheapest place to catch a misunderstanding.
- **Separate writer and reviewer.** A fresh context is not swayed by the reasoning that produced the code.
- **Treat the design system as the source of truth.** Figma is sometimes imperfect, so differences get flagged, not copied.
- **Commit the brief and the prompt with the PR.** Reviewers and auditors can see what was asked for.
