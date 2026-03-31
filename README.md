# java-general-standards

`java-general-standards` is a reusable skill for reviewing and refactoring Java code against general engineering standards.

Chinese documentation: [README.zh-CN.md](./README.zh-CN.md)

## What It Covers

This skill focuses on general Java standards that are broadly reusable across projects:

1. naming, constants, enums, and magic-value control
2. code style, object/value handling, collections, concurrency, and control flow
3. exceptions, error-code boundaries, and logging rules
4. unit testing expectations and review signals
5. MySQL, SQL, and ORM mapping constraints
6. engineering structure vocabulary and documentation signals

It is intentionally separate from project-specific layered backend rules. If a repository also needs strict layering constraints such as `Controller -> Service -> BizMapper -> Mapper`, pair this skill with `java-backend-standards`.

## Repository Layout

```text
.
├── SKILL.md
├── README.md
├── README.zh-CN.md
├── agents/
│   └── openai.yaml
└── references/
    ├── checklist.md
    ├── code-and-runtime-rules.md
    ├── engineering-structure.md
    ├── exceptions-and-logging.md
    ├── mysql-sql-orm.md
    ├── naming-and-constants.md
    └── unit-testing.md
```

## Included References

- `references/naming-and-constants.md`: naming, enums, constants, magic-value guidance
- `references/code-and-runtime-rules.md`: style, object/value rules, collections, concurrency, control flow
- `references/exceptions-and-logging.md`: error-code boundaries, exception handling, logging rules
- `references/unit-testing.md`: unit-test expectations and review signals
- `references/mysql-sql-orm.md`: MySQL, SQL, and ORM mapping guidance
- `references/engineering-structure.md`: model/layer vocabulary, documentation and design-review signals
- `references/checklist.md`: flat review checklist for quick passes

## Usage

Install or copy this skill into your Codex skills directory, or distribute it through your internal skill workflow.

Use it when the task is about general Java engineering quality rather than project-specific backend layering.
