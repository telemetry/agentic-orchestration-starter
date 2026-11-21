# Meta prompting in one minute

You write a short brief, the agent writes the detailed build prompt and asks you what it cannot work out, you approve it, and a fresh agent session builds from it. Automated checks, not the agent's opinion, decide when it is done.

## Why it works

- **Long hand-written prompts backfire.** Piling instructions into one prompt makes the model follow each one less reliably, which [Osmani](https://addyosmani.com/blog/good-spec/) calls the curse of instructions.
- **The agent already reads the repo.** It finds conventions, file layout and test setup itself. We only need to write what is not in the code: decisions, scope and what done means ([Claude Code docs](https://code.claude.com/docs/en/best-practices)).
- **A clean start helps.** Building in a fresh session from a written prompt gives the build a clean context and a written definition of done.

## Three lines for the team

- We write the what; the agent writes the how.
- We approve the plan before any code exists.
- Done means the checks pass and the evidence is in the PR.

## The instruction that turns a brief into a meta prompt

See [templates/META_PROMPT_INSTRUCTION.md](../templates/META_PROMPT_INSTRUCTION.md).

## A note on the term

"Meta prompting" is used loosely across the industry. The meaning here, where the agent writes the detailed prompt from your brief, matches the spec-first workflow described by Osmani and in the Claude Code docs.
