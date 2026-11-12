# Severity And Prioritization

This reference owns final severity and priority across architecture-health checks. Numerical observations in category references help select evidence to inspect; they are not automatic findings, mandatory remediation, or universal risk grades.

## Status

| Status | Meaning | Report action |
|--------|---------|---------------|
| CRITICAL | A verified or strongly supported reachable failure can cause serious security, data-integrity, availability, financial, or other material harm in the project's actual use | Put the failure path, impact, confidence, and immediate containment or correction first |
| WARNING | A supported failure or demonstrated change cost merits correction, but the evidence does not establish critical impact or urgency | Explain affected behavior, likelihood or reachability, and the smallest useful correction |
| INFO | A contextual observation or optional improvement without a demonstrated material failure | Keep separate from blockers; do not manufacture work to remove it |
| PASS | The stated check was performed and its scoped expectation was met | Name the evidence and its limits; do not imply untested behavior is safe |
| SKIP | The check is inapplicable or could not be performed | Record the reason and what remains unknown |

A missing feature, large file, dependency count, percentage, or tool score does not determine final severity. A failed check may reveal an application defect or an unavailable tool; preserve the actual error and distinguish them. Never turn an unknown into PASS.

## Evidence Per Finding

Record:

- the relevant file/line, command result, or source of the observation;
- the supported trigger, affected behavior, and plausible consequence;
- actual exposure and any compensating control;
- confidence and the smallest evidence gap that could change the conclusion;
- one canonical root cause or owner where supported;
- a bounded correction and the check that would establish its result.

Separate observed failures from hypotheses. Several checks may describe one root cause: report one finding with the supporting observations rather than inflating its count. Do not infer a shared cause from naming or proximity alone.

## Priority Order

1. Address serious reachable harm and required contract failures first. A costly critical correction must not be displaced by cosmetic quick wins.
2. Next, prioritize demonstrated reliability or changeability bottlenecks that affect current work or the next likely change.
3. Use effort, dependencies, reversibility, and available evidence to choose among comparable risks. State assumptions behind time estimates; do not imply precision without project evidence.
4. Defer optional improvements when their value does not justify the scope. An audit can correctly recommend no change.

Use labels such as **Immediate risk**, **Next correction**, and **Optional improvement**, with a reason. The quick-win and strategic-investment sections of [report-template.md](report-template.md) organize recommendations after urgency is established; they are not a formula for trading off unrelated harms.

## Comparison Between Audits

Do not calculate a universal 0-100 score, letter grade, average, maturity bonus, or deduction per finding. No such scale has been calibrated here, and averaging can conceal a single critical defect.

For a comparison, use concrete outcomes under comparable scope and conditions: whether a named failure remains reachable, whether the same check passes, measured latency under the same workload, or how many owners a verified business-rule change touches. Record the revision, command/workload, relevant environment, and any differences. Report unresolved critical findings and missing coverage prominently. An empty finding list is not a production-readiness certificate.

## Project Context

- **Prototype or greenfield:** Defer speculative scaling, optimization, and process machinery when no current requirement needs them. Preserve security and critical behavior checks appropriate to the real data and exposure. Do not grant a coverage percentage exemption or maturity bonus.
- **Active or mature product:** Use actual incidents, workload, release workflow, and change history to identify material test/build latency, dependency, ownership, and documentation problems. Age and size alone do not raise severity.
- **Inherited or rescue project:** Establish exposure, critical data, credential handling, recoverability, and the tests that protect essential behavior. Defer style cleanup unless it directly obstructs the repair. Unknown history is a reason to obtain evidence, not to declare every missing convention critical.

## Context That Can Increase Severity

These are investigation prompts, not automatic escalation rules:

| Observation | Evidence needed before raising severity |
|-------------|----------------------------------------|
| No health endpoint | The deployment's actual health/restart contract and a reachable failure it cannot detect |
| No rate limiting | Exposed abuse path, resource or financial impact, and existing upstream controls |
| No monitoring | A material failure that cannot be detected or diagnosed within the required response time |
| In-memory sessions | Multi-instance or restart behavior that violates the real session contract |
| No visible backups | The authoritative backup/recovery setup, critical data at risk, and required recovery outcome |
| Missing index | Query plan, workload, and demonstrated or well-supported latency/resource impact |
| Business-rule scatter or ownerless logic | A concrete supported change or failure that can make the duplicated rules disagree |
| Split authority or multiple mutators | A reachable race, inconsistent decision, duplicate side effect, or broken state transition in the affected flow |

For auth, billing, permissions, entitlements, tenant lifecycle, or external event-driven workflows, inspect authority and mutation paths early because their consequences can be serious. Their names alone do not prove a critical finding.
