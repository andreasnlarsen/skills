# SPEC.md Template

Use the topics that help the current plan. This is not a required file, section order or questionnaire. Preserve an existing artifact, requirement IDs, priorities and wording. Native Plan mode uses its native output; a prototype plan needs only the decisions required to build and review that prototype.

## Skeleton

Copy the parts that apply and omit the rest without N/A filler. Example IDs and phases are formatting, not project requirements.

```markdown
# SPEC: <title>

- **Project / Repo:**
- **Status:** `draft | approved | in-progress | implemented | superseded | archived`
- **Decision basis:** [user-approved decisions; delegated agent choices; unresolved items]
- **Execution plan:** [separate plan path, when present]
- **Last updated:**
- **Superseded versions:** `archive/specs/`

## Goal

## Non-Goals

## Target Users and Journeys

## Requirements

| ID | Priority | Requirement | Acceptance criterion | Verification and expected evidence |
| --- | --- | --- | --- | --- |
| REQ-001 | P0 | | | |
| REQ-002 | P0 | | | |
| REQ-010 | P1 | | | |
| REQ-020 | P2 | | | |

## Non-Functional Requirements

## Technical Decisions

## Lifecycle / State Model

## Accepted Interface

## Phases

### Phase 1 (release scope)
- [ ] REQ-001
- [ ] REQ-002

### Phase 2
- [ ] REQ-010

## Risks and Open Decisions
```

## Decision Context

Identify the product goal, users, journeys, current requirements owner, accepted decision basis and material constraints. Clarify likely scope misunderstandings without inventing non-goals. Status labels such as approved or implemented do not grant authority.

Keep a separate execution plan's dependency order and progress in that plan. A superseded specification belongs in `archive/specs/`, not beside the active contract as another owner.

## Requirements and Evidence

For new requirements, stable IDs can help trace behavior and verification. P0 denotes required delivery scope when that priority scheme fits; preserve an existing scheme and release definition. Later work stays later unless the user changes it.

The skeleton's requirement row shows the minimum: the behavior the user must be able to accomplish, and the check, state/case or rubric that establishes it.

Non-functional requirements need meaningful conditions or project-supported metrics. Do not manufacture numeric targets. Preserve an explicit testing cadence or project convention; choose meaningful behavior and realistic failure checks rather than a universal test stack or coverage quota.

## Technical Decisions

Explain unresolved build/configure/buy choices, relevant alternatives, rationale and operating burden. Reuse accepted decisions. Describe the material application boundaries, data entities/relationships, integration roles, authentication, limits and dependencies.

Name canonical domain terms and preserve the project's vocabulary. Establish shared rule owners, systems of record and authoritative mutators where relevant; keep local presentation and narrow adapter details local. A likely next change may justify a replaceable seam, but no future roadmap or generic extension platform is required.

## Lifecycle Behavior

For workflows, approvals, billing, retries, jobs, webhooks and similar stateful processes, an adequate model includes relevant objects and states, transitions/triggers, finalizing owners, idempotency, invalid transitions and supported recovery. Identify observational paths and derived projections.

One useful transition representation is:

| Object | From → To | Trigger | Finalizing owner | Idempotency/failure behavior |
| --- | --- | --- | --- | --- |
| Domain object | Supported transition | Event or user action | Actual authority | Required contract |

Use a diagram or existing model when clearer. A status/field list alone does not explain behavior. Avoid invented recovery or fallback paths merely to fill a table.

## Accepted Interface

For UI work, reference the accepted artifact and revision, acceptance basis, journeys/states, simulations and material changes since acceptance. Link the existing design-system owner rather than copying token values or creating another document. Connect visible actions and data to their real requirements, especially where the mockup simulates persistence, permissions or integrations.

## Delivery and Open Decisions

Define useful implementation phases, dependencies and observable finish lines using the accepted priorities. Include relevant rendered and functional checks. Record material risks, unknowns, their consequences and resolution points. A deferred unknown may remain only when it does not block the planned stage.
