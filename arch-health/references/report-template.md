# Report Template

`arch-health-report.md` in the project root is the active latest report. Before replacing it, archive the previous file as `archive/reports/arch-health-report-<yyyy-mm-dd>.md`, adding a suffix if that name exists, or follow a stronger existing repository convention. Never overwrite an archived report.

```markdown
# Architecture Health Report

**Project:** [name]
**Date:** [date]
**Type:** [frontend/backend/fullstack/etc.]
**Audited scope:** [categories, revision, and important exclusions]
**Main risk:** [evidence-backed risk or no material finding in the checked scope]

## Executive Summary

[2-3 sentences: overall health, biggest risk, most impactful quick win]

[If relevant, add a one-line "Canonical Ownership / Split Authority / Rule Scatter" callout naming the most important scattered rule or split-authority flow, the likely canonical owner, and the authoritative mutator.]

[If relevant, add a one-line "Main Changeability Bottleneck" callout naming the issue most likely to make the next significant change expensive, and whether the best remediation is consolidation, boundary cleanup, or a replaceable seam.]

[If relevant, add a one-line "Conceptual Model Repair" callout recommending [mece-thinking](../../mece-thinking/SKILL.md) before `/spec-forge` or implementation when overlap, mixed levels, or missing buckets are the dominant issue.]

## Coverage And Priorities

| Category | Evidence checked | Material finding | Priority and reason | Missing evidence |
|----------|------------------|------------------|---------------------|------------------|
| [category] | [files/checks/revision] | [verified or plausible failure] | [impact, reachability, urgency] | [unknowns or none] |

[Put critical risks first, including expensive fixes. Quick wins do not outrank a serious unresolved risk merely because they are cheap.]

## Quick Wins (High Impact, Low Effort)

[Findings that can be fixed in <1 hour with significant improvement]

1. **[Finding]** — [impact]. Fix: [specific remediation]. Effort: ~[time].
2. ...

[When a finding is driven by rule scatter or split authority, name the likely canonical owner, system of record, and authoritative mutator in the fix text.]
[When a finding is mainly about change cost, explain how the fix makes the next likely change cheaper or more local. Prefer explicit ownership or a replaceable seam over vague "add abstraction" advice.]

## Strategic Investments (High Impact, High Effort)

[Findings that need planning but deliver major improvements]

1. **[Finding]** — [impact]. Approach: [remediation strategy]. Effort: ~[time].
2. ...

[When a finding needs larger consolidation, recommend a scoped specification using `spec-forge` when useful. Implementation requires a separate user request.]
[When the future shape is unclear, recommend a replaceable seam instead of speculative platformization or generic extension points.]
[When the main blocker is a broken partition of concepts, lifecycle states, authority boundaries, decision branches, or policy buckets, explicitly recommend [mece-thinking](../../mece-thinking/SKILL.md) before `/spec-forge` or implementation.]

## Detailed Findings

### [Category Name]

| # | Check | Status | Evidence and impact | Confidence | Remediation |
|---|-------|--------|---------------------|------------|-------------|
| [id] | [check] | [status] | [location, supported failure path or demonstrated change cost] | [high/medium/low] | [smallest useful correction and verification] |

[Repeat for each category]

## Questions for the Team

[Things the audit couldn't determine from code alone]

1. [Question] — needed to assess [what]
2. ...
```
