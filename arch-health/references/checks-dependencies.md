# Dependencies

---

## DEP-01: Outdated Dependencies

**What:** Dependencies that are significantly behind the latest version.
**Detection:** dynamic — `npm outdated` / `pip list --outdated` / `cargo outdated` / equivalent.
**Assessment:** Version distance is a discovery clue. Check supported release lines, relevant security advisories, actual usage, and required platform compatibility. Several major versions behind may still be supported; a current major may still be vulnerable. Assign severity to the verified exposure or contract failure, not the version count.
**Possible correction:** Recommend a supported version that resolves the demonstrated issue, with changelog and compatibility evidence; verify the package name and publisher before installing.

## DEP-02: Abandoned Packages

**What:** Dependencies with no maintenance — no commits, no releases, no response to issues.
**Detection:** static/remote metadata — inspect supported releases, repository activity and responses to relevant issues. Release age is a clue; a lockfile generally does not establish maintenance status.
**Possible correction:** Replace, fork or inline an abandoned package when inactivity creates a support, compatibility or security problem in the used path.

## DEP-03: License Compliance

**What:** Dependencies with licenses incompatible with the project's license or usage.
**Detection:** dynamic — an already installed license inventory tool / `pip-licenses` / equivalent. Static — check license fields in lock files.
**Possible correction:** Report exact license/use/distribution evidence; recommend a change only after establishing obligations from authoritative guidance.

## DEP-04: Bundle Impact

**What:** Dependencies that are disproportionately large relative to the functionality they provide.
**Detection:** dynamic — bundle analysis tools. Static — check package sizes in node_modules, look for heavy packages used for single functions.
**Possible correction:** Import specific submodules (`lodash/debounce`) or a lighter alternative when measured bundle cost is disproportionate; compare behavioral compatibility first.

## DEP-05: Security Vulnerabilities

See [SEC-03](checks-security.md#sec-03-supply-chain-owasp-a06).

## DEP-06: Dependency Count

**What:** Unused or overlapping dependencies add avoidable maintenance or supply-chain exposure.
**Detection:** static — count direct dependencies in manifest file. Count total transitive dependencies.
**Possible correction:** Remove confirmed unused or overlapping dependencies when that reduces real maintenance or supply-chain cost; count alone does not justify custom replacements.

## DEP-07: Lock File Health

**What:** Missing, outdated, or inconsistent lock file.
**Detection:** static — check lock file exists, is committed, matches manifest. Do not run an install merely to audit consistency; use an existing non-mutating lockfile check when available.
**Possible correction:** Generate the lockfile and use `--frozen-lockfile` in CI when it is absent or inconsistent; libraries and applications can have different contracts.

## DEP-08: Vendor Lock-In

**What:** Provider coupling makes a supported change or verification need unnecessarily widespread.
**Detection:** static — trace provider-specific decisions, contracts and callers. Determine whether they should change together before proposing a wrapper.
**Possible correction:** Localize provider-dependent behavior in a dedicated module when an actual change or testing need justifies it; SDK imports alone do not require a wrapper.

## DEP-09: Phantom Dependencies

**What:** Dependencies used in code but not declared in manifest (relying on transitive installation).
**Detection:** static — check imports against declared dependencies. Look for packages imported but not in dependencies/devDependencies.
**Possible correction:** Declare directly used packages in the manifest when they rely on transitive installation; respect intentional peer, optional or platform dependencies.

## DEP-10: Pinning Strategy

**What:** Version policy that fails the repository's reproducibility, consumer-compatibility, or update requirements.
**Detection:** static — check version specifiers in manifest. Look for `*`, `latest`, or `>=` without upper bound.
**Assessment:** Inspect unbounded selectors and inconsistent intent. Exact pins are not a defect by themselves, and mixed specifiers may reflect distinct dependency contracts. Check how updates are reviewed and how the actual package manager uses the manifest and lock file.
**Possible correction:** Preserve the repository's verified version contract and any exact-version save settings the environment enforces; a library's compatibility range differs from an application lockfile.
