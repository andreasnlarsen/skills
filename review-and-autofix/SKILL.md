---
name: review-and-autofix
description: Review scoped code changes, triage findings, apply authorized fixes and verify results, including delegated review checkpoints.
---

# Review and Autofix

Review the actual requested changes against their requirements. Apply fixes when authorized. A clear review describes the checked scope, not completion of the parent task.

## Required Result and Authority

Establish the exact target: files, staged diff, uncommitted changes, commit, PR or branch. Preserve that target across transports.

Retrieve the original requirements, accepted decisions, corrections, preserved behavior, exclusions and requested finish line. Keep them separate from the author's explanation and implementation. Verify that the reviewer received the context needed for its claims.

Supply missing context through a supported reviewer route, or perform the requirement check yourself: do these changes deliver the requested behavior across affected callers and workflow steps? A corrected requirement or assumption can invalidate a conclusion even when files have not changed.

## Select the Route

| Need | Reference |
| --- | --- |
| Start or resume review state | [state-and-reporting.md](references/state-and-reporting.md): one cumulative private ledger and evidence record |
| Native Codex review | [native-review.md](references/native-review.md): exact argv, compute, owned processes and recovery |
| Fix accepted findings | [remediation.md](references/remediation.md): choose the repair from evidence and coordinate writes |
| Context-aware reviewer or worker | [review-loop-template.md](references/review-loop-template.md): adapt the relevant self-contained brief |

Use an existing structured harness when it preserves the target, freezes the reviewed content and exposes the chosen compute. Otherwise use a supported native or in-session route. Do not create a new helper script during a review run unless the user asks. Honor the caller's supported model and effort; otherwise default to GPT-6.1 Sol (`gpt-6.1-sol`) with `xhigh` reasoning. Verify host support and record the actual selection; report an unavailable default instead of silently substituting another model or effort.

Use standard mode unless the caller selects another. Honor an explicit work/round budget. Default fix budget is 3 cycles, at most 5, unless the caller sets another; a justified additional review pass without fixes does not consume one.

## Accept Findings Before Fixing

For each material finding record severity/impact, location, expected behavior and source, actual failure path, reachability, confidence, correction and verification. Classify reachability as proven, plausible, speculative or unsupported, and identify the contract basis: explicit requirement, public/API contract, platform behavior, test/reproduction, current-diff regression or reviewer hypothesis.

Disposition is `accepted`, `deferred` or `rejected`. A supported rare failure can matter.

| Mode | Findings requiring correction when fixes are authorized |
| --- | --- |
| strict | Accepted actionable findings at every severity |
| standard | Critical/high, and medium reachable under a real contract or current-diff regression; low only when requested or a cheap, low-risk local correction |
| fast | Critical/high; medium/low are follow-ups by default |

Classify gate scope separately:

- `code`: executable code, tests, configuration, public/API contracts, repository instructions, and documentation that governs execution or operational safety. An inaccurate setup command or safety rule belongs here.
- `docs-sync`: ordinary explanatory, status or architecture drift that cannot misdirect executable behavior or an operational/safety contract.

Normalize native findings enough to support those decisions.

## Review, Repair and Clear

Keep the target, requirement sources, content fingerprint, review purpose, verification evidence and finding history in the [private state](references/state-and-reporting.md). Confirm actual reviewer completion before accepting a verdict. Triage findings against the cumulative history; use [remediation.md](references/remediation.md) for fixes.

A clear code result requires a clean review of the final relevant content, coverage of the actual requirements and requested review purposes, and passing relevant verification. The first review may satisfy the final gate when its evidence already covers that content. Add a pass only for a distinct unresolved question, an affected conclusion after changes, or an explicit request. Auth, permissions, entitlements, billing, privacy, data loss, tenant lifecycle and workflow status transitions are where a second look pays off.

Changes to code, tests, configuration or operational contracts invalidate affected evidence. Ordinary explanatory docs do not invalidate unrelated checks. Deferred or rejected findings and queued docs-sync work remain visible without masquerading as code blockers.

When a technique stalls, preserve the reproduction, attempted hypotheses and remaining coverage, then choose a materially different permitted step. An incomplete checkpoint returns control to its parent task and does not reset exhausted attempts.

## Caller Result

For delegated checkpoints preserve these fields, with detail proportionate to the review:

- `terminal_status`: `clear`, `blocked` or `incomplete`;
- `accepted_findings_remaining`: separate code and docs-sync scopes;
- `review_evidence`: purpose, reviewer compute when known, content fingerprint, outcome and missing coverage;
- `verification_status` and `ledger_path`;
- `continuation`: unresolved work, reproduction, attempted remedies, next useful step and any exact missing authority, or none;
- concise findings and remediation summary.

A caller may also specify a stable task ID and `terminal` or `nonterminal` checkpoint lifecycle. Preserve the ledger for a nonterminal checkpoint; archive it on successful terminal closeout under its reference contract.

Past failures used for testing: [eval-cases.md](references/eval-cases.md).
