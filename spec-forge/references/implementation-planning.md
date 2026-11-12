# Implementation Planning

The root skill owns stage, runtime, requirement identity and acceptance evidence. Use this reference for substantial implementation planning.

Inspect affected code and its callers, state, dependencies and checks to choose credible phases and owners. Record material coupling or verification risks and only the repair the requested outcome needs. Greenfield work has logical owners without invented file boundaries.

Reuse settled stack and build-versus-buy decisions. If a choice is open or materially changed, compare realistic existing, configured, bought and built options against the requirement and total ongoing burden. Keep the decision basis in one place.

Shape verifiable phases around useful completed behavior and actual dependencies. Preserve accepted priorities and release scope. Establish shared contracts before delegated parallel work and assign disjoint writes from inspected code. For UI work, follow [frontend-planning.md](frontend-planning.md); reference accepted designs and simulation limits instead of creating a new theme or design document by default.

## Artifact Ownership

Use the existing requirements artifact, including a sufficient PLAN.md. Default to SPEC.md only when a separate spec is needed and file writes are permitted. A separate execution plan references requirements instead of duplicating them.

Keep one active owner of the scoped implementation requirements. Multiple active root specs require an explicit request. When replacing an active spec, archive the superseded version as `archive/specs/SPEC-<slug>-<yyyy-mm-dd>.md`, adding a suffix if that name exists; never overwrite an archived spec. Historical specs do not remain the implementation contract.

[spec-template.md](spec-template.md) is an optional content guide. Use [validation-checklist.md](validation-checklist.md) to check the planned stage's substance, then follow the root's handoff and continuation rules.
