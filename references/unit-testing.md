# Unit Testing

## Scope

Use this reference when reviewing:
- whether a change needs tests
- whether unit tests are maintainable
- whether test setup respects isolation

## Core Principles

- Good unit tests follow AIR:
  - Automatic
  - Independent
  - Repeatable
- Prefer BCDE coverage thinking for important logic:
  - Border
  - Correct
  - Design
  - Error
- Tests should be non-interactive and should use assertions rather than console inspection.
- Tests must not depend on execution order.
- Tests should avoid dependency on external networks, services, and mutable shared environments.
- Critical or central business changes should include or update unit tests.
- Unit tests belong in test directories, not production source directories.
- Use mocks, fakes, or in-memory implementations where dependency injection makes them practical.

## Design Guidance

- Prefer constructor or dependency injection so dependencies can be mocked or replaced.
- Keep test granularity small enough to localize failures.
- Refactor code that is hard to test instead of writing fragile tests around it.
- For database-related tests, prepare data through code or fixtures that respect business rules.
- Avoid leaking dirty data from tests into shared environments.
- Decide unit-test scope during design or review for important modules instead of bolting tests on after release pressure starts.
- Coverage numbers can guide effort, but maintainability and defect-localization matter more than raw percentages.

## Review Signals

- New business logic with no tests.
- Tests that call each other or rely on order.
- Tests that require manual inspection of output.
- Tests that hit real external services without an explicit reason.
- Tests that only cover the happy path but ignore boundary and error cases.
- Tests placed in production source trees.
