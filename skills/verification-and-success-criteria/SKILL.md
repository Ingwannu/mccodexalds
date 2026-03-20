---
name: verification-and-success-criteria
description: Define completion with concrete success criteria and explicit evidence instead of vague claims that a task works. Use when fixing bugs, adding validation, changing behavior, preserving behavior during refactors, or any change where regression risk or proof of completion matters.
---

# Verification and Success Criteria

Use this skill to turn "it should work" into explicit evidence.

## Output

Produce:
- Verifiable goal
- Success criteria
- Verification method
- Before state
- After state
- Limits
- Result

## Workflow

1. Convert the request into an observable goal.
2. Choose the strongest practical verification method:
   - tests,
   - reproduction steps,
   - assertions,
   - before and after behavior,
   - explicit runtime checks.
3. Match the check to the task:
   - bug fix -> reproduce, fix, verify,
   - validation change -> invalid fails, valid still passes,
   - refactor -> behavior preserved,
   - behavior change -> new outcome appears, old unintended outcome does not.
4. State verification limits honestly.
5. Report completion against the criteria, not intuition.

## Guardrails

- Do not declare success without checks.
- Do not imply stronger certainty than the evidence supports.
- Do not hide test or environment limits.

## Appendix

- Need scope and acceptance before coding: use `spec-before-implementation`.
- Need PRD-level test planning: use `prd-writing`.
