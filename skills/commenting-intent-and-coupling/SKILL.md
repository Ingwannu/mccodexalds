---
name: commenting-intent-and-coupling
description: Write or review comments that explain intent, constraints, and coupling instead of restating visible behavior. Use when editing non-trivial comments, touching fragile or misleading code, preserving intent comments, or deciding whether a comment belongs inline versus in higher-level documentation.
---

# Commenting Intent and Coupling

Use this skill when a future reader could misread code structure without explanation.

## Output

For each substantial comment, make sure it answers:
- Why is this here?
- What is it coupled to?
- What role does it serve?
- What constraint makes this shape necessary?

## Workflow

1. Decide whether a comment is needed at all.
2. If needed, explain intent rather than visible behavior.
3. State coupling, ordering, invariants, protocol assumptions, or compatibility constraints when they are not obvious from code alone.
4. Preserve valid intent comments during edits.
5. Update or remove stale comments immediately.

## Guardrails

- Do not narrate what the code already says.
- Do not use comments to excuse code that should be simplified.
- Do not push system-level design history into tiny inline comments.
- Keep comments sparse, specific, and high-signal.

## Appendix

- Need broader design history: use `decision-logging`.
- Need to decide whether the knowledge belongs in docs instead: use `repo-context-hygiene`.
