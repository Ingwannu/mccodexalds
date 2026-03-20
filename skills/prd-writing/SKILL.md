---
name: prd-writing
description: Draft or refine compact, execution-ready PRDs for medium or large work. Use when adding features, making broad behavioral changes, or standardizing implementation requests into repository-visible documents with goal, non-goals, priorities, dependencies, risks, and tests.
---

# PRD Writing

Use this skill to turn a feature idea or broad change into a compact PRD before implementation starts.

## Output

Write a PRD that includes:
- Title
- Goal
- Non-goals
- Must-have
- Should-have
- Nice-to-have
- Current context
- UX or behavior notes
- Dependencies and reuse
- Implementation plan
- Risks
- Tests and verification

Use the template in `references/prd-template.md` when you need a starting structure.

## Workflow

1. Build context from the current implementation and repository-visible docs.
2. State Goal and Non-goals clearly.
3. Split scope into Must-have, Should-have, and Nice-to-have.
4. Describe the intended UX or behavioral change.
5. Check existing code, APIs, data, and workflows before proposing new paths.
6. Record dependencies, migration concerns, and operational risks.
7. Write a short implementation plan.
8. Define tests and verification before coding.
9. Review the draft and correct any facts that came from weak assumptions.

## Guardrails

- Do not skip the PRD for medium or large work.
- Do not let optional ideas blur the Must-have scope.
- Do not write the PRD as only a feature wishlist.
- If facts are missing, mark them explicitly.

## Appendix

- Need a lighter pre-coding checklist instead of a full PRD: use `spec-before-implementation`.
- Need to persist design rationale: use `decision-logging`.
- Need compact domain docs to support the PRD: use `domain-context-template`.
