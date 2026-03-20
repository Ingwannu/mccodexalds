---
name: decision-logging
description: Record meaningful implementation decisions and tradeoffs so future readers understand why a path was chosen. Use when multiple valid approaches exist, the chosen design is non-obvious, or changes affect architecture, interfaces, data flow, compatibility, safety, or maintenance tradeoffs.
---

# Decision Logging

Use this skill when the code alone will not explain why a specific path was chosen.

## Output

Capture:
- Decision
- Chosen approach
- Alternatives considered
- Constraints and priorities
- Why this won
- Why others lost
- Where the record belongs

## Workflow

1. Name the concrete decision.
2. List only realistic alternatives.
3. State what mattered most in this codebase: correctness, compatibility, safety, speed, maintenance cost, or delivery speed.
4. Explain why the selected option won against those constraints.
5. Explain briefly why the rejected options lost.
6. Record the decision at the right level:
   - inline comment for local constraints,
   - repo-visible notes, PR text, or ADR for broader decisions.

## Guardrails

- Do not document fake alternatives.
- Do not use vague claims like "cleaner" without codebase-specific meaning.
- Do not overload inline comments with system history.
- Do not skip decision history when future readers will need the why.

## Appendix

- Need to persist the result as repo-visible guidance: use `repo-context-hygiene`.
- Need scope and priorities first: use `spec-before-implementation` or `prd-writing`.
