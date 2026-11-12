# Eval cases

Past failures kept as test cases for this skill. These are not instructions; use them when testing or maintaining the skill.

## Prompt argument assumed compatible with a target flag
- Situation: A native `codex review` needed the task's requirements; `--help` listed a `[PROMPT]` argument next to `--uncommitted` and `--base`.
- Wrong behavior: Assumed the prompt argument could be combined with the target flag because both appeared in help, or changed global instructions/target scope as a workaround, and treated the target-only verdict as covering requirements it never received.
- Expected behavior: Verify custom-prompt/target compatibility before combining them; otherwise perform the requirement check separately and record its evidence before calling the result clear.

## Native review declared stale on silence
- Situation: Native review of a large diff (several thousand changed lines) produced no output for 17+ minutes.
- Wrong behavior: Classified the review as parked on silence alone and launched a duplicate; the skill was then patched with a universal wait formula (`max(15 min, min(30 min, 8 min + 1 min per 1000 changed lines))`, one extension to 40 minutes, "silence under 17 minutes is normal").
- Expected behavior: Keep the live process, inspect process/session/token evidence at a modest cadence, and set an observation bound from actual runtime behavior. Restart only with evidence of no progress and never while the original process is active.

## Same finding re-fixed round after round
- Situation: The same finding, or a dominant cluster after a bounded shared fix, reappeared across fix rounds and sessions of one task.
- Wrong behavior: Kept applying symptom fixes each round; the skill was then patched with a fixed "2 consecutive rounds" counter and a single structural-pivot budget as stop conditions.
- Expected behavior: Count materially equivalent repeats from the cumulative ledger, stop the ineffective technique, and choose a materially different permitted step or return `incomplete` with the attempted-remedy history.

## Stale model and MCP identifiers taken from examples
- Situation: Selecting reviewer compute and trimming a failing MCP server for a native launch.
- Wrong behavior: Assumed a model named in an old example (for example `Astra`) and fixed MCP server ids copied from an old example still existed in the current host configuration.
- Expected behavior: Resolve supported model IDs, efforts and actual MCP server ids from the current host/tool configuration and record the actual selection.

## Consent gate invented for a review subprocess
- Situation: Launching native `codex review` as a new CLI process; the shell hit a sandbox/network restriction.
- Wrong behavior: Invented an "upload approval" or "fresh post-risk approval" gate because review ran in a subprocess, and recast the sandbox restriction as conversational data-sharing consent.
- Expected behavior: Treat the review request as authorizing processing through the configured Codex account/workspace, use normal tool escalation for the restriction, and stop only on an explicit prohibition of remote processing or a changed destination/account.
