# MySQL SQL And ORM

## Scope

Use this reference when reviewing:
- table and column design
- index and query patterns
- SQL safety and maintainability
- ORM mapping rules

## Table And Column Rules

- Table names and column names should use lowercase letters, digits, and underscores.
- Avoid plural table names when the codebase treats tables as single-entity concepts.
- Boolean-like database fields should follow the project's established convention consistently.
- When the project uses `is_xxx` fields in storage, keep ORM mappings explicit so Java property names stay coherent.
- Required audit columns such as create/update timestamps should be updated consistently when the project expects them.
- Use `decimal` for precise numeric values such as money.
- Avoid oversized varchar usage when text/blob-style storage is the real data shape.
- Index names and key names should follow a predictable prefix convention when the repo uses one.

## Index And Query Rules

- Unique business identifiers should be protected by unique indexes.
- Avoid joins across too many tables unless justified and measured.
- Avoid left-like full wildcard search patterns on indexed columns.
- Prefer indexes that match filter and order patterns.
- Avoid implicit type conversion that invalidates indexes.
- Large `IN` lists should be reviewed carefully.
- Prefix indexes on large varchar columns should be chosen intentionally rather than indexing the full field blindly.
- Prefer composite index ordering that matches the actual equality/range/order pattern.

## SQL Rules

- Prefer `count(*)` for row count semantics.
- Handle `sum()` nullability deliberately.
- If pagination `count` is zero, return early instead of executing the page query.
- Do not rely on foreign keys or cascades if the target architecture expects application-managed relationships.
- Do not use `select *` in application queries.
- Multi-table queries should qualify columns with aliases.
- Use parameter binding rather than string interpolation.
- Review data-fix SQL with a `select` first before destructive updates or deletes.
- Avoid stored procedures when the target architecture values code portability, reviewability, and application-layer ownership.

## ORM Mapping Rules

- Prefer explicit field selection and explicit mappings when conventions do not align exactly.
- Use `resultMap`-style explicit mappings where field and property naming rules diverge.
- Do not use `${}` style interpolation in SQL XML templates for normal query parameters.
- Do not return raw `HashMap` or loosely typed maps as query results when typed models are expected.
- Update modified-time fields consistently on updates when the project uses them.
- Avoid large catch-all update statements that write unchanged fields by default.

## Review Signals

- `select *`
- `${}` in mapper XML
- ambiguous multi-table columns
- hand-built SQL with string concatenation
- pagination code that always runs both `count` and `page` queries
- raw map-based result handling instead of typed models
- SQL or ORM code that silently loses index usage through type mismatch
