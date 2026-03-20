---
name: pr-guide
description: Prepare repository-visible implementation handoffs for pull requests, reviews, or task completion. Use when summarizing what changed, why it changed, what decisions were made, what risks remain, and how the result was verified.
---

# PR Guide

Use this skill to prepare a compact handoff for review or future readers.

## Output

Produce a repository-visible summary with:
- What changed
- Why it changed
- Scope boundaries
- Key decisions
- Risks and follow-ups
- Verification performed
- Docs updated

Use the template in `references/pr-template.md` when you need a starting point.

## Workflow

1. Read the PRD, spec, or task notes first.
2. Summarize the behavior change, not just the diff.
3. Record why the change exists.
4. Record any non-obvious decisions or rejected alternatives.
5. State verification clearly, including limits.
6. Link any updated docs, guides, or follow-up work.

## Guardrails

- Do not dump raw diff details without explaining behavior.
- Do not omit risks, limitations, or follow-up work.
- Do not claim stronger verification than was actually performed.
- Do not leave review context trapped only in chat.

## Appendix

- Need to create the spec first: use `spec-before-implementation` or `prd-writing`.
- Need to capture the design tradeoff in more detail: use `decision-logging`.
