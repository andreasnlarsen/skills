# Backend Health

---

## BE-01: API Design Consistency

**What:** Inconsistent URL patterns, HTTP methods, response formats, or status codes across API endpoints.
**Detection:** static — scan route definitions for naming patterns (plural vs singular, kebab vs camel), response shapes, status code usage.
**Possible correction:** Align the endpoint with its established consumer contract; adopt an API style guide only when inconsistency creates material client cost.

## BE-02: N+1 Query Patterns

**What:** Code that queries a database inside a loop, causing N+1 queries.
**Detection:** static — look for database calls inside `.map()`, `.forEach()`, `for` loops, or list comprehensions. Check ORM usage for missing `include`/`joinedload`/`preload`, and recursive queries without depth limits.
**Possible correction:** Eager-load, batch with `WHERE IN`, or use a dataloader when repeated queries are demonstrated; preserve filtering and authorization semantics.

## BE-03: Auth Coverage

**What:** A protected operation can be reached without the required authentication or authorization.
**Detection:** static — check if route handlers have auth middleware. Look for routes without auth decorators/guards. Compare public vs protected routes.
**Possible correction:** Apply auth middleware globally with explicit opt-out for public routes when any protected operation is reachable without it.

## BE-04: Input Validation

See [SEC-09](checks-security.md#sec-09-input-validation-at-boundaries).

## BE-05: Error Handling Patterns

**What:** Inconsistent error handling — some endpoints return stack traces, some swallow errors, some return inconsistent error formats.
**Detection:** static — check for unhandled promise rejections, empty catch blocks, inconsistent error response shapes, stack traces in error responses.
**Possible correction:** Use centralized error-handling middleware with a defined response format when callers get inconsistent failures; never expose stack traces in production.

## BE-06: Database Migration Health

**What:** Schema changes cannot be applied or recovered according to the deployment and data-preservation contract.
**Detection:** static — compare migration history, dependencies and the expected schema. Assess the supported forward-repair, rollback or restore path for relevant changes.
**Possible correction:** Preserve applied migration history; choose rollback, forward repair or a verified restore path that fits the data change.

## BE-07: Logging Quality

**What:** Insufficient, excessive, or unstructured logging.
**Detection:** static — inspect whether relevant failures are diagnosable, log volume is useful, levels reflect conditions and sensitive values are protected. Look for `console.log` / `print` in production code paths.
**Possible correction:** Use a structured logging library (pino, winston, structlog) with levels when failures are hard to diagnose; never log secrets or unnecessary personal data.

## BE-08: Config Management

**What:** Hard-coded configuration, missing environment variable validation, secrets in code.
**Detection:** static — search for hard-coded URLs, ports, connection strings. Check for `.env.example`. Verify env vars are validated at startup.
**Possible correction:** Move environment-dependent values to environment variables validated at startup, with a `.env.example`, when configuration is hard-coded; keep stable constants local.

## BE-09: DB Connection Management

**What:** Connection pool misconfiguration, connection leaks, missing connection limits.
**Detection:** static — check for connection pool settings. Look for connections opened but not closed/returned. Check for missing connection timeout.
**Possible correction:** Release every connection in try/finally or a context manager when leaks are found; size pool and timeouts from workload and deployment limits.

## BE-10: Rate Limiting

**What:** A reachable abuse or resource-exhaustion path lacks adequate controls.
**Detection:** static — inspect costly/public operations and existing application, gateway or provider limits against legitimate workload and exposure.
**Possible correction:** Add rate-limiting middleware returning `429` with `Retry-After` when a verified abuse path lacks upstream protection; prioritize auth endpoints.

## BE-11: Async/Concurrent Safety

**What:** Race conditions, missing locks, unsafe shared state in concurrent code.
**Detection:** static — look for shared mutable state without synchronization. Check for missing `await` on async operations. Look for fire-and-forget async calls without error handling.
**Known failure:** Missing `await` on a promise whose result is used.
**Possible correction:** Await operations whose result or ordering matters; give background work an error owner and lock shared state where the runtime can race.

## BE-12: API Versioning

**What:** API changes can break supported consumers without a suitable compatibility or transition contract.
**Detection:** static — inspect consumers, published contracts and API evolution. Route or header versions are examples of a mechanism, not proof of compatibility.
**Possible correction:** Version routes or headers when a change would break supported consumers; a version prefix is not universally required.

## BE-13: Health Check Endpoints

**What:** Missing or insufficient health check endpoints.
**Detection:** static — search for `/health`, `/healthz`, `/ready`, `/live` routes. Compare health/readiness behavior with what the deployment platform or monitor consumes, including the effect of dependency checks on restart and routing decisions.
**Possible correction:** Expose `/health` (liveness) and `/ready` (readiness) as the platform consumes them; keep dependency checks out of restart decisions.

## BE-14: Background Job Resilience

**What:** Background-job failures or retries violate the supported delivery and finalization contract.
**Detection:** static — check job/worker definitions for retry configuration, error handling, timeout settings, dead-letter queue config.
**Possible correction:** Add timeouts, retry with exponential backoff and a dead-letter queue when failed jobs are silent or retried unsafely; preserve idempotency.
