# TDD implementation prompt

## Phase 1: Understand

Before writing any code, thoroughly read the entire spec — every section, every edge case, every type definition. If the spec references other files, read those too. Do not skim. Do not skip sections.

Then read the existing codebase carefully. Understand the project structure, existing patterns, naming conventions, and dependencies already in use. Build a complete mental model of what exists before you change anything.

If anything in the codebase is fundamentally incompatible with the spec and cannot be reconciled, abort and explain why. Do not guess or improvise around contradictions.

## Phase 2: Test-driven implementation

Start by writing end-to-end tests and major behavioral tests that verify the spec's expected behavior. These tests must fail initially — they define what correct looks like before any implementation exists.

Then implement incrementally, running tests frequently. For each piece of functionality:

1. Write or identify the failing test that covers it.
2. Write the minimal implementation to make it pass.
3. Refactor if needed, ensuring all tests still pass.

Be thorough. Every behavior described in the spec must have a corresponding test. Every edge case. Every error condition. Do not move on from a section until its tests pass and you are confident the implementation is correct.

Do not cut corners. Do not skip tests for "simple" code. Do not leave placeholder implementations.

## Phase 3: Verify

Once implementation is complete, go back to the spec and read it again — thoroughly, from top to bottom. For every described behavior, confirm:

1. The behavior is implemented correctly.
2. There is at least one test that exercises it.
3. The test actually verifies the correct outcome, not just that code runs without error.

Check for gaps methodically. Walk through every section of the spec and cross-reference against your tests and implementation. If you find anything missing — even something small — implement and test it before finishing.

Finally, run the full test suite. Every test must pass. Do not skip this step. Do not assume tests pass — run them and verify.
