---
name: code-plan
description: Create a plan for a code change through structured Q&A. Clarifies behavior, captures decisions and acceptance criteria. Use when starting a new feature or change that needs a clear plan before implementation.
---

Create a plan for a code change through a structured dialogue.

## Stages

Work through these stages in order. Get explicit approval before moving to the next.

### 1. Clarify

Ask clarifying questions **one-by-one** to understand:
- What the feature/change does from the user's perspective
- Expected behavior and edge cases
- Inputs, outputs, error cases
- What's in scope and what's not

### 2. Approach

Once behavior is clear, discuss how it should be built:
- Architecture and key abstractions
- Where it fits in the existing codebase
- Trade-offs between approaches
- What the acceptance criteria are

Don't specify types, interfaces, or implementation details — those are the agent's job during implementation. Focus on decisions and constraints.

### 3. Write the plan

With both stages approved, write the plan:

- Capture the key decisions made during discussion
- List acceptance criteria — what must be true when this is done
- Include any constraints or boundaries ("must not", "always", "never")
- Note which docs need updating as part of this change
- Keep it short — a page max. If it's longer, the scope is too big; split it.

**Where to save:**
- If the user specifies a path, use that
- Otherwise, save to `plan.md` in the project root

Plans are ephemeral. They're work orders, not permanent documentation. After implementation, they can be discarded.

## Re-thinking the plan

If a path is getting messy or may cause future issues, bring it to the user's attention — the plan may need revision before continuing.
