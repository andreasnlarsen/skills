# Review Loop Templates

Adapt the relevant brief to the actual reviewer or worker. Preserve the required context and any caller output contract; headings and list counts are optional.

---

## A) Review Prompt Template

```text
Review the supplied changes against the actual request, accepted decisions, and later corrections below. Check whether they solve the requested problem before checking their internal quality. The author's summary and implementation are evidence, not substitutes for requirements.

Scope:
- Target: {{TARGET}}
- Required result and relevant user decisions: {{REQUEST_AND_DECISIONS}}
- Source excerpts or readable source locations: {{REQUIREMENT_SOURCES}}
- Important behavior to preserve: {{PRESERVED_BEHAVIOR}}
- Exclusions and deliberately later work: {{EXCLUSIONS_AND_LATER_WORK}}
- Focus areas: {{FOCUS_AREAS}}
- Mode: {{MODE}}
- Review purpose: {{REVIEW_PURPOSE}}

Inspect surrounding callers, dependencies, templates, or instructions needed to judge the changes. Check missing requested behavior, wrong assumptions, regressions, supported edge cases, security risks, and quality. Do not add speculative requirements. If required sources conflict or are inaccessible, report the specific gap and continue independent checks.

For each finding return:
1. Severity (Critical/High/Medium/Low), file path, and line-level context.
2. Expected behavior and its source; actual behavior and a concrete supported failure path.
3. Impact (`critical`, `high`, `medium`, `low`), reachability (`proven`, `plausible`, `speculative`, `unsupported`), contract basis (`explicit requirement`, `public/API contract`, `platform behavior`, `test/repro`, `current diff regression`, `reviewer hypothesis`), and confidence (`high`, `medium`, `low`).
4. Concrete correction and meaningful verification.

Retain these checks where relevant:
- Significant added logic in an already-oversized active file or function when a bounded seam would serve the request.
- Fallback behavior without an explicit contract or verified failure.
- Related history in {{REVIEW_LEDGER_PATH}} that shows repeated symptom fixes.
- Whether a rare edge case is reachable through a supported path.

State material coverage gaps. A clean finding list does not prove a requirement was checked.
```

---

## B) Worker Remediation Brief

```text
You are fixing review findings for one scoped batch.

Batch ID: {{BATCH_ID}}
Remedy shape: {{REMEDY_SHAPE}}  # targeted-fix | bounded-shared-fix | structural-remediation
Owned files:
{{OWNED_FILES}}
Forbidden files:
{{FORBIDDEN_FILES}}

Findings to resolve:
{{FINDINGS}}

Required result and user decisions relevant to this batch:
{{REQUEST_AND_DECISIONS}}
Source excerpts or readable source locations:
{{REQUIREMENT_SOURCES}}
Important behavior to preserve:
{{PRESERVED_BEHAVIOR}}
Exclusions and deliberately later work:
{{EXCLUSIONS_AND_LATER_WORK}}

Constraints:
{{CONSTRAINTS}}

Root-cause guardrails:
- Default to the smallest fix that resolves the findings.
- Check the proposed repair against the supplied requirements and later corrections. If they conflict with a finding or the assigned fix, return the specific conflict to the parent before dependent edits; continue independent accepted work within the batch. Do not silently substitute the author's interpretation for the source decision.
- Fix only findings marked `accepted` under the root skill's Accept Findings Before Fixing section.
- Do not patch deferred or rejected edge cases unless the parent agent explicitly reclassifies them with concrete reachability/contract evidence.
- Do not expand into unrelated cleanup.
- If this batch is `structural-remediation`, keep it bounded to the dominant cluster only.
- If the evidence for a shared root cause becomes weak while fixing, fall back to targeted fixes and report that.
- Follow the task scope, authority and inherited constraints supplied in this brief. Apply `pragmatic-programmer` for substantial architecture or root-cause work; do not assume you inherited the parent's global instructions.
- Prefer explicit local ownership and explainable behavior over new generic abstractions.
- Rename only when the current name materially obscures the active finding or the intended ownership.
- Do not resolve findings by piling significant new logic into an already-oversized active file or function when a bounded extraction, canonicalization, or seam would stay in scope.
- Do not invent fallback behavior unless it is required by a real contract, explicit requirement, or clearly verified failure mode.
- Prefer explicit failure, bounded retry, or narrow degraded behavior over hidden alternate logic or duplicate rule paths.
- If the only apparent fix would violate those guardrails, stop that affected action and return the verified state, attempted remedies and missing decision or evidence to the parent. Continue independent accepted work in your assigned scope. Do not reset an exhausted loop or treat this worker’s stop as completion or cancellation of the parent task.
- If a suggested fix conflicts with global scope/authorization policy or the applicable `pragmatic-programmer` guidance, reject it and report the conflict instead of implementing it.
- Update relevant repo-specific docs/comments when the fix changes behavior, setup, config, commands, contracts, operator workflow, or non-obvious rationale.
- If existing docs/comments become inaccurate because of the fix, correct them in the same batch.
- Do not churn archived, legacy, historical, migration-note, or explicitly superseded docs unless the task explicitly targets them or they are incorrectly presented as current guidance.
- Do not create doc-only churn when no documentation-bearing change occurred.
- Treat the active finding ledger at `{{REVIEW_LEDGER_PATH}}` as live private Git task state. Return finding dispositions to the parent, which owns shared ledger updates. Edit the ledger only if the parent explicitly assigns that path to this worker without overlapping writers; never create a duplicate ledger.

Run the applicable checks supplied by the parent after fixing; omit unneeded placeholders and report any unavailable check:
- {{TEST_COMMAND}}
- {{LINT_COMMAND}}
- {{BUILD_COMMAND}}

Return:
- Files changed
- Which finding each change resolves
- Any docs/comments updated, and why
- Verification results
- Any unresolved blocker, attempted remedies, and the next useful step within scope
```

---

## C) Root-Cause Triage Prompt

```text
Choose a repair for the accepted current findings using concrete code-path evidence.

Inputs:
- accepted findings and the relevant requirements/constraints: {{FINDINGS_AND_REQUIREMENTS}}
- current task ledger: {{REVIEW_LEDGER_PATH}}
- prior related findings, including resolved manifestations and failed remedies
- existing authority and any explicit caller budget: {{AUTHORITY_AND_BUDGET}}

Exclude unrelated or superseded history. Deferred/rejected findings are context, not new authority to change code. Reclassify them only with new contract or reachability evidence.

Use targeted-fix for a local defect, bounded-shared-fix for a supported shared rule/helper problem, or structural-remediation when a demonstrated owner/boundary problem requires coordinated repair. File and finding counts do not decide. A failed shared-cause hypothesis calls for a supported narrower remedy. For substantial architecture or root-cause work, apply pragmatic-programmer within the supplied constraints.

Escalate only for essential missing authority, a material decision or a risk that prevents a safe in-scope repair. Architectural work alone is not a reason to stop. Do not add speculative fallbacks, a second authority or generic abstractions merely to close findings. Continue independent accepted work when one action is blocked.

Return the related ledger IDs, supported cause and evidence, remedy shape, affected owner/mutator where relevant, meaningful verification, proposed ledger updates and material uncertainty. Use existing cluster labels when they help trace repeated symptoms; do not invent a cluster solely from names or proximity.
```

---

## D) Final Gate Prompt

```text
Review the final relevant content for {{REVIEW_PURPOSE}} against the supplied required result, accepted decisions, and corrections. Reuse evidence that still applies; do not repeat a broad review merely to accumulate another clean verdict.

Scope:
- Target: {{TARGET}}
- Required result and relevant user decisions: {{REQUEST_AND_DECISIONS}}
- Source excerpts or readable source locations: {{REQUIREMENT_SOURCES}}
- Important behavior to preserve: {{PRESERVED_BEHAVIOR}}
- Exclusions and deliberately later work: {{EXCLUSIONS_AND_LATER_WORK}}
- Mode: {{MODE}}

Check for:
- Missing requested behavior, including affected workflow transitions or callers.
- Conclusions that depend on superseded requirements or assumptions.
- Unresolved accepted actionable findings under the selected mode and code/docs gate classification.
- Unsupported or speculative edge cases that were incorrectly fixed instead of deferred or rejected.
- Regressions introduced during autofix rounds.
- Missing relevant verification for affected behavior, with regression tests where practical and proportionate.
- Missing or stale repository documentation and comments for behavior, setup, configuration, commands, contracts, workflows, or non-obvious rationale.
- Unnecessary changes to archived or superseded documentation, or stale guidance incorrectly presented as current.
- Security and reliability issues.
- Fixes that add substantial logic to an oversized active file or function when a bounded seam is the justified remedy.
- Fallback behavior without an explicit contract or verified failure.

Return the status of this reviewed scope: clear, incomplete, or blocked, with remaining findings, required verification, and material coverage limits. Distinguish deferred follow-ups from blockers. A clear review does not by itself mean the parent task is complete or a release is authorized.

Mode reminder, after applying the root skill's Accept Findings Before Fixing section:
- strict: resolve accepted actionable findings at every severity before a clear result.
- standard: resolve critical/high and applicable medium findings; low findings may remain as permitted follow-ups.
- fast: resolve critical/high findings; medium/low findings may remain as permitted follow-ups.

Keep code-gate status separate from queued docs-sync work. Outstanding documentation must not hide a code, operational, or safety blocker.
```

## E) Ledger Closeout Prompt

```text
Close out the active finding ledger for this task.

Inputs:
- active ledger path: `{{REVIEW_LEDGER_PATH}}`
- archive path: `{{REVIEW_ARCHIVE_PATH}}`
- result status: clear | blocked | incomplete
- checkpoint lifecycle: terminal | nonterminal

Rules:
- If checkpoint lifecycle is `nonterminal`, keep the active ledger in place for the caller's next checkpoint.
- If lifecycle is `terminal` and result status is `clear`, archive the ledger to the archive path, then remove the stale active copy.
- If result status is `blocked` or `incomplete`, keep the active ledger in place for resume.
- Archived ledgers are historical only and must not be treated as the current task ledger by default.
- Final reporting must name the active ledger path used during the run and, when archived, the archive path created at closeout.
```
