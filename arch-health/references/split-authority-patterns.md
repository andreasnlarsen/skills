# Split Authority Patterns

Use this reference when a codebase may have more than one writer or authority for the same shared mutable business state or durable side effect.

## Definition

`Split authority` exists when `2+` in-scope paths are allowed to mutate the same shared mutable business state, finalize the same durable side effect, or behave as if they are co-equal authorities, without a documented runtime or contract-boundary reason.

Aliases:
- too many authorities
- multiple mutators
- dual source of truth

This is different from nearby concepts:
- `rule scatter`: the same business rule is implemented in multiple places
- `ownerless logic`: no canonical owner is clear
- `split authority`: multiple writers/finalizers act as authorities for one shared state or side effect

## Detection Checklist

For each critical mutable business datum or durable side effect in scope, map:

1. The business state or durable side effect.
2. The system of record.
3. Every in-scope path that can mutate or finalize it.
4. The authoritative mutator.
5. Allowed non-authoritative paths that may only read, display, enqueue, or derive projections.
6. Any justified duplication caused by a real runtime or contract boundary.

Flag split authority if:
- `2+` handlers, jobs, hooks, workers, return pages, or webhooks can finalize the same state.
- A recovery path can mutate the same durable state as the normal lifecycle path without a documented ownership rule.
- An external platform is treated as authoritative, but app code also behaves like an equal authority.

Do not flag split authority when:
- the client performs local UX validation while the server remains authoritative
- a page polls and displays status only
- a cache, mirror, or materialized view is derived from canonical state and does not compete as an authority
- one path enqueues work while another path is the only mutator of durable state

## Severity Guidance

Use [severity-matrix.md](severity-matrix.md). Establish a reachable race, conflicting decision, duplicated side effect or broken transition, then assess its impact. The domain name and number of writers alone do not determine severity.

## Example Cases

### Bad: checkout return page and webhook both set billing state

- Return page marks subscription active in the app database.
- Webhook also marks subscription active and provisions access.
- Result: race conditions, retries, and conflicting authorities.

### Good: return page displays status, webhook mutates billing state

- Return page shows pending/success and reloads current status.
- Webhook updates subscription state and triggers idempotent provisioning.
- Result: one mutator, one authority.

### Bad: API route and worker both finalize the same tenant status

- API route sets tenant to `ready`.
- Worker later also decides readiness independently.
- Result: two mutators for the same durable lifecycle state.

### Good: API route submits command, worker owns lifecycle transition

- API route records intent or enqueues a job.
- Worker is the only path allowed to finalize tenant readiness.

### Near-miss: local validation plus authoritative server validation

- Client blocks obviously invalid values.
- Server still owns durable validation and state mutation.
- This is not split authority by itself.

### Acceptable exception: offline/local validation with authoritative server commit

- A local client must validate format or eligibility offline.
- Server remains the only authority that commits durable state.
- Document the boundary so the duplication is clearly non-authoritative.
