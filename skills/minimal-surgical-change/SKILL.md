---
name: minimal-surgical-change
description: Keep bug fixes, hotfixes, and narrow high-risk edits tightly scoped and directly traceable to the requested task. Use when applying a bug fix, patch, hotfix, or other bounded production change where extra refactoring would raise risk or expand scope.
---

# Minimal Surgical Change

Use this skill for bug fixes, hotfixes, and narrow patches where scope creep raises risk.

## Output

Summarize the change with:
- Requested change
- Smallest affected area
- Existing path reused
- Out-of-scope areas left untouched
- Newly-unused code removed
- Verification

## Workflow

1. Define the exact behavior change.
2. Find the smallest viable edit point in the existing path.
3. Keep surrounding code untouched unless correctness requires otherwise.
4. Match local structure and style.
5. Remove only leftovers created by your own change.
6. Verify that every modified area maps directly to the task.

## Guardrails

- Do not sneak in refactors during a narrow fix.
- Do not introduce a parallel path when the existing path should be patched.
- Do not change formatting, comments, or adjacent code without need.
- Do not remove unrelated pre-existing dead code.

## Appendix

- Need explicit regression checks: use `verification-and-success-criteria`.
- Need to capture a non-obvious patch rationale: use `decision-logging`.
