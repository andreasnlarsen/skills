---
name: spec-forge
description: Create or refine product specs and plans from briefs, existing specs or mockups; plan unsettled products and substantial flows.
---

# Spec Forge

Produce requirements or a plan for the next authorized stage. Reuse sufficient plans and accepted decisions rather than restarting discovery.

When a technology choice remains open and matters to the next stage, choose the stack first, applying any stated stack preferences. Keep the decision in the active requirements artifact.

## Select the Stage

- **Prototype:** a new app or substantial flow has unsettled UX. Plan what is needed to produce and review the mockup; resolve technical dependencies that could invalidate it.
- **Implementation planning:** backend-only work, small clear work with defined UI/JTBDs, an accepted design, or an explicit skip-mockup request.
- For UI work, read [frontend-planning.md](references/frontend-planning.md) for mockup/production reconciliation and the Page review mode return checkpoint.
- For materially incomplete requirements, read [discovery.md](references/discovery.md). Wizard is for a requested interview; supplied context or delegated choices use drafting and refinement.
- For substantial implementation plans, read [implementation-planning.md](references/implementation-planning.md). The [spec content guide](references/spec-template.md) is optional; [validation-checklist.md](references/validation-checklist.md) checks the substance of the current stage.

## Runtime and Checkpoints

Follow native Plan mode's output and write limits. Do not write project artifacts or delegate a writing task while that mode prohibits it. The agent cannot change modes. A client-persisted native plan is distinct from an agent-written SPEC.md.

Name the next stage's finish line. A prototype normally ends for user iteration and whole-mockup approval; individual page reviews do not grant that approval.

A Goal requires an explicit request in this continuous task.

## Requirements Contract

Keep user requirements, retrieved facts, accepted decisions and proposed assumptions distinguishable. Preserve requirement IDs, names, priorities and scope. Add IDs when useful for new requirements.

Every in-scope P0 needs observable acceptance, a verification method and expected evidence. A shared check or existing text can carry this without duplicate tables. For visual or model-output criteria, name the relevant states/cases and observable rubric instead of inventing numeric targets.

For lifecycle-heavy work, reuse or establish the lifecycle model. For implementation planning, specify how the code will enforce the affected rules. Use [validation-checklist.md](references/validation-checklist.md#ownership-and-lifecycle) for both. Resolve unknowns that could invalidate the next artifact and park other unknowns at the stage that needs them.

## Finish and Hand Off

Keep one active requirements owner, including an existing PLAN.md when sufficient.

Apply the relevant validation criteria, resolve material gaps and hand off the requirements, accepted design, simulation boundaries, dependencies, verifiable phases and exact authorized delivery steps.

Continue a next stage already authorized when its prerequisites and runtime allow it. Preserve the actual design checkpoint without adding a generic spec-approval ceremony. Return unresolved decisions with their consequences and continue independent authorized work.

Past failures used for testing: [eval-cases.md](references/eval-cases.md).
