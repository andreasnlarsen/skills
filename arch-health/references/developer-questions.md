# Developer Questions

Questions for material gaps that the request and read-only evidence cannot resolve. Use the available user-input mechanism; do not require a tool by an obsolete name. Ask only when the answer would change scope, severity or a recommendation.

---

## Deployment and Workload

Resolve these facts from supplied or retrieved context when they affect the audit.

1. **Is this deployed to production? What hosting platform?**
   - Needed for: infrastructure severity calibration, security priority, scaling relevance.
   - If not deployed: lower severity for infrastructure, observability, cost checks.

2. **Rough user/request count?**
   - Options: <100, 100-1K, 1K-10K, 10K-100K, >100K
   - Needed for: scaling and cost relevance, rate limiting severity.

3. **Proprietary or open-source?**
   - Needed for: license obligations and distribution context; do not assign severity from proprietary/open-source status alone.
   - Also affects exposure assessment. Confirm whether a secret was publicly committed instead of assuming exposure from repository visibility alone.

4. **Team size?**
   - Options: Solo developer, 2-5, 6-20, >20
   - Needed for: DevEx severity calibration, documentation importance, onboarding friction relevance.

---

## Ask If Relevant (based on gaps in detection)

Ask these when static/dynamic analysis leaves gaps that affect severity, priority, or a concrete recommendation.

5. **Do you have a staging environment?**
   - Ask when: deployment config exists but environment parity can't be determined.
   - Affects: INF-03 (Environment Parity).

6. **What's the deployment process?**
   - Ask when: no CI/CD config found, or config exists but deployment steps unclear.
   - Affects: INF-04 (CI/CD Pipeline Health).

7. **Are there automated database backups?**
   - Ask when: database exists but backup config can't be found in code.
   - Affects: INF-09 (Backup & Recovery).

8. **What monitoring/alerting tools are in use?**
   - Ask when: no APM/monitoring library found in code but project is in production.
   - Affects: OBS-01 (APM), OBS-04 (Alerting).

9. **Are there compliance requirements? (GDPR, SOC2, HIPAA, PCI-DSS)**
   - Ask when: project handles user data, payments, or health information.
   - Affects: Security severity escalation, logging requirements, data handling checks.

10. **What's the biggest pain point right now?**
    - Ask when: calibrating report emphasis — this helps prioritize the remediation plan.
    - Affects: Report ordering and emphasis.

---

## Ask for Calibration

These set the tone for recommendations — how aggressive should the remediation plan be?

11. **Project phase: active development, maintenance mode, or end-of-life?**
    - Options: Active development, Maintenance mode, End-of-life, Rescue/inherited
    - Affects: Which risks and changes are relevant to the project's actual use and remaining lifetime. Do not apply a maturity score or blanket severity adjustment.

12. **Appetite for refactoring right now?**
    - Options: High (proactive), Medium (if it helps velocity), Low (only if critical), None (stability mode)
    - Affects: how much goes into the recommendation sections of [report-template.md](report-template.md), and whether to offer remediation tasks.
