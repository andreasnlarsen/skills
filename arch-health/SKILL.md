---
name: arch-health
description: Audit codebase architecture, changeability and technical debt. Use for "/arch-health", "architecture review", "codebase health check", "technical-debt audit" or finding implicit state machines.
---

# Architecture Health

Audit the requested codebase and explain which failures or change costs merit attention.

## Scope and Evidence

Use project manifests, structure and existing documentation to identify the relevant architecture and categories. An unqualified audit covers applicable categories; a focused request keeps its named scope. Calibrate findings against actual deployment exposure, critical data, workload, team workflow and the next likely change. Use [developer-questions.md](references/developer-questions.md) for material context that the repository cannot establish.

Read the applicable references as investigation prompts, not a mandatory checklist of features the project must add:

| Area | Reference |
| --- | --- |
| Code quality and ownership | [checks-code-quality.md](references/checks-code-quality.md) |
| Tests | [checks-testing.md](references/checks-testing.md) |
| Frontend | [checks-frontend.md](references/checks-frontend.md) |
| Backend | [checks-backend.md](references/checks-backend.md) |
| Infrastructure | [checks-infrastructure.md](references/checks-infrastructure.md) |
| Dependencies | [checks-dependencies.md](references/checks-dependencies.md) |
| Security | [checks-security.md](references/checks-security.md) |
| Observability | [checks-observability.md](references/checks-observability.md) |
| Developer experience | [checks-devex.md](references/checks-devex.md) |
| Cost and scaling | [checks-cost-scaling.md](references/checks-cost-scaling.md) |

Static inspection does not execute project code. Use dynamic checks only to resolve material questions, with existing verified tools and repository-native commands. Tests, lint, builds, dependency audits and bundle measurements are options. Distinguish a tool failure from a check exposing an application failure.

Use [CQ-18](references/checks-code-quality.md#cq-18-implicit-lifecycle-rules) to inventory implicit lifecycles across the requested scope when asked to find them. In a broad audit, focus on material lifecycles. Include concrete code recommendations where warranted.

## Findings and Priority

[severity-matrix.md](references/severity-matrix.md) owns status, evidence and prioritization. Size, count, age and tool scores are clues, not severity rules. Do not calculate universal health scores or letter grades. Group observations that share a supported root cause.

Explain the main changeability bottleneck when one is supported: what makes the next likely change expensive, and whether clearer ownership, a better boundary or a replaceable seam would help. Use [split-authority-patterns.md](references/split-authority-patterns.md) when several paths can finalize the same state or effect. Use [mece-thinking](../mece-thinking/SKILL.md) before planning a repair when overlapping concepts, mixed levels or missing states are the dominant problem.

## Report and Handoff

The default current artifact is `arch-health-report.md` in the project root. Before superseding it, archive the previous report under `archive/reports/`, following an established repository convention when one exists. Historical reports are not current evidence.

[report-template.md](references/report-template.md) is the default structure and archive naming; depart from it when the reader's decisions need a different shape. Organize around those decisions: checked scope and revision, material risks, evidence and confidence, missing coverage, and bounded recommendations. Put serious reachable harm before cheap cleanup. Include likely effort or useful implementation dependencies when supported, without a fixed time estimate.

An audit may recommend no change. Remediation tasks for the top findings, tagged quick-win or strategic, are available on request. Use `spec-forge` when a substantial repair needs specification.
