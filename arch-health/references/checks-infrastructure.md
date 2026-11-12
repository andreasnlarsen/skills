# Infrastructure & Platform

---

## INF-01: Hosting Appropriateness

**What:** Over- or under-engineered hosting for the project's actual needs.
**Detection:** static — check for deployment config (Dockerfile, vercel.json, netlify.toml, terraform, etc.). Ask developer about hosting. Compare with actual requirements.
**Possible correction:** Match hosting to workload (static → CDN, APIs → serverless or containers, databases → managed) when current hosting misfits reliability, team or cost.

## INF-02: Container Health

**What:** Container configuration creates unnecessary privilege, exposed build contents, resource cost or startup failures.
**Detection:** static — inspect the image, build context, user, runtime dependencies and platform health contract.
**Possible correction:** Use multi-stage builds, a non-root user, `.dockerignore` and a `HEALTHCHECK` instruction when privilege, build-context, size or startup issues are demonstrated.

## INF-03: Environment Parity

**What:** Environment differences undermine the supported deployment or test contract.
**Detection:** static — check for environment-specific config files, conditional logic based on NODE_ENV/ENVIRONMENT, different dependency versions. Ask developer.
**Possible correction:** Remove the environment differences that violate the deployment contract, for example with containers or feature flags; document known remaining differences.

## INF-04: CI/CD Pipeline Health

**What:** Delivery checks or release steps leave a demonstrated reliability or feedback gap.
**Detection:** static — check for `.github/workflows/`, `.gitlab-ci.yml`, `Jenkinsfile`, etc. Check what the pipeline runs (tests, lint, build, deploy).
**Possible correction:** Add the lint, test, build or deploy stage that addresses the actual delivery risk; a full pipeline is not required merely because CI is absent.

## INF-05: Database Scaling Readiness

**What:** Database behavior cannot meet the expected workload within its latency, consistency or connection limits.
**Detection:** static — check schema for indexes on foreign keys and commonly queried fields, queries without pagination, connection pool config, single database instance for high traffic. Ask developer about read/write patterns.
**Possible correction:** Add indexes, pagination or pool limits from query plans and workload; account for write cost and consistency before adding replicas.

## INF-06: CDN Configuration

**What:** Static-asset delivery causes material latency, origin load or transfer cost.
**Detection:** static and dynamic — inspect asset routes, host/CDN behavior, caching and measured transfer. Same-origin URLs may already use a CDN.
**Possible correction:** Use a CDN with cache headers and content hashing when measured asset latency or origin load is material; the host may already provide one.

## INF-07: Secret Management

**What:** Secrets stored insecurely — in code, in plain text config, or committed to git.
**Detection:** static — scan for API keys, tokens, passwords in source files. Check `.gitignore` for `.env`. Check for secrets in CI/CD config files. Look for hardcoded connection strings.
**Possible correction:** Move secrets to environment variables or a secret manager via the project's established secret-handling process; recommend rotation for verified exposure.

## INF-08: SSL/TLS

**What:** Missing or misconfigured HTTPS.
**Detection:** ask developer — check if production URL uses HTTPS. Check for HSTS headers in code. Check for mixed content patterns.
**Possible correction:** Enable managed HTTPS and fix mixed content when traffic needs confidentiality; set HSTS only with a suitable HTTPS/domain rollout.

## INF-09: Backup & Recovery

**What:** Missing database backup strategy or untested recovery.
**Detection:** ask developer — check for backup configuration, backup schedule, recovery testing.
**Possible correction:** Enable automated backups with retention set by acceptable data loss, and test restores when recovery is unverified.

## INF-10: Infrastructure as Code

**What:** Infrastructure changes or recovery depend on undocumented, unreproducible manual state.
**Detection:** static — inspect the supported configuration, provider exports, deployment scripts or infrastructure code and compare them with the relevant recovery/change requirements.
**Possible correction:** Define infrastructure in version-controlled code when manual drift or restoration risk warrants it; reuse provider exports or scripts first.
