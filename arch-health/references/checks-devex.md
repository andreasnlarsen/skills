# Developer Experience

---

## DX-01: Build Time

**What:** Slow build times that hurt development velocity.
**Detection:** dynamic — time the build command.
**Possible correction:** Enable incremental builds and build caching (Turborepo, nx) when profiling shows a build bottleneck; changing compilers needs compatibility evidence.

## DX-02: Test Runtime

**What:** Slow test suite discouraging developers from running tests.
**Detection and assessment:** Use [Testing Health T-07](checks-testing.md#t-07-test-runtime) as the single owner of runtime evidence and remediation. Reuse that result instead of timing and reporting the same bottleneck twice. Describe the effect on the development feedback loop here.

## DX-03: CI/CD Speed

**What:** Slow CI pipeline discouraging frequent commits and PRs.
**Detection:** dynamic — check CI config for estimated duration. Ask developer for typical CI time.
**Possible correction:** Cache dependencies, parallelize independent jobs and run fast checks first when CI is a demonstrated feedback bottleneck.

## DX-04: Documentation

**What:** Missing or outdated documentation for setup, architecture, and key decisions.
**Detection:** static — compare existing setup, architecture or API documentation with the implementation and intended reader tasks. File presence or modification date alone does not establish correctness.
**Possible correction:** Fix the missing or stale instructions that block setup, operation or a likely change; reuse the existing documentation owner.

## DX-05: Dev Environment Setup

**What:** Complex or unreliable local development setup.
**Detection:** static — check for setup instructions, docker-compose.yml, devcontainer.json, Makefile with setup target, seed scripts.
**Possible correction:** Automate setup with a single command (`make setup`, `docker compose up`) when manual steps are fragile or repeated.

## DX-06: Code Generators / Scaffolding

**What:** Repetitive boilerplate that could be generated.
**Detection:** static — inspect repeated boilerplate, frequency of change and observed drift. Compare the existing implementation with any generator already in use.
**Possible correction:** Add a generator when stable repeated boilerplate causes recurring work or drift; compare with keeping the small implementation explicit.

## DX-07: IDE Integration

**What:** Editor or language-tool differences create avoidable code or collaboration problems.
**Detection:** static — check for `.editorconfig`, `.vscode/` settings, `.idea/` settings (if committed), TypeScript/language server config, lint/format on save config.
**Possible correction:** Add `.editorconfig` or shared format-on-save settings when inconsistent editor behavior causes real code problems; preserve individual preferences.

## DX-08: Commit/PR Conventions

**What:** Commit history or review context is difficult to use for the team's actual work.
**Detection:** static — check for commitlint config, PR template, conventional commits usage in git log. Check for pre-commit hooks.
**Possible correction:** Add commitlint, a PR template or pre-commit hooks when history or review friction is demonstrated; their absence is not a finding.

## DX-09: Local Dev Parity

See [INF-03](checks-infrastructure.md#inf-03-environment-parity).

## DX-10: Onboarding Friction

**What:** New developers struggle to get productive — too many tribal knowledge dependencies.
**Detection:** static + ask developer — check for onboarding docs, architecture overview, glossary. Estimate setup time. Check for documented conventions.
**Possible correction:** Document or automate the knowledge gap that blocks new contributors, kept with existing setup documentation; a separate guide is not automatically needed.
