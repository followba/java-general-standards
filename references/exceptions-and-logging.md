# Exceptions And Logging

## Scope

Use this reference when reviewing:
- error code design
- exception handling boundaries
- logging APIs and message shape

## Error Codes

- Error codes should be stable, easy to compare, and easy to communicate.
- Error codes are not user-facing text.
- Error codes should not encode version numbers or log levels.
- User prompts, error messages, stack traces, and error codes have different responsibilities and should stay separate.
- A short source-oriented scheme is preferable to an overfitted code taxonomy. One practical pattern is:
  - `A` for caller or user-side errors
  - `B` for current-system business or execution errors
  - `C` for third-party dependency errors
- Reuse existing error codes where the semantics already match instead of inventing near-duplicates.

## Exception Rules

- Do not use exceptions for normal control flow.
- Do not catch broad exceptions unless the boundary truly requires it.
- Catch exceptions in order to handle them. If you do not handle them, rethrow them.
- Do not swallow exceptions silently.
- Prefer business-meaningful exception types over `RuntimeException`, `Exception`, or `Throwable` in normal application code.
- Stable code and risky code should not share one broad `try/catch` block without reason.
- Top-level application boundaries should convert internal exceptions into stable outward responses.
- Boundary layers should take responsibility for converting failures into the contract that layer exposes.
- Resource cleanup should use `try-with-resources` where possible.
- Do not `return` from `finally`.
- When rollback depends on a caught exception, make the rollback behavior explicit.
- Null-safety is still the caller's responsibility even if a callee often returns empty objects or collections.

## Logging Rules

- Use a logging facade such as SLF4J instead of binding directly to a concrete logging implementation in business code.
- Use parameterized logging instead of string concatenation.
- Avoid repeated logging of the same failure across multiple layers on the same host.
- Production code should not use `System.out`, `System.err`, or `printStackTrace()`.
- Error logs should preserve incident context and stack trace.
- Do not serialize whole objects to JSON for logging without understanding getter side effects and payload cost.
- Choose log levels deliberately: `error` for real failures, `warn` for notable but recoverable issues, `info` selectively, `debug` sparingly.
- Guard expensive `debug` or `trace` log argument computation in hot paths when the logging framework will not short-circuit that work.

## Review Signals

- `catch (Exception e)` in non-boundary code.
- `catch` blocks that only log and continue without a clear recovery path.
- `printStackTrace()` or console output in production paths.
- Logs built with `+` concatenation inside hot paths.
- Error codes leaking directly into front-end responses as the only user explanation.
- Boundary APIs that throw raw implementation exceptions without translation.
