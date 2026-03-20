---
name: repo-context-hygiene
description: Keep important project knowledge durable, repository-visible, and reusable instead of leaving it in chat history or temporary session context. Use when work depends on project-specific context, repeated explanations should become durable docs, or guidance needs to be placed in the right home such as AGENTS.md, skills, guides, ADRs, or task specs.
---

# Repository Context Hygiene

Use this skill to decide what knowledge should become durable project memory and where it should live.

## Output

Produce a short placement decision:
- Missing context
- Why it matters
- Durable or temporary
- Best repository-visible home
- Action
- Follow-up needed

## Workflow

1. Identify the context currently trapped in chat, memory, or scattered tools.
2. Decide whether it is durable enough to preserve.
3. Choose the right home:
   - `AGENTS.md` for always-on global rules,
   - skills for repeatable workflow guidance,
   - guides for recurring project knowledge,
   - ADRs for major decisions,
   - specs or task docs for work-specific requirements.
4. Keep default instructions compact and split by concern.
5. Update stale guidance instead of layering new guidance on top.

## Guardrails

- Do not treat chat history as durable documentation.
- Do not dump every rule into `AGENTS.md`.
- Do not preserve low-value temporary chatter.
- Do not leave repeated explanations undocumented.

## Appendix

- Need a compact DB, API, page, or workflow guide: use `domain-context-template`.
- Need to record why a choice was made: use `decision-logging`.
