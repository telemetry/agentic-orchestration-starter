# The meta prompt instruction

Paste this to the planner agent once BRIEF.md and AGENTS.md exist.

```markdown
Read BRIEF.md and AGENTS.md. Do not write code.
Interview me until you could write the build prompt for this brief.
Then write PROMPT.md with: ordered steps, the files each step touches,
the exact command to run after each step, the boundaries, and a list
of anything in the brief that is still ambiguous.
```

Then:

1. Answer its questions.
2. Review PROMPT.md: the order of work, the files touched, the tests promised.
3. Start a fresh agent session and tell it to run PROMPT.md.

## Review instruction

Paste this to a reviewer subagent before human review.

```markdown
You are reviewing code you did not write. Compare the diff with BRIEF.md.
Check every definition-of-done line is implemented and has a test.
Report only gaps that affect correctness. Skip style.
```
