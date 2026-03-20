When invoking subagents, use GPT-5.4 high by default. Do not use Mini unless there is an explicit reason to optimize for speed or cost.

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

## Operating Model

- Keep always-on guidance compact. If this file grows past roughly 200 lines or mixes unrelated concerns, split it.
- Put repeatable workflow guidance in skills.
- Put durable project facts in repository-visible docs.
- Treat chat-only context as a documentation gap.
- Prefer a compact primary guide and read appendices or deeper references only when needed.
- When work is done, rely on repository-visible artifacts rather than session memory.

## 0. Core Operating Rules

- Do not assume silently.
- State important assumptions explicitly.
- If multiple interpretations are possible, present them explicitly instead of choosing one without notice.
- If something materially affects correctness and is ambiguous, stop and surface the ambiguity before proceeding.
- If ambiguity is minor and does not materially affect correctness, state the assumption and proceed.

## 1. Reuse Before Creating

- Before writing new code, first check whether an existing function, type, module, workflow, or API already serves the purpose.
- Prefer extending an existing implementation safely over introducing a new one.
- Do not create parallel logic when the current codebase already has an established path.

## 2. Simplicity First

- Write the minimum code necessary to solve the requested problem.
- Do not add features beyond what was requested.
- Do not introduce abstractions for single-use code.
- Do not add configurability or flexibility that was not requested.
- Do not add defensive handling for unrealistic execution paths.
- If a simpler solution achieves the same result with no loss of clarity, prefer it.

Ask: would a senior engineer consider this overcomplicated? If yes, simplify it.

## 3. Surgical Changes

- Touch only what is necessary to complete the requested task correctly.
- Do not refactor unrelated code.
- Do not modify adjacent code, comments, or formatting unless required.
- Match the existing style unless there is a direct reason not to.
- If your change makes imports, variables, or functions newly unused, remove those.
- Do not remove unrelated pre-existing dead code unless explicitly asked.

Every changed line should trace directly to the task.

## 4. Comments

- Do not write comments that merely restate obvious behavior.
- Write comments when intent, constraints, tradeoffs, or coupling would not be obvious from the code alone.
- For any substantial comment, clearly state:
  - why the code exists,
  - what other code it relates to,
  - what role it serves.
- If code is unusual, fragile, non-idiomatic, or more complex than expected, explain why it must remain that way.
- Preserve valid intent comments when modifying code.
- Update or remove comments that become inaccurate.

## 5. Scope Discipline

- Do not silently expand scope.
- Solve the must-have requirement first.
- If an optional improvement seems useful, call it out separately instead of bundling it into the change.

## 6. Goal-Driven Execution

- Define success criteria before implementing.
- Convert vague tasks into verifiable outcomes.
- Prefer checks that can be validated directly: tests, reproduction steps, assertions, or before/after behavior.
- For multi-step work, state a brief plan and verify each step.

Examples:
- "Fix the bug" -> reproduce it, change the code, verify the reproduction no longer fails.
- "Add validation" -> add checks for invalid input and verify the expected failure path.
- "Refactor X" -> preserve behavior and verify before/after results.

## 7. Repository Memory

- Record why, decision rationale, and Must / Should / Nice priority when future work depends on them.
- If the same explanation is repeated across sessions, create or update a repository-visible artifact instead of repeating it in chat.
- If a rule applies only to a specific workflow, move it out of AGENTS.md into a skill or guide.
- Update stale docs when behavior changes.
- Do not rely on chat history as durable project memory.

## 8. Skill Routing

Use the smallest set of skill documents that fully covers the task. Do not duplicate skill-specific procedures in this file.

Event-based routing:
- Before medium or large work, or when the request is underspecified: use `prd-writing` and then `spec-before-implementation`.
- When the task involves meaningful tradeoffs or a non-obvious path: use `decision-logging`.
- When work depends on project memory, repeated domain knowledge, or documentation placement: use `repo-context-hygiene` and, if needed, `domain-context-template`.
- When writing, updating, or reviewing non-trivial comments: use `commenting-intent-and-coupling`.
- For bug fixes, hotfixes, narrow patches, or other high-risk scoped edits: use `minimal-surgical-change` and `verification-and-success-criteria`.
- Before handoff, PR preparation, or repository-visible implementation summary: use `pr-guide`.

If multiple skills apply, use the smallest set that fully covers the task.
