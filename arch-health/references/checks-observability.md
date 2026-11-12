# Observability

---

## OBS-01: Application Monitoring / APM

**What:** No application performance monitoring in production.
**Detection:** static — check for APM library imports (Datadog, New Relic, Sentry Performance, OpenTelemetry). Ask developer about monitoring setup.
**Possible correction:** Add APM (Datadog, New Relic, OpenTelemetry) when failures or latency cannot be observed within the required response time; platform metrics may suffice.

## OBS-02: Error Tracking

**What:** No centralized error tracking — errors lost in logs or unnoticed.
**Detection:** static — check for error tracking service integration (Sentry, Bugsnag, Rollbar, Datadog). Check for global error handlers that report to a service.
**Possible correction:** Add Sentry or equivalent with source maps when distributed logs or minification prevent diagnosis; protect sensitive data.

## OBS-03: Structured Logging

See [BE-07](checks-backend.md#be-07-logging-quality).

## OBS-04: Alerting Configuration

**What:** No alerting on critical conditions — team finds out about issues from users.
**Detection:** ask developer — check for alerting rules, PagerDuty/OpsGenie integration, threshold-based alerts.
**Possible correction:** Alert on error-rate, latency and downtime conditions with an owner when actionable; a dedicated on-call platform is not required by default.

## OBS-05: Health Check Endpoints

See [BE-13](checks-backend.md#be-13-health-check-endpoints).

## OBS-06: Log Aggregation

**What:** Logs scattered across multiple servers/containers with no central collection.
**Detection:** ask developer — check for log aggregation service (ELK, Grafana Loki, Datadog Logs, CloudWatch).
**Possible correction:** Ship logs to a central service when scattered instances prevent timely diagnosis; a single-instance service may need none.

## OBS-07: Distributed Tracing

**What:** No request tracing across services in a multi-service architecture.
**Detection:** static — check for tracing library (OpenTelemetry, Jaeger, Zipkin). Check for trace ID propagation in HTTP headers. Only relevant for multi-service architectures.
**Possible correction:** Add OpenTelemetry tracing with trace-ID propagation and sampling when cross-service diagnosis is a demonstrated gap.

## OBS-08: Business Metrics

**What:** No tracking of business-relevant metrics (signups, purchases, feature usage).
**Detection:** static — check for analytics/metrics library (PostHog, Amplitude, Mixpanel, custom metrics). Check for event tracking calls in code.
**Possible correction:** Track key business events (signups, conversions, feature adoption) needed for actual decisions; define what each event proves and its source.

## OBS-09: Dependency Monitoring / Circuit Breakers

**What:** No monitoring of external dependency health, no circuit breakers for failing dependencies.
**Detection:** static — check for circuit breaker patterns (opossum, resilience4j, polly). Check for timeout configuration on external API calls. Check for retry logic.
**Possible correction:** Add timeouts to external calls and a circuit breaker for critical dependencies when a dependency failure can cascade.
