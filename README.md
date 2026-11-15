# SmarterTogether

An open learning system for coding, DSA, debugging, and software engineering. It helps learners reason and implement for themselves instead of receiving a finished solution by default.

## What it does

| Capability | Command | Learning behavior |
| --- | --- | --- |
| Progressive hints | `/hint [0-5]` | One graduated clue at a time; starts with a prediction when there is no attempt. |
| Socratic teaching | `/teach` or `/coach` | One focused question, then waits for the learner. |
| Concept lessons | `/explain` | Concept → mental model → mechanics → example → code → pitfalls → transfer check. |
| DSA foundations | `/foundations` or `/toolkit` | Maps prerequisites without spoiling the original exercise. |
| Applied practice | `/challenge [topic] [difficulty]` | Creates a realistic, answer-free scenario. |
| Collaborative design | `/together [task]` or `/involve` | Works through material design and planning decisions with you, one checkpoint at a time. |
| Guided feature scaffolding | `/code [feature]` | Clarifies requirements, researches current practices, plans the feature, and creates empty file/function scaffolds when file access exists. |
| Learning review | `/review` | Identifies one evidence-backed, highest-leverage issue. |
| Evidence-led debugging | `/debug` | Tests one hypothesis with one small diagnostic step. |

The shared prompt also includes `/quiz`, `/reflect`, and `/reveal`. `/reveal` is the only deliberate mode that may provide a complete solution for the current task.

`/together` is read-only and keeps a decision log, inviting the learner to weigh alternatives before assembling the final design. `/code` can use that agreed design to scaffold.

`/code` is the only protected mode allowed to create scaffold files. It describes responsibilities and signatures while leaving implementation to the learner. If the assistant cannot write files, it returns copyable per-file skeletons. It asks blocking questions before making a plan; nonblocking assumptions are stated. Use `/teach`, `/hint`, `/review`, or `/debug` as you implement.

## Hint ladder

`/hint` is not a disguised solution generator. It uses six controlled levels:

| Level | Purpose |
| --- | --- |
| 0 | Ask for a prediction or tiny trace. |
| 1 | Focus attention on one constraint or behavior. |
| 2 | Name one relevant concept. |
| 3 | Explore one relationship, invariant, or decision rule. |
| 4 | Identify one incomplete local checkpoint. |
| 5 | Give one small local unblock that cannot finish the task alone. |

The mentor moves up only after the learner shows an attempt or evidence. `/reveal` is separate; it is not “hint level 6.”

## Use it

### ChatGPT Custom GPT

This is the best public ChatGPT route. In the GPT editor, paste [chatgpt-custom-gpt-instructions.md](chatgpt-custom-gpt-instructions.md) into **Instructions** (not the full master prompt; Custom GPT Instructions has a size limit). Enable only the capabilities you want; **Actions are not required**. Add the provided conversation starters, test the GPT, then choose the public sharing option available to your account.

### ChatGPT, Codex, Gemini, or Claude chat

Copy [master-system-prompt.md](prompts/master-system-prompt.md) into a project, Gem, custom instruction surface, or the first message of a new chat. This works as a portable fallback, but it does not install native skills or plugins.

### Claude skills

Download the individual ZIP packages from [dist/claude](dist/claude) and import them wherever your Claude account exposes skill import. Platform availability differs by plan and region; the prompt fallback above always works.

### Source skills

The individual skill sources are under [skills](skills). The individual ZIPs in `dist/claude/` are built from the nine source skills. A GitHub release must be created separately.

Check your platform’s current publishing instructions before distributing new skill packages.

## Examples

```text
/hint I am solving this array problem. I tried nested loops and it times out.
/teach Here is my retry handler and the duplicate-message bug I see: ...
/explain idempotency keys in TypeScript
/foundations [paste an unsolved DSA exercise]
/challenge event-driven architecture intermediate
/together Design the end-to-end order confirmation workflow with me.
/code Add an event-driven fulfillment flow to my .NET service. Here is the repo and the behavior I need: ...
/debug Expected one email; actual behavior is three emails. Here are the logs: ...
```

## Repository layout

```text
prompts/
  master-system-prompt.md              # Canonical full prompt
chatgpt-custom-gpt-instructions.md     # Compact Custom GPT instructions
skills/                                # Canonical portable skill packages
dist/claude/                           # Individual skill ZIP release assets
evals/behavior-cases.md                # Manual behavior and leakage checks
docs/                                  # Blueprint, privacy, terms
```

## Contributing and releasing

The canonical behavior starts in [master-system-prompt.md](prompts/master-system-prompt.md) and the nine folders under [skills](skills). When behavior changes:

1. Update the master prompt and the affected canonical skill package(s).
2. Update the Custom GPT version so it preserves the same learning contract within its field limit.
3. Run the cases in [behavior-cases.md](evals/behavior-cases.md).
4. When ready to release, regenerate the distributable ZIP assets and publish a new release.

**Release status:** The source prompt and skill tree include `/code` and `/together`, with matching skill ZIPs in `dist/claude/`. Create a GitHub release to publish a new version. Update any existing Custom GPT manually with the compact instructions.

Do not silently weaken the anti-spoiler contract. Release notes should call out changes to `/reveal`, hint levels, or answer-leakage protections.

## License

[MIT](LICENSE)
