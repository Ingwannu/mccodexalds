---
name: spec-before-implementation
description: Turn medium or ambiguous implementation requests into a small execution spec before coding. Use when work is underspecified, spans multiple files or subsystems, changes APIs, schemas, workflows, or data flow, or carries hidden tradeoffs and missing requirements.
---

# Specification Before Implementation

Use this skill to convert a non-trivial request into a compact execution spec before code is written.

## Output

Produce a short spec with:
- Goal
- Non-goals
- Must-have
- Should-have
- Nice-to-have
- Reuse candidates
- Constraints and dependencies
- Acceptance criteria
- Risks and open questions
- Plan

## Workflow

1. Restate the task as a concrete implementation target.
2. Separate desired outcome from guessed implementation.
3. Check whether existing code, workflows, or APIs already satisfy the need.
4. Split scope into Must-have, Should-have, and Nice-to-have.
5. Record constraints, dependencies, and assumptions that affect correctness.
6. Define acceptance criteria in observable terms.
7. Stop and surface missing information if it materially affects correctness.
8. Keep the final plan short and verifiable.

## Guardrails

- Do not start non-trivial implementation from a vague request.
- Do not mix required scope with optional improvements.
- Do not create a new path before checking reuse.
- If uncertainty is minor, state the assumption and proceed.
- If uncertainty is material, stop and surface it.

## Appendix

- Need a full feature workflow or PRD: use `prd-writing`.
- Need tradeoff history: use `decision-logging`.
- Need explicit validation planning: use `verification-and-success-criteria`.
