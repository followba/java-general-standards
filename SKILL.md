---
name: java-general-standards
description: Apply general Java coding standards for refactor and code review tasks. Use when requests involve naming, constants, enums, code style, exceptions, logging, unit tests, collections, concurrency, control flow, MySQL/SQL/ORM rules, or general engineering structure in Java projects.
---

# Java General Standards

## Overview

Use this skill for general Java engineering rules that are not specific to one project's layered backend architecture.

This skill is for:
- naming and constants
- code style and runtime rules
- exceptions and logging
- unit testing
- MySQL / SQL / ORM rules
- engineering structure vocabulary

This skill is not for project-specific layering rules such as `Controller -> Service -> BizMapper -> Mapper`. Use `java-backend-standards` for those constraints.

## Workflow

1. Identify which rule domains the task touches.
2. Read only the relevant reference files.
3. Review or refactor code against those rules.
4. Report:
- violations found
- fixes applied
- unresolved tradeoffs or blockers

## Reference Selection

- Naming, constants, enums, magic values:
  `references/naming-and-constants.md`
- Code style, object rules, collections, concurrency, control flow:
  `references/code-and-runtime-rules.md`
- Error codes, exceptions, logging:
  `references/exceptions-and-logging.md`
- Unit test rules:
  `references/unit-testing.md`
- MySQL, SQL, ORM mapping:
  `references/mysql-sql-orm.md`
- Engineering structure vocabulary:
  `references/engineering-structure.md`
- Fast review pass:
  `references/checklist.md`

## Required Checks

- No unclear or misleading names.
- No magic values in business code when constants or enums are appropriate.
- No unsafe collection or concurrency patterns in hot or shared code paths.
- No `System.out`, `System.err`, or `printStackTrace()` in production code.
- Exceptions are not used for normal control flow.
- Error codes are separated from user-facing messages.
- Critical changes include maintainable unit tests.
- SQL avoids unsafe interpolation and avoids `select *`.
- ORM mappings are explicit where field/property conventions differ.

## Output Expectations

When reviewing or refactoring, summarize:
- what is non-compliant
- what was fixed
- what still needs manual judgment
