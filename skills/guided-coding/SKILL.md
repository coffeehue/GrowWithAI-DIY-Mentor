---
name: guided-code-scaffolding
description: Plan and scaffold a real software feature while leaving implementation to the learner. Use when they start with /code or explicitly ask for a researched implementation plan, project file structure, and empty typed function skeletons they can fill in.
---

# Guided code scaffolding

Treat `/code` as a special learning mode: plan the architecture and create only the minimum compilable declarations and empty or throwing bodies. Do not implement business behavior or solve the learner's active task. This mode permits scaffold file edits; other protected learning modes remain read-only. `/reveal` is the only full-answer unlock.

1. Inspect the repository first: conventions, similar features, language/framework versions, tests, interfaces, and existing contracts. In chat without files, request a tree or examples only when necessary.
2. Extract observable behavior, success/failure criteria, dependencies, integration and trust boundaries. Group and ask blocking questions before finalizing a plan or creating files; wait for answers. Label nonblocking assumptions and proceed. Never invent critical requirements. If choices are delegated, decide and explain.
3. With web access, verify version-sensitive practices in official docs. For complex unfamiliar workflows, consult maintainers' examples, specifications, or other reliable primary sources, and cite the useful findings. If browsing is unavailable, say so and use repository evidence. Follow existing conventions; apply SOLID, DRY, KISS, readable naming, testability, and relevant reliability/security concerns proportionately, without extra architecture for its own sake.
4. Produce a reviewable plan: confirmed scope and assumptions; key design choices with reasons/trade-offs; path-by-path map (`new`/`existing`, responsibility); named interfaces/functions with signatures; learner-owned implementation order; and meaningful acceptance checks. Describe responsibilities, never a full algorithm or completed bodies.
5. If agent file tools exist, create the minimal planned scaffolds without waiting for a second permission request. Preserve existing behavior and user edits. Do not wire incomplete methods into live startup, routes, migrations, or production workflows. If touching an existing file would be unsafe, show its insertion point and signature instead. Where a body is required, use an explicit not-implemented throw in the correct language. Do not write solved tests or fake return values. State clearly that invoking stubs fails until implemented.
6. Without file tools, provide a path map and separate copyable skeleton for each proposed file; distinguish proposed from created. Close with the first function to implement and one targeted design/behavior question. Continue with `/teach`, `/hint`, `/review`, or `/debug` as the learner works.

For small features, prefer extending a few existing files. For an event-driven flow, surface only the boundaries actually needed by the requirements (message contract, publisher/consumer integration, failure and duplicate handling where relevant). Keep contracts explicit and implementations empty.
