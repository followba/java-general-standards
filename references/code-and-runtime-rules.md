# Code And Runtime Rules

## Scope

Use this reference when reviewing:
- code formatting and readability
- object and value handling rules
- collection usage
- concurrency and locking
- control-flow hygiene

## Code Style

- Use braces for `if/else/for/while/do` blocks even when the body is one line.
- Use 4-space indentation consistently.
- Keep line length controlled and wrap at natural boundaries such as operators, commas, and chained calls.
- Put one space after `//` in line comments.
- Add one space after commas in argument lists and variable declarations.
- Prefer readable boolean or intermediate variables over deeply nested condition expressions.
- Avoid assignment inside other expressions, especially in conditionals.
- Extract long methods instead of letting one method grow without structure.

## Object And Value Rules

- Add `@Override` to every overriding method.
- Access static members through the class, not through an instance.
- Use a constant or known non-null receiver for `equals`, or use `Objects.equals`.
- Compare boxed integers with `equals`, not `==`.
- Match Java field types to database field ranges.
- Represent money in the smallest currency unit with integer types, or use a precise decimal policy consistently.
- Do not construct `BigDecimal` from `double`; prefer `String` or `BigDecimal.valueOf`.
- Use wrapper types for POJO fields and RPC parameters/returns when nullability matters.
- Avoid boolean property names that break framework getter/setter conventions in mapped objects.

## Collection Rules

- Use `isEmpty()` instead of `size() == 0` when checking emptiness.
- When collecting to maps, define duplicate-key behavior explicitly.
- Do not assume `Collectors.toMap()` accepts null values safely.
- Do not cast `subList()` results to concrete list implementations.
- Do not modify collections returned by `Arrays.asList`, `Collections.emptyList`, or similar fixed/immutable views.
- Do not add or remove items inside `foreach`; use `Iterator.remove()` where mutation is required.
- Use typed `toArray(new T[0])` instead of raw `toArray()`.
- Initialize collection capacity when the expected size is known or large.
- Prefer `entrySet()` traversal for key-value iteration.
- Be deliberate about whether `Map` implementations allow `null` keys or values.

## Concurrency Rules

- Do not create raw threads in application code when a thread pool is the intended execution model.
- Prefer `ThreadPoolExecutor` or the project-standard executor setup over convenience factories that hide queue and capacity risk.
- Give threads meaningful names.
- Clean up custom `ThreadLocal` values, especially with pooled threads.
- Keep lock acquisition and release structured so `unlock()` only runs when the current thread actually holds the lock.
- Keep lock order consistent when multiple resources are locked together.
- Do not place risky method calls between `lock()` and the start of the protected `try/finally`.
- Use optimistic locking or version-based updates deliberately when concurrent record updates can conflict.
- Prefer `ScheduledExecutorService` over `Timer` for scheduled concurrent work.

## Control-Flow Rules

- Do not use exceptions for ordinary branching.
- In `switch`, make fall-through explicit and keep `default` present.
- Guard external `String` values against null before switching on them.
- Prefer guard clauses over deep `if/else` nesting when it improves readability.
- Move heavy work out of loops when possible.
- Validate externally controlled parameters at system boundaries and expensive code paths.

## Review Signals

- Methods with dense nested branching and no extracted helpers.
- `Collectors.toMap()` without merge behavior in code that can duplicate keys.
- `Arrays.asList(...).add(...)` or mutation of immutable collection views.
- Direct `new Thread(...)` in application logic.
- `lock()` / `unlock()` patterns that can fail under exceptions.
- Equality checks on boxed values with `==`.
