# Cost & Scaling

---

## CS-01: Hosting Cost Appropriateness

**What:** Over- or under-provisioned hosting relative to actual usage.
**Detection:** ask developer — what are you paying for hosting? What's your traffic? Compare with cheaper alternatives.
**Possible correction:** Right-size hosting when bills and utilization show a mismatch; include migration and ongoing work in the comparison.

## CS-02: Database Scaling Readiness

See [INF-05](checks-infrastructure.md#inf-05-database-scaling-readiness).

## CS-03: Caching Strategy

**What:** Missing or ineffective caching leading to unnecessary computation and database load.
**Detection:** static — check for caching layer (Redis, Memcached, in-memory cache). Look for repeated expensive computations without caching. Check for HTTP cache headers.
**Possible correction:** Cache repeated expensive work with a defined invalidation strategy when reuse and acceptable staleness justify it; an incorrect cache is worse than recomputation.

## CS-04: Connection Management

See [BE-09](checks-backend.md#be-09-db-connection-management).

## CS-05: Scaling Limits

**What:** Architectural patterns that create hard scaling limits (single points of failure, non-horizontal patterns).
**Detection:** static — check for single-process assumptions (in-memory sessions, file-based state). Look for singleton patterns that prevent horizontal scaling. Check for shared file system dependencies.
**Possible correction:** Move sessions to an external store and file state to object storage when deployment requires multiple instances or restart durability.

## CS-06: N+1 at Scale

See [BE-02](checks-backend.md#be-02-n1-query-patterns).

## CS-07: Asset Optimization

**What:** Unoptimized assets (images, fonts, scripts) increasing bandwidth costs and load times.
**Detection:** static — check for image optimization pipeline, font subsetting, JS/CSS minification, compression (gzip/brotli).
**Possible correction:** Convert to WebP/AVIF, subset fonts and enable gzip/brotli when assets materially affect transfer cost; retain required content and fidelity.

## CS-08: Third-Party Cost Awareness

**What:** Third-party services with usage-based pricing that could become expensive at scale.
**Detection:** static — identify third-party services with usage-based pricing (API calls, emails, storage, compute). Check for rate limiting on outbound API calls.
**Possible correction:** Track usage per service and set billing alerts when usage-based charges are material; compare caching or alternatives only after checking total cost.

## CS-09: Cold Start / Initialization

**What:** Slow startup time affecting serverless costs, deployment speed, and auto-scaling responsiveness.
**Detection:** dynamic — measure application startup time. Static — check for heavy initialization (large file reads, database migrations at startup, eager loading of all modules).
**Possible correction:** Lazy-load modules and defer non-critical initialization when startup is measured as slow; provisioned concurrency is an economic choice.
