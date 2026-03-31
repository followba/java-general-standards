# Security

## Scope

Use this reference when reviewing Java application code that:
- handles user input
- renders user-visible data
- performs redirects
- exposes account- or tenant-scoped data
- uses platform resources such as SMS, email, payment, or order creation

This file is intentionally focused on application review signals, not full platform or infrastructure security design.

## Access And Data Exposure

- Personal or tenant-scoped pages and actions must enforce permission checks.
- Sensitive user data should not be displayed in raw form when masking is expected.
- Do not expose internal error details, stack traces, or raw codes directly as user-facing messages.

## Input Validation

- Validate all externally controlled parameters before they influence query shape, ordering, paging, file access, redirects, or expensive processing.
- Treat input validation as a security boundary, not just a UX concern.
- Validate batch-size and page-size style parameters to avoid memory pressure and abusive queries.
- Be cautious with regex-based validation for attacker-controlled inputs; poorly designed patterns can create ReDoS risk.

## Injection And Output Safety

- SQL parameters must use binding or other explicit safe parameterization. Do not build query conditions with string concatenation.
- Do not output unescaped or unfiltered user-controlled data into HTML views.
- Redirect targets supplied from outside the system should pass explicit allowlist validation.

## Request And Action Protection

- State-changing form and AJAX operations should have CSRF protection when the application model requires it.
- High-cost or sensitive platform actions such as SMS, email, calls, ordering, or payment need anti-replay or abuse controls.
- User-generated content flows should consider anti-spam, abuse throttling, and content filtering when the product domain requires it.

## Review Signals

- Missing permission checks on user-owned resources.
- Raw personal data shown in full where masking is expected.
- Dynamic SQL assembled from request strings.
- Request parameters directly controlling `order by`, redirect targets, or regex execution.
- HTML rendering of unsanitized user data.
- Missing replay or rate controls around costly external actions.
