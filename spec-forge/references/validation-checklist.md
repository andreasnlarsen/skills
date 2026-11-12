# Specification Validation

Check the current stage's substance, not a document shape. The root skill owns requirement identity and P0 acceptance evidence. Reuse sufficient prose, diagrams or canonical references; do not duplicate tables or add N/A filler.

## Outcome and Scope

Does the plan preserve the requested result, accepted priorities, requirement IDs and release definition? Resolve actual contradictions against current decisions. A vague quality word such as “fast” or “secure” needs an observable condition, not an invented metric. A milestone must not quietly drop P0 work, promote later work or turn a prototype into a production commitment.

## Acceptance Evidence

Each in-scope P0 needs acceptance, a method and expected evidence that establish the user's outcome. Creating an authentication endpoint is not enough to prove the required users can sign in. Shared checks may cover several requirements only when they exercise each claimed behavior.

Specify relevant cases/states and a rubric for visual, usability or model-output requirements. A structural CLI pass cannot prove those qualities. Performance/load claims need the corresponding workload and conditions. Use existing checks and frameworks where they can establish the required behavior; test counts and coverage percentages do not substitute for it.

## Feasibility and Architecture

Are dependencies that could invalidate the next artifact resolved? A documented API capability does not establish tenant access or a working integration. For an open build-versus-buy choice, compare actual incremental setup and maintenance across the people involved. Verify current pricing or limits before using them as a deciding rationale. Reuse sufficient accepted decisions rather than repeating a provider survey for every common capability.

For changed systems, check the affected owners, callers, state, dependencies and behavioral coverage. A file's size or a missing test filename is only a clue. The architecture should support the actual requirement without invented extension points, fallback paths or secondary authorities.

## Ownership and Lifecycle

For shared rules and mutable state, identify canonical business-rule owners, the system of record and the finalizing path. Other paths may read, display, enqueue or derive projections. Document a real runtime/contract exception where one is necessary; two entries in a table do not justify competing authority.

For lifecycle-heavy work, establish the relevant objects/states, allowed and forbidden transitions, triggers, transition owners, idempotency, supported recovery and observational paths. A field list does not define a lifecycle. For example, a billing return page may display status while a webhook owns finalization; a local/offline format check may coexist with authoritative server validation.

For implementation plans that change or make a lifecycle explicit, reconcile current behavior with accepted requirements. Specify the state representation, where the owner enforces transitions, what effects follow each relevant event and which writers must use that path. Preserve supported behavior outside the approved changes. If the cutover affects stored state or in-flight work, plan how to carry it forward. Define expected outcomes and checks for allowed and forbidden transitions and relevant duplicate, late or concurrent events.

Do not invent recovery merely to fill a lifecycle section. A fallback needs the real failure it handles and an explanation of how primary authority stays intact. Cached entitlement data must not silently become another rule owner.

## Mockup and Handoff

For an accepted UI, connect critical journeys, visible data/actions and required states to real implementation requirements. Simulation does not establish persistence, authorization or live integration. Apply [frontend-planning.md](frontend-planning.md) for the whole-mockup checkpoint and production reconciliation.

Resolve material gaps from evidence or delegated judgment. A remaining essential fact, decision or manual step stays visible with its consequence. Do not remove required scope or invent approval to make the plan appear complete.
