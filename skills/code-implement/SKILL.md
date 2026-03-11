---
name: code-implement
description: TDD implementation from a plan. Writes all tests first, then implements until they pass, then reviews against acceptance criteria.
---

Implement functionality from a plan through TDD.

## Steps

### 1. Review the plan

Read the plan being implemented. Understand the full scope — decisions, acceptance criteria, constraints — before writing any code. If no plan exists, suggest running `/code-plan` first.

Read any referenced documentation (architecture docs, behavioral specs) for orientation.

### 2. Write all tests

Write tests that cover the plan's acceptance criteria before writing any implementation code.

- Test names should map to acceptance criteria so failures are traceable
- Layer tests by type (unit, integration, e2e) where appropriate for the project
- Tests must rigorously exercise real code paths — no shortcuts
- Reasonable mocks only where necessary (external services, I/O)
- Test observable outcomes, not internal mechanics

### 3. Implement

Write code to pass the tests. Iterate until all tests pass.

- Refer to any code style documentation and enforcement rules (lints, structural tests)
- Adhere to the style and organization of existing code
- Re-use existing techniques, functions, types where practical
- Keep it simple — the simplest implementation that satisfies the acceptance criteria
- If the plan specifies types, interfaces, or other implementation details, follow them

### 4. Review against plan

Once all tests pass, review the implementation:

- Walk through every acceptance criterion — is it met?
- Are edge cases handled?
- Is anything missing or extra?
- Review project docs — do any need updating to reflect this change?

Flag any issues found and fix them before considering the work done.

### 5. Run enforcement

Run all lints, structural tests, and CI checks. Fix any violations. The enforcement layer catches architectural mistakes that the plan doesn't specify — import boundaries, complexity limits, naming conventions.

## When the plan is wrong

If implementation reveals a plan issue — stop and flag it. Do not work around it. The plan needs to be revised first.
