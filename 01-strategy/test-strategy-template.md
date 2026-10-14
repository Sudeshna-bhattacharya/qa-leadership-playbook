# Test Strategy Template

> **Scope:** a product, platform or programme. Written once, revised when architecture, team or risk profile changes.
> **Owner:** QA Lead · **Reviewers:** Engineering Manager, Product Owner, Tech Lead
> **Length target:** 4–6 pages. If nobody reads it, it isn't a strategy.

---

## 1. Context

| Item | Details |
|---|---|
| Product | *What it does and who uses it* |
| Architecture | *e.g. React SPA + Node microservices + PostgreSQL, deployed on AWS* |
| Release cadence | *e.g. trunk-based, multiple deploys per day / fortnightly releases* |
| Team | *e.g. 3 squads, 12 developers, 4 QA engineers* |
| Regulatory or compliance needs | *e.g. PCI-DSS, GDPR, WCAG 2.2 AA* |

## 2. Quality goals

Define 3–5 measurable goals. Examples:

- Production escaped defects (Sev 1–2): **≤ 1 per release**
- Regression feedback in CI: **< 20 minutes** per merge
- Automated coverage of critical user journeys: **100%**
- API endpoint coverage: **100%** of public endpoints
- Accessibility: **WCAG 2.2 AA** on all customer-facing pages

## 3. Scope

| In scope | Out of scope (and why) |
|---|---|
| Web app, public REST APIs, mobile web | Third-party payment provider internals (covered by contract tests at our boundary) |
| | Legacy admin tool (scheduled for retirement in Q3) |

## 4. Test levels and ownership

| Level | Purpose | Owner | Tooling | Runs |
|---|---|---|---|---|
| Unit | Logic in isolation | Developers | Jest / JUnit | Every commit |
| Component / contract | Service boundaries, API contracts | Dev + QA | Pact / schema tests | Every PR |
| API / integration | Business rules, data, auth | QA (with dev support) | Playwright API / Postman + Newman | Every PR |
| UI end-to-end | Critical user journeys only | QA | Playwright | Every PR (smoke), nightly (full) |
| Performance | Response time, throughput, stability | QA | k6 / JMeter | Nightly + pre-release |
| Accessibility | WCAG compliance | QA + Design | axe-core, Lighthouse, screen readers | Every PR (automated) + per release (manual) |
| Security | OWASP Top 10 basics | Security + QA | ZAP baseline, dependency scanning | Nightly |
| Exploratory | Unknown unknowns | QA (whole team in bug bashes) | Session-based charters | Every feature |

See [Automation strategy](../03-automation/automation-strategy.md) for the pyramid and what to automate.

## 5. Risk approach

Features are scored with [risk-based testing](risk-based-testing.md). High-risk areas get deeper testing, more automation and mandatory exploratory sessions.

## 6. Environments and test data

| Environment | Purpose | Data | Refresh |
|---|---|---|---|
| Local / ephemeral PR env | Dev and PR checks | Seeded fixtures | Per PR |
| QA / staging | Integration, regression, UAT | Anonymised production snapshot + synthetic | Weekly |
| Pre-prod | Performance, release candidate sign-off | Production-like volume | Per release |

**Rules:** no real customer PII outside production. Tests create their own data and clean it up. Shared accounts are read-only.

## 7. Entry and exit criteria

**Entry (story ready for test):** acceptance criteria agreed, deployed to the test environment, unit tests green, feature flag state known.

**Exit (story done):** acceptance criteria verified, automated tests added at the right level, no open Sev 1–2 bugs, accessibility checks pass, PR reviewed.

## 8. Defect management

Follow [Defect management](../02-process/defect-management.md) for severity, priority, triage and SLAs.

## 9. Reporting

- **Per PR:** CI status + test report link
- **Per sprint:** quality summary (escaped defects, flaky rate, automation added)
- **Per release:** [release readiness checklist](../02-process/release-readiness-checklist.md) + go/no-go

Metrics are defined in the [QA metrics guide](../04-metrics/qa-metrics.md).

## 10. Risks to the strategy

| Risk | Mitigation |
|---|---|
| Unstable shared test environment | Ephemeral environments per PR; service virtualisation for third parties |
| Automation backlog grows faster than capacity | Automation is part of the Definition of Done; pairing with developers |
| Key-person dependency in QA | Rotation across squads; documented runbooks |

---

*Revision history: v1.0, YYYY-MM-DD, initial version.*
