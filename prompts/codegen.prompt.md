## Setup

1. Read the task file path provided in the Blade Run invocation argument. Treat that file as the source of implementation requirements.
2. Read `docs/` thoroughly for project context (architecture, protocol, state, UI).
3. Explore the existing codebase and tests before writing changes. Follow established structure and conventions.
4. If the task file is missing, ambiguous, or conflicts with existing docs/contracts, stop and report the issue clearly.

## Implementation

5. Write tests first (TDD). Tests should cover the behavior described in the provided task file.
6. Implement until all tests pass. Run tests with `npm test`.
7. Follow existing patterns and conventions found in the codebase.
8. Iterate: if tests fail, fix the implementation, not the tests (unless the test is wrong).

## Review

9. Re-read the provided task file. Verify every required behavior is implemented.
10. Re-read `docs/`. Verify your implementation adheres to the architectural decisions and behavioral contracts described there.
11. If anything is missing or contradicts the docs, fix it.

## Finish

12. Commit your work to the current branch with a clear commit message summarizing what was implemented.
13. Print a concise completion note including: what changed, test/lint results, and any follow-up items.
