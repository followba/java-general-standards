# Design And Architecture

## Scope

Use this reference when reviewing:
- architecture and design documentation quality
- schema or data-structure changes
- state-heavy business objects
- multi-object interaction flows
- non-functional requirement capture

This file is about design-review signals and documentation expectations, not project-specific layering rules.

## Core Expectations

- Storage schemes and core data structures should be reviewed before rollout when they materially affect long-term system cost or risk.
- Design documentation should capture boundaries, module relationships, inputs/outputs, and non-functional requirements where the change is large enough to justify it.
- Agile delivery is not a reason to skip all design artifacts; the goal is to remove waste, not to remove thinking.

## When Extra Design Artifacts Are Justified

- If an object has more than a few meaningful states, document the state model and transitions explicitly.
- If a feature involves a deeper collaboration chain across multiple components, document the interaction sequence explicitly.
- If schema, storage, indexing, or long-lived data migration is involved, document the data-structure decisions explicitly.
- If the model space becomes large or dependency-heavy, document the model relationships clearly enough for future maintainers.

## Design Principles

- Isolate change points instead of letting them leak everywhere.
- Prefer composition over inheritance unless substitution is clearly valid.
- Keep classes close to a single responsibility.
- Depend on abstractions where extension, replacement, or decoupling is a real maintenance concern.
- Extract shared behavior and shared configuration instead of repeating the same logic across modules.

## Documentation Signals

- Design docs should explain why the chosen structure is acceptable, not just what classes were added.
- The codebase should retain enough documentation for later maintenance, refactoring, and incident response.
- Code is part of the documentation surface, but it is not enough to explain deep call chains, state transitions, or non-functional tradeoffs.

## Review Signals

- Schema changes with no durable reasoning about indexing, cardinality, or lifecycle.
- Stateful workflows with no explicit transition model.
- Multi-component flows with no sequence-level explanation.
- Large design changes described only in code diffs with no architectural summary.
- Repeated logic that should have been extracted into shared modules or abstractions.
