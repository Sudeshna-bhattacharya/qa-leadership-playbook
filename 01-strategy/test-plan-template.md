# Test Plan Template

> **Scope:** one release, epic or major feature. Lightweight by design: fill in what's useful, delete the rest.
> The [test strategy](test-strategy-template.md) answers *how we test in general*. This plan answers *what we test for this release*.

---

## 1. Summary

| Item | Details |
|---|---|
| Release / epic | *e.g. Checkout v2, Release 2026.11* |
| Target date | YYYY-MM-DD |
| QA owner | *name* |
| Linked tickets | *epic / board link* |

## 2. What's changing

- *Feature A: new payment method (card + wallet)*
- *Feature B: redesigned order-history page*
- *Tech change: migration from REST v1 to v2 for orders API*

## 3. Risk assessment

Use the [risk scoring](risk-based-testing.md) table.

| Area | Impact (1–5) | Likelihood (1–5) | Score | Test depth |
|---|---|---|---|---|
| Payment authorisation | 5 | 4 | 20 | Deep: full API + E2E + exploratory + perf |
| Order history UI | 3 | 3 | 9 | Standard: E2E happy paths + a11y |
| Email receipts | 2 | 2 | 4 | Light: smoke + manual spot check |

## 4. Test approach for this release

| Type | Planned work |
|---|---|
| API | New endpoints: contract + negative + auth tests |
| UI E2E | Checkout with each payment method; order history pagination |
| Regression | Full nightly suite; manual regression only for areas without automation |
| Performance | Checkout API at 2× peak load for 30 min; p95 < 800 ms |
| Accessibility | axe-core in CI; manual keyboard + screen-reader pass on checkout |
| Exploratory | 2 × 60-min sessions on payment failures and retries |
| Compatibility | Chrome, Safari, Firefox (latest 2); iOS Safari; Android Chrome |

## 5. Out of scope

- *Admin refund tool: unchanged in this release*

## 6. Entry and exit criteria

**Entry:** build deployed to staging, feature flags configured, test data available.

**Exit:**

- [ ] All planned tests executed
- [ ] 0 open Sev 1 / Sev 2 defects
- [ ] Sev 3 defects reviewed and accepted by Product
- [ ] Performance thresholds met
- [ ] No new accessibility violations (critical / serious)
- [ ] Automation for new features merged

## 7. Schedule

| Activity | Dates | Owner |
|---|---|---|
| Test design & automation | | |
| Feature testing | | |
| Regression & performance | | |
| Release sign-off | | |

## 8. Dependencies and assumptions

- *Payment sandbox credentials available by DD/MM*
- *Design sign-off on new components before testing starts*

## 9. Sign-off

| Role | Name | Decision | Date |
|---|---|---|---|
| QA Lead | | Go / No-go | |
| Product Owner | | | |
| Engineering Manager | | | |
