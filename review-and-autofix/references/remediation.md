# Accepted Findings and Remediation

The root skill owns finding acceptance, mode and the clear gate. [state-and-reporting.md](state-and-reporting.md) owns cumulative finding history. Read this reference when fixing accepted findings or assigning a fix worker.

## Choose the Remedy

Use accepted findings and related current-task history, including resolved manifestations, to identify the cause. A repeated wave of local findings can reveal a shared rule, owner or boundary problem; naming or proximity alone cannot.

Choose the smallest repair that resolves the supported cause within the actual authority:

- `targeted-fix`: the defect is local;
- `bounded-shared-fix`: a shared helper, rule or contract explains related defects;
- `structural-remediation`: a demonstrated ownership or boundary problem requires a coordinated change;
- `manual-escalation`: an essential decision, new authority or unresolved risk prevents a safe in-scope fix.

File counts, cluster counts and architectural labels do not determine the remedy or grant permission. If the shared-cause hypothesis fails, use the supported local repair instead. Continuing symptom churn calls for renewed diagnosis; it does not create an automatic refactor budget or require another identical review loop.

Use [pragmatic-programmer](../../pragmatic-programmer/SKILL.md) for substantial root-cause, ownership or design work. Preserve required behavior and canonical authority. Do not invent fallback paths or abstractions to silence a speculative finding. If no compliant repair is supported, return the exact gap while continuing independent accepted fixes.

## Execute and Verify

Fix directly by default. When delegation is authorized and useful, give workers disjoint file ownership, the relevant requirements and accepted findings, and applicable verification commands using [template B](review-loop-template.md#b-worker-remediation-brief). Use [template C](review-loop-template.md#c-root-cause-triage-prompt) for the remedy decision. Serialize overlapping work and coordinated structural changes. If workers conflict, narrow ownership or finish sequentially rather than retrying a competing batch.

Keep the repair and affected operational documentation together. Reuse valid evidence and check changed behavior, dependencies and required repository gates. Review the repaired paths when existing evidence does not establish their correctness; structural work does not automatically require a second native broad review.

Update the shared ledger through its assigned owner. Record failed hypotheses and verification regressions so later checkpoints do not repeat them. Keep historical documentation intact unless it is incorrectly presented as current or explicitly in scope.

For Wrangler or other runtime permission errors, preserve the error and use the host-permitted diagnostic route. A supported task-local log directory may resolve a log-path problem; changing HOME or authentication discovery to make a check pass is not a valid repair.
