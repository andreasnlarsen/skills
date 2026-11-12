# Testing Health

---

## T-01: Test Coverage Percentage

**What:** Percentage of code covered by tests.
**Detection:** dynamic — run tests with coverage flag (`--coverage`, `--cov`, etc.).
**Assessment:** Coverage percentage is a screening measure, not a severity grade. Check what the report includes and whether important supported behavior and realistic failures are exercised. A high percentage can miss critical behavior; a low percentage alone does not prove a critical defect. Record a verified satisfactory check as `PASS`, not `INFO`.
**Possible correction:** Cover a concrete behavioral gap or current regression with the smallest meaningful check; a higher percentage is not the goal.

## T-02: Test-to-Code Ratio

**What:** Ratio of test lines to source lines.
**Detection:** static — count lines in test files vs source files.
**Possible correction:** Assess important behavior and realistic failures directly. Test-line ratio alone does not justify adding tests.

## T-03: Missing Test Types

**What:** Project lacks entire categories of tests (no unit, no integration, or no e2e).
**Detection:** static — check for test directories/files, test framework config, e2e config (Playwright, Cypress, etc.).
**Assessment:** Compare existing tests with the project's requirements and realistic failure paths. A missing category alone is not a finding; another test type may already provide sufficient evidence.
**Possible correction:** Add a test type only when an existing requirement or uncovered behavior needs its particular evidence; another type may already cover it.

## T-04: Assertion Density

**What:** A test may not observe the outcome it claims to cover.
**Detection:** static — inspect each relevant test's success/failure condition, including assertions, expected exceptions and harness-level outcomes.
**Possible correction:** Check the expected outcome or invariant; assertions, expected exceptions or a harness verdict each suffice, and their count is not a quality measure.

## T-05: Mock Overuse

**What:** Tests that mock so much they're not testing real behavior.
**Detection:** static — inspect what mocks replace and whether the remaining interaction can expose the claimed failure.
**Possible correction:** Choose mocks by whether they preserve the behavior under test and give a repeatable check, such as a forced timeout or error path; use the real interaction when a mock would hide the failure under investigation.

## T-06: Flaky Test Indicators

**What:** Tests that use timing-dependent logic, random data, or shared state.
**Detection:** static — search for `setTimeout` in tests, `Math.random()` without seeds, shared mutable state between tests, `sleep`/`wait` without condition.
**Possible correction:** Use polling/waitFor, seeded random data and isolated state when tests depend on timing, randomness or shared state.

## T-07: Test Runtime

**What:** How long the full test suite takes to run.
**Detection:** dynamic — time the test suite execution.
**Assessment:** This check owns test-runtime assessment, including DX-02. Record the command, environment, suite scope, observed duration, and the repository's latency target or comparable baseline. Flag a material regression or demonstrated feedback bottleneck; do not assign universal warning/critical times.
**Possible correction:** Profile the bottleneck, then use targeted commands, safe parallelism or fixtures; preserve database, transaction, locking and migration semantics under test.

## T-08: Snapshot Staleness

**What:** Snapshot tests that haven't been updated and may be auto-approved without review.
**Detection:** static — inspect whether snapshot content and reviewed changes expose meaningful behavior or conceal it among unrelated output.
**Possible correction:** Prefer explicit assertions when snapshots hide meaningful regressions among unrelated output; keep snapshots small and reviewable.

## T-09: Test Isolation

**What:** Tests that depend on execution order or share mutable state.
**Detection:** static — look for global state mutation in test setup, tests that reference other test data, missing cleanup in afterEach/teardown.
**Possible correction:** Set up state per test with beforeEach/afterEach cleanup when leakage causes order dependence; run in random order to expose it.

## T-10: Missing Edge Case Tests

**What:** Material, reachable failures or input/state boundaries lack sufficient test coverage.
**Detection:** Inspect how existing tests exercise the affected behavior, including error handling and validation. Identify a concrete failure or boundary that remains unchecked; do not infer a gap from test counts or filenames alone.
**Assessment:** Assess the uncovered behavior's impact and reachability. An error-test percentage is not a quality target.
**Possible correction:** Add the smallest meaningful test for the uncovered boundary; empty inputs, concurrency and network failures matter only where reachable.

## T-11: Test Configuration Health

**What:** Test framework configuration issues.
**Detection:** static — check for test config file existence, proper test patterns, coverage exclusions.
**Possible correction:** Fix discovery, timeout or coverage configuration that misrepresents results; exclude generated/non-source data from coverage.
