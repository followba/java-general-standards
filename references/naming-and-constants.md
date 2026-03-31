# Naming And Constants

## Scope

Use this reference when reviewing:
- class, method, field, and package naming
- constant and enum naming
- magic values in business code
- role and suffix conventions in Java models and services

## Rules

- Use clear English names. Avoid mixed pinyin and English unless the domain term is already stable.
- Do not start or end identifiers with underscores or dollar signs.
- Class names use `UpperCamelCase`.
- Methods, parameters, fields, and local variables use `lowerCamelCase`.
- Package names use lowercase and should stay semantically simple.
- Constants use uppercase with underscores and should express complete meaning.
- Prefer longer but precise names over short names that hide meaning.
- Abstract classes should use `Abstract` or `Base` prefixes when that clarifies intent.
- Exception classes should end with `Exception`.
- Test classes should end with `Test`.
- Service implementation classes may use `Impl` when the codebase already separates interface and implementation explicitly.
- Enum classes should end with `Enum` when the project uses that convention consistently.
- Enum members should be uppercase with underscores.
- Interface names should express capability or role directly instead of carrying redundant prefixes.
- Avoid non-standard abbreviations that reduce readability.
- Do not use raw status strings or raw numeric business state values in business flow.
- Boolean-like persistence fields and Java boolean properties must follow the framework conventions used by the codebase consistently.
- Prefer enums for bounded state sets and constants for thresholds, default values, and reusable keys.
- Avoid broad "all constants in one file" designs when the codebase already groups constants by domain.
- Group constants by reuse scope: cross-app, app-wide, module, package, or class-local.
- Use uppercase `L` for long literals.
- Use domain model suffixes consistently when the project distinguishes `DO`, `DTO`, `BO`, and `VO`.

## Review Signals

- Misleading abbreviations that weaken readability.
- Business semantics hidden behind `0`, `1`, `"Y"`, `"N"`, `"PENDING"` style literals.
- Duplicate constants with slightly different meanings.
- Names that leak transport or storage concerns into business concepts.
- Parameter names or local variables that shadow fields in a way that hurts readability.
