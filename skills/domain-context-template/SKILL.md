---
name: domain-context-template
description: Capture compact repository-visible domain guides for repeated DB, API, page, or workflow context. Use when the same project facts must be re-explained, when chat-only context causes confusion, or when a task needs a concise guide with appendices instead of a bloated global rule file.
---

# Domain Context Template

Use this skill to create compact guides for project knowledge that is reused often.

## Output

Create one compact guide per concern, such as:
- DB structure guide
- API surface guide
- Page or route guide
- Workflow guide

Use the template in `references/domain-guide-template.md` as a starting point.

## Workflow

1. Identify the context that is being repeated or rediscovered.
2. Split by concern instead of mixing DB, API, page, and workflow rules in one file.
3. Write a compact primary guide with:
   - what this area is,
   - the facts another agent needs first,
   - key constraints,
   - where deeper references live.
4. Separate facts, conventions, and open questions.
5. Add appendices or references only when they reduce repeated rediscovery.

## Guardrails

- Do not put domain guides into `AGENTS.md`.
- Do not create one giant catch-all guide.
- Do not mix stable facts with temporary guesses.
- Do not duplicate the same explanation across multiple files without need.

## Appendix

- Need help deciding where the guide belongs: use `repo-context-hygiene`.
- Need a task-specific spec using this context: use `spec-before-implementation` or `prd-writing`.
