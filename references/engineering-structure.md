# Engineering Structure

## Scope

Use this reference when a task needs shared vocabulary for Java backend model roles or common application layering.

This file is intentionally generic. Project-specific layering rules belong in project-specific skills, and broader architecture-review guidance belongs in `design-and-architecture.md`.

## Common Model Terms

- `DO` / `PO`: persistence-facing data objects mapped closely to storage models
- `DTO`: transport objects between internal layers or services
- `BO`: business objects that package domain behavior or business-oriented state
- `VO`: presentation or response-facing view objects
- `Query`: request objects used for searches or filters, especially when parameter count grows

## Common Layer Terms

- `Web` / `Controller`: request entry, validation, response shaping
- `Service`: business orchestration and transactional coordination
- `Manager`: reusable cross-domain orchestration or third-party integration layer, if the project uses it
- `DAO` / `Mapper`: persistence access

## Structural Guidance

- Keep terminology consistent within one repository.
- Do not overload one type to play multiple roles without a clear reason.
- Query objects are preferable to loose maps when filter shape is non-trivial.
- DTOs and VOs should be separated when API-facing needs differ from internal transport needs.
- Prefer composition or aggregation over inheritance unless substitution is truly valid.
- Follow single-responsibility pressure early, before one class becomes the fallback home for unrelated behavior.
- Rely on interfaces or abstractions where the codebase benefits from extensibility and replacement.

## Documentation And Comment Rules

- Public classes, methods, and abstract methods should have meaningful API-facing documentation when the codebase expects Javadoc-style comments.
- Enum members should be documented when their meaning is not obvious from the name alone.
- Keep comments synchronized with code changes.
- Good naming and structure reduce comment burden; comments should explain intent or constraints, not restate obvious code.
- Delete dead code rather than leaving large commented blocks without clear reason and timestamp.
- Code is not a complete substitute for architecture or design documentation.

## Review Signals

- One class used as DB model, transport model, and response model without an explicit reason.
- Generic `Map` inputs replacing typed query objects.
- Unclear naming where `DTO`, `VO`, and `DO` are used inconsistently.
- Public API shapes with no durable documentation in a codebase that relies on Javadoc.
- Large commented-out blocks with no explanation.
