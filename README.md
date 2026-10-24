# Document Processing Architecture Review

This repository contains the requirements, proposed API contract, and synthetic request traces for an architecture decision about document processing.

## Review question

Should document processing run synchronously within the HTTP request, or should requests be accepted and processed by background workers?

## Scope

- Compare synchronous and queued processing.
- Evaluate six synthetic request traces against the API contract and requirements.
- Document success, timeout, duplicate retry, and worker failure scenarios.
- Produce an architecture comparison diagram in Miro.
- Record the recommendation and unresolved risks in a GitHub decision issue.

## Evidence disclaimer

All traces are synthetic examples created for this architecture review. They are not production measurements and do not establish actual service reliability or performance.
