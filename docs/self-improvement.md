# Self-improvement

When corrected or when something new is learned during a session, persist the lesson so it doesn't repeat. Don't just acknowledge and move on — update the system.

## Where to persist

| What happened | Update |
|---------------|--------|
| Corrected on how to file something | `docs/filing.md` |
| A skill instruction was ambiguous or caused wrong behavior | The skill's `SKILL.md` |
| Learned a new user preference or convention | `AGENTS.md` or the relevant doc |
| Discovered a better tool or command for a task | The skill that uses it |
| Encountered a new edge case in a workflow | The skill's guidelines section |
| Doesn't fit an existing file | Use `/memory` to log it |

## Guidelines

- Fix the source, not the symptom. If a skill caused wrong behavior, fix the skill — don't just remember to work around it.
- Keep changes minimal and scoped. Don't rewrite a whole doc to add one rule.
- If unsure whether a correction is general or one-off, ask before persisting.
