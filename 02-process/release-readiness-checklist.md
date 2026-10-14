# Release Readiness Checklist

Use this for the go/no-go decision. Anything unticked needs a named owner and an accepted risk, or the release waits.

**Release:** ________ **Date:** ________ **QA owner:** ________

## ✅ Testing

- [ ] All stories in scope meet the [Definition of Done](qa-in-agile.md#definition-of-done-story)
- [ ] Full automated regression green on the release candidate (link to run: ____)
- [ ] No tests skipped or quarantined without a ticket and owner
- [ ] Exploratory sessions completed for high-risk areas
- [ ] Cross-browser / device matrix passed
- [ ] Accessibility: no critical or serious violations; manual keyboard check on changed pages

## 🐞 Defects

- [ ] 0 open Sev 1 / Sev 2 defects
- [ ] Open Sev 3 defects reviewed and accepted by Product (list: ____)
- [ ] Known issues documented in release notes

## ⚡ Non-functional

- [ ] Performance tests meet thresholds (p95 ____ ms, error rate < ____ %)
- [ ] Security scans: no new high or critical findings
- [ ] Monitoring, alerts and dashboards ready for new features

## 🚀 Deployment

- [ ] Database migrations tested on a production-like copy, including rollback
- [ ] Feature flags configured and documented
- [ ] Rollback plan written and tested
- [ ] Smoke test suite ready to run straight after deployment
- [ ] Support and stakeholders informed

## 🗳️ Decision

| Role | Name | Go / No-go | Notes |
|---|---|---|---|
| QA Lead | | | |
| Product Owner | | | |
| Engineering Manager | | | |

**Post-release:** run smoke tests → watch error rates and key metrics for 30–60 min → log escaped defects for the next retro.
