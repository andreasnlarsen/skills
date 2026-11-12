# Private Review State And Reporting

Read before creating or resuming review state. All review transports share this private ledger; do not put it in the reviewed worktree. The root owns review decisions and progress-based stopping conditions.

## Resolve State Paths

Derive one stable `task-id` for the run before creating the ledger:
   - If the user names the task, use a sanitized version of that label.
   - Otherwise use `uncommitted` for uncommitted-change reviews.
   - Otherwise use `base-<branch>` for base-branch reviews.
   - Normalize it to lowercase letters, digits, `.`, `_`, or `-`; do not allow `/`, `..`, or an empty value.
   - Reuse the same `task-id` when resuming the same review task so the same ledger file is refreshed instead of recreated.
   - Resolve and create private state paths before the first review:
     - `REVIEW_STATE_DIR="$(git rev-parse --path-format=absolute --git-path "codex/review-and-autofix/$task_id")"`
     - `REVIEW_LEDGER_PATH="$REVIEW_STATE_DIR/ledger.md"`
     - `REVIEW_ARCHIVE_DIR="$(git rev-parse --path-format=absolute --git-path codex/review-and-autofix/archive)"`
   - Git private metadata is the mandatory persistence layer for review state. Do not write the ledger under the repository worktree.

## Baseline Snapshot

Record baseline before edits:

- Current branch and git status
- Actual selected review target (files, staged/uncommitted changes, commit, PR or branch scope)
- Explicit caller work/round budget, when supplied
- Chosen mode (`strict`, `standard`, `fast`)
- Selected reviewer model/effort and each review purpose
- Required result, source decisions, preserved behavior, exclusions, and completed or missing requirement-check coverage
- Reviewed content fingerprint and evidence that remains applicable after each fix
- Verification commands to run after each fix cycle
- Active finding ledger path: `REVIEW_LEDGER_PATH`, resolved through `git rev-parse --path-format=absolute --git-path`
- Create or refresh the finding ledger at that path for this task. This is required and must be carried forward across rounds and same-task review sessions.
- Finding ledger contract:
  - One row per finding or stable finding-cluster.
  - Required fields:
    - `ledger_id`
    - `cluster_label` (`rule-scatter` | `ownerless-logic` | `split-authority` | `oversized-hotspot` | `speculative-fallback` | `coincidence-driven`, when the evidence supports one)
    - `status` (`new` | `resolved` | `repeated` | `superseded`)
    - `first_seen_at`
    - `last_seen_at`
    - `times_seen`
    - `files_or_modules`
    - `shared_cause_hypothesis`
    - `evidence_notes`
    - `last_remedy_shape`
  - Resolved findings stay in the ledger as symptom-churn evidence.
  - Exclude only unrelated or clearly stale findings from other diffs/tasks.
  - Update the existing ledger after each round; do not silently recreate it from scratch.
  - Treat `REVIEW_LEDGER_PATH` as live private Git operational state, not project documentation or reviewed source.
  - Archived historical ledgers belong under `REVIEW_ARCHIVE_DIR` and are not the default current source of truth.


## Closeout And Archive

When the run reaches a real terminal state:

1. **Successful closeout**
   - For a standalone run or delegated terminal checkpoint, archive the active ledger to a new `REVIEW_ARCHIVE_DIR/<yyyy-mm-ddTHHMMSS>-<task-id>.md`; never overwrite an earlier archive.
   - Remove the stale active `REVIEW_LEDGER_PATH` only after the archive write succeeds.
   - For a delegated nonterminal checkpoint, keep `REVIEW_LEDGER_PATH` active for the caller's next checkpoint; do not archive it yet.
   - In the final summary, name the active ledger path and, when terminally archived, the archive path created at closeout.
2. **Paused, blocked, or incomplete run**
   - Keep the active ledger at `REVIEW_LEDGER_PATH`.
   - Refresh it in place when the same task resumes.
   - Do not create sibling ledgers for the same `task-id` without a concrete reason.
3. **Artifact interpretation**
   - Treat each task's `REVIEW_LEDGER_PATH` as live state for active work.
   - Treat `REVIEW_ARCHIVE_DIR` as historical context only.
   - Do not scan archived ledgers as the default current source of truth unless the user explicitly asks for history.

---

## Reporting

Keep detailed round evidence in the existing ledger. User updates should explain material findings, repairs, verification and remaining dependencies without a fixed per-round template.

For a delegated checkpoint, return the root skill's caller contract. A standalone summary should make the checked scope, result, relevant evidence and unresolved work clear. Include active and archived ledger paths as applicable; finding counts are optional and do not establish completeness.
