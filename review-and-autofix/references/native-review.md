# Native Review Execution and Recovery

Read this before launching or recovering `codex review`. The root skill owns finding acceptance, requirements coverage and the clear gate; [state-and-reporting.md](state-and-reporting.md) owns private state. Other review transports need this reference only when they invoke native review.

## Exact Target and Compute

Apply the root skill's model and effort defaults unless the caller selects supported alternatives. Resolve host support and record the actual compute. Set both `model` and `review_model` for a native launch so a separate configured review override cannot change the selected reviewer. Use in-session review only when its effective reviewer compute is known to match. Native subprocesses retain the parent sandbox/approval posture and authorized account/workspace.

Build a fresh shell argv array for each launch; do not execute a scalar command string or use `eval`. Validate configuration values rather than interpolating unchecked text. For example, after setting validated `REVIEW_MODEL` and `REVIEW_EFFORT`:

```sh
REVIEW_CMD=(codex --disable apps -c "model=\"$REVIEW_MODEL\"" -c "review_model=\"$REVIEW_MODEL\"" -c "model_reasoning_effort=\"$REVIEW_EFFORT\"")
REVIEW_CMD+=(review)
"${REVIEW_CMD[@]}" --uncommitted
```

For a branch comparison, first verify the exact nonempty ref:

```sh
git rev-parse --verify --quiet --end-of-options "$BASE_BRANCH^{commit}"
"${REVIEW_CMD[@]}" --base "$BASE_BRANCH"
```

Use a currently supported route for other targets. Do not widen a file, staged, commit or PR request to fit these examples. Verify custom-prompt/target compatibility before combining them. Target-only native commands do not receive this task's conversation or review purpose; perform the root skill's requirement check for missing context before calling the result clear.

Normal review model processing through the configured Codex account is already authorized by the review request. A separate subprocess is not a new archive upload or recipient. Honor a prohibition on all remote processing and stop if this CLI would change the authorized destination/account. Use normal tool escalation for a real sandbox/network restriction; never change the subprocess to full-access mode or override HOME.

## Own the Process

Record each launched PID/session under the private review state and run native reviews serially. Inspect only processes this task owns. Before terminating one, verify its command is `codex review` and its cwd matches the repository. If ownership cannot be established, leave it alone.

Keep a healthy review alive. Silence and startup noise alone do not prove failure. Inspect available process, session/log or token-event evidence at a modest cadence using bounded waits that allow user updates. Honor a tool's retry interval and any explicit user time budget. Set a practical observation bound when needed from actual runtime behavior.

A completed review needs an explicit final result, or normal process exit with a final reviewer verdict. A live process is still in progress. An exit without verdict, explicit interruption, or sustained lack of progress supported by process evidence leaves the result incomplete.

## Recover by Failure Cause

| Evidence | Permitted response |
| --- | --- |
| MCP OAuth/auth-refresh noise, including `TokenRefreshFailed` | Continue observing if review progress remains; the log line alone is not terminal. |
| A specific MCP server prevents startup/progress | Use a per-run disable only if that override is supported for the actual server and current Codex build. |
| MCP override yields `invalid transport` | Abandon the override and return to the baseline argv; treat it as a tool limitation. |
| Wrangler/local bind or log-path `EPERM` | Preserve the error and use the narrow host-permitted diagnostic escalation. Keep subprocess sandbox posture. |
| Backend reconnect, DNS or stream failure | Preserve baseline settings and use the host-permitted network diagnostic/escalation. |
| Authentication failure after a HOME override | Remove that override; do not infer the real account is invalid from altered discovery. |

A supported MCP trim is scoped to the review invocation. Resolve the actual configured server ID, validate it against `[A-Za-z0-9_-]+`, then append `-c "mcp_servers.<validated-id>.enabled=false"` before the review subcommand. Keep useful servers enabled unless they caused the failure. Some remote streamable HTTP servers reject this override; do not assume compatibility or edit global config as an incidental repair.

Retry a recoverable infrastructure failure only when the cause or a permitted recovery gives the retry a reasonable prospect of progress. Preserve attempt history and stop repeated identical failures; return their evidence and a different useful route to the coordinator. Do not restart a review paused or canceled by the user until they resume it, or run a replacement while the original process is still active.

An incomplete native result leaves its missing coverage visible. It neither clears the review nor ends other authorized work.
