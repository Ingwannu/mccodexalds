# McCodexalds

[한국어 README](./README.md)

This repository is an example of translating the ideas from the Yozm article [How We Standardized Vibe Coding for a Product Team with Claude Code (aka the McDonald's System)](https://yozm.wishket.com/magazine/detail/3457/) into a reusable Codex structure built around `AGENTS.md` and `skills/`.

The goal is simple. Instead of dumping a large amount of context into the AI at once, this repository separates context into a short always-on operating guide and small skill documents that are only loaded when needed.

## Problems This Repository Tries to Solve

The article repeatedly points to a similar set of problems:

- As projects grow, context overload increases and the AI starts hallucinating or producing odd implementations.
- Intent that exists only in chat is ephemeral, so it becomes hard to trace why something was built that way.
- Even when an existing implementation or API could be reused, the AI may create a parallel path and introduce duplicate logic.
- If rules keep being appended forever, a single rule file becomes bloated and consumes too much context before the work even starts.
- Non-developers or new contributors still end up asking humans for the current state and intent.

This repository tries to reduce those problems with a few principles:

- Keep the always-read guide short and explicit.
- Split repeatable workflows into separate skill documents.
- Store important intent, decisions, and priorities in the repository instead of chat.
- Limit context usage by loading only the documents needed for the current task.

## How System Prompting and Skills Are Split

In this repository, the file that plays the "system prompt role" is [`AGENTS.md`](./AGENTS.md) at the project root.

The split is:

- [`AGENTS.md`](./AGENTS.md): shared operating rules that should always apply. This includes explicit assumptions, reuse-first behavior, simplicity, surgical changes, comment rules, scope control, and success criteria.
- [`skills/`](./skills/): small task manuals that are only read in specific situations. These cover workflows such as writing PRDs, preparing a spec before implementation, recording decisions, and defining verification criteria.

This follows the article's strategy of using a compact core guide plus deeper references only when needed. Instead of putting every rule into one giant file, the repository keeps the core operating rules in `AGENTS.md` and routes detailed execution steps through skills.

## How It Works

The execution flow is:

1. The agent reads [`AGENTS.md`](./AGENTS.md) first to establish baseline operating rules.
2. It chooses only the skills that match the current task.
3. It reads the selected `SKILL.md` files and follows their inputs, outputs, workflow, and guardrails.
4. It writes the result back into repository-visible code or documentation.
5. When the session ends, the important intent and process still remain in the repository for future work.

The point is not to build an AI that "knows everything," but an AI that loads the right manual at the right time.

## Included Skills and Their Roles

The included skills were selected to support the same goal: split a large rule file into smaller task-specific documents, and keep intent and process inside the repository.

- [`skills/commenting-intent-and-coupling`](./skills/commenting-intent-and-coupling/): captures why code exists and what constraints or coupling matter, instead of restating obvious behavior.
- [`skills/decision-logging`](./skills/decision-logging/): records why a path was chosen among multiple valid options.
- [`skills/domain-context-template`](./skills/domain-context-template/): turns repeated explanations about DBs, APIs, pages, or workflows into compact repository-visible guides.
- [`skills/minimal-surgical-change`](./skills/minimal-surgical-change/): keeps bug fixes and hotfixes narrowly scoped.
- [`skills/pr-guide`](./skills/pr-guide/): captures what changed, why it changed, what risks remain, and how the result was verified.
- [`skills/prd-writing`](./skills/prd-writing/): structures feature work around goal, non-goals, priorities, risks, and verification before implementation.
- [`skills/repo-context-hygiene`](./skills/repo-context-hygiene/): promotes repeated chat explanations into durable repository-visible artifacts.
- [`skills/spec-before-implementation`](./skills/spec-before-implementation/): turns ambiguous work into a short execution spec before coding begins.
- [`skills/verification-and-success-criteria`](./skills/verification-and-success-criteria/): replaces vague confidence with observable success criteria and explicit checks.

## Routing in This Repository

The `Skill Routing` section in [`AGENTS.md`](./AGENTS.md) determines which skills should be loaded in which situations.

For example:

- medium or underspecified work -> `prd-writing` then `spec-before-implementation`
- non-obvious tradeoffs -> `decision-logging`
- repeated project knowledge -> `repo-context-hygiene`, and `domain-context-template` when needed
- bug fixes or narrow patches -> `minimal-surgical-change` and `verification-and-success-criteria`
- handoff or final repository-visible summary -> `pr-guide`

So `AGENTS.md` acts as the router for when to load something, and each skill acts as the manual for how to work once that situation is identified.

## Mapping the Article to This Repository

The connection between the article's concerns and this repository looks like this:

- giant rule file problem -> short [`AGENTS.md`](./AGENTS.md) + split `skills/`
- disappearing intent -> PRDs, decision logs, PR guides, and domain guides stored in the repository
- duplicate implementations -> `Reuse Before Creating` and `spec-before-implementation`
- scope blow-up -> `Simplicity First`, `Scope Discipline`, and `minimal-surgical-change`
- unverified optimism -> `Goal-Driven Execution` and `verification-and-success-criteria`

## Repository Structure

```text
mccodexalds/
├─ AGENTS.md
├─ README.md
├─ README.en.md
└─ skills/
   ├─ commenting-intent-and-coupling/
   ├─ decision-logging/
   ├─ domain-context-template/
   ├─ minimal-surgical-change/
   ├─ pr-guide/
   ├─ prd-writing/
   ├─ repo-context-hygiene/
   ├─ spec-before-implementation/
   └─ verification-and-success-criteria/
```

## One-Line Summary

This repository is a base for experimenting with a workflow that standardizes team intent and process through a short always-on guide plus situation-specific skill documents, instead of trying to teach the AI everything at once.
