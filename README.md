# QA Leadership Playbook

![QA](https://img.shields.io/badge/Quality%20Engineering-Playbook-2ea44f)
![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey)

How I build, run and grow quality engineering teams: the strategies, standards, templates and rituals I use as a **QA Technical Lead**.

This is a working playbook, not theory. Every document is meant to be copied into a real team and adapted.

---

## 🧭 Principles

1. **Quality is a team responsibility. QA makes it easy.** Testers don't own quality alone; we build the guardrails, feedback loops and habits that let the whole team ship confidently.
2. **Shift left, then shift right.** Prevent defects in refinement and design, catch them early in CI, and watch production to learn what we missed.
3. **Test where it's cheapest.** Push checks down the pyramid: unit → API → UI. UI tests are for user journeys, not for business rules.
4. **Risk decides depth.** Not everything deserves the same testing effort. Impact × likelihood drives what we test, how deeply, and what we automate.
5. **A flaky test is worse than no test.** It erodes trust in the whole suite. Fix it, quarantine it or delete it, but never ignore it.
6. **Measure outcomes, not activity.** Escaped defects and lead time matter. Test-case counts don't.
7. **Grow people deliberately.** Every engineer has a skills map, a growth goal and a path from manual to automation, or from automation to leadership.

---

## 📚 Contents

### 1. Strategy

| Document | Use it for |
|---|---|
| [Test strategy template](01-strategy/test-strategy-template.md) | Product- or programme-level approach: scope, levels, environments, tooling, risks |
| [Test plan template](01-strategy/test-plan-template.md) | Release or feature-level plan: what, when, who, entry and exit criteria |
| [Risk-based testing](01-strategy/risk-based-testing.md) | Scoring features by impact × likelihood to decide test depth |

### 2. Process

| Document | Use it for |
|---|---|
| [QA in Agile](02-process/qa-in-agile.md) | QA activities across the sprint, Three Amigos, Definition of Ready and Done |
| [Defect management](02-process/defect-management.md) | Severity vs priority, bug lifecycle, triage rules, SLAs |
| [Release readiness checklist](02-process/release-readiness-checklist.md) | Go / no-go criteria before every release |

### 3. Automation

| Document | Use it for |
|---|---|
| [Automation strategy](03-automation/automation-strategy.md) | Test pyramid, what (not) to automate, tool selection, ROI |
| [Automation coding standards](03-automation/coding-standards.md) | Conventions every test codebase follows |
| [PR review checklist](03-automation/pr-review-checklist.md) | Reviewing test code consistently |
| [Flaky test policy](03-automation/flaky-test-policy.md) | Detect → quarantine → fix → restore |

### 4. Metrics

| Document | Use it for |
|---|---|
| [QA metrics guide](04-metrics/qa-metrics.md) | The metrics I track, their formulas and the ones I avoid |

### 5. People

| Document | Use it for |
|---|---|
| [30-60-90 day onboarding](05-people/onboarding-30-60-90.md) | Getting a new QA engineer productive and confident |
| [Skills matrix](05-people/skills-matrix.md) | Levels and expectations from Associate to Lead |
| [Manual → automation upskilling plan](05-people/upskilling-manual-to-automation.md) | 12-week programme to move manual testers into automation |

### 6. AI in testing

| Document | Use it for |
|---|---|
| [AI-assisted testing guidelines](06-ai-in-testing/ai-assisted-testing-guidelines.md) | Where AI helps, where it doesn't, guardrails and review rules |

### GitHub templates

- [Bug report issue form](.github/ISSUE_TEMPLATE/bug_report.yml)
- [Pull request template for test code](.github/PULL_REQUEST_TEMPLATE.md)

---

## 🔗 See it in practice

- [playwright-ts-framework](https://github.com/Sudeshna-bhattacharya/playwright-ts-framework): fixture-based UI + API automation, following the standards in this playbook
- [postman-api-testing](https://github.com/Sudeshna-bhattacharya/postman-api-testing): advanced API suite with chaining, contract tests and known-defect tracking

---

## 👩‍💻 Author

**Sudeshna Bhattacharya**, QA Technical Lead · 17 years in quality engineering · [GitHub](https://github.com/Sudeshna-bhattacharya)

Content is licensed under [CC BY 4.0](LICENSE). Use it, adapt it, and credit the source.
